---
{"dg-publish":true,"permalink":"/article-full/analisa-phishing-identitaskita-com/","title":"Analisa Phishing identitaskita.com","tags":["article","full"],"created":"2025-06-30T22:42:56.512+07:00","updated":"2025-07-06T09:02:19.054+07:00"}
---

# Analisa Phishing identitaskita.com  

Source: [my.id](https://nikkoenggaliano.my.id/read.php?id=46)  

#phishing #malwareanalysis #androidsecurity #reversing  

[Analisa Phishing identitaskita.com](https://nikkoenggaliano.my.id/index.php)

Last Update Article: 2024-12-19 20:43:16

---

Assalamualaikum warahmatullahi wabarakatuh, halo teman-teman semua! pada artikel kali ini saya akan menuliskan perjalanan saya dalam melakukan sedikit proses Reverse Engineering terhadap situr phishing yang saya dapatkan dari grup [skill-issue](https://skill-issue.org/), jadi malam ini setelah melihat discord skill-issue saya menemukan kurang lebih ada chat seperti di bawah ini

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image.png)

Di sana salah satu member dari skill-issue menanyakan adakah yang pernah melakukan analisa indikasi situs phishing beralamat [identitaskita.com](http://identitaskita.com/) lalu dijawab oleh teman lain yang yang memberikan jalan terbaik seperti melaporkan ke pihak-pihak tertentu, analisa dapat dilakukan oleh “orang nganggur” tentu saja akulah **si nganggur** itu (beneran) \[ngegame doang sih\] 🤣🤣🤣

## Web Recon

Untuk bentuk web aplikasinya web phishing ini meniru halaman resmi milik Google Playstore yang mana akan melakukan instalasi sebuah aplikasi android, seperti berikutlah lampiran gambar tangkapan layarnya

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%201.png)

Tombol yang ada di web tersebut hanya ada sebuah button `install` yang mana mengarahkan ke sebuah fungsi JS untuk melakukan download per chunk, seperti inilah potongan kode yang dilakukan rendering di browser

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%202.png)

Debugging pertama paling nyaman memang lewat *inspect element,* karena ternyata jika dilakukan *view-source:* ternyata konten utamanya disembunyikan pada sebuah base64 encode, berikut adalah bentuknya

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%203.png)

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%204.png)

seluruh kontennya berada di sebuah variable `encodeContent` dan setelahnya akan dilakukan decode dan memasukannya pada body HTML, mari kita coba lakukan decode siapa tau ya kan ada sesuatu yang menarik, karena kodenya dilakukan inspect element sangat berat mari gunakan `curl` saja untuk mengambil kontennya yang mana akan dilakukan decode di local.

1. copy content to local

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%205.png)

1. Hapus manual konten yang bukan base64
2. Gunakan WSL untuk melakukan decode
	![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%206.png)

Dengan ini saya sudah dapat source asli dari kode-kode *frontend* -nya meskipun bukan hal yang mungkin berfungsi tapi ya kenapa tidak dilakukan analisanya. Fungsi download di- *handle* oleh javascript

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%207.png)

```php
function handleDownload() {
            if (document.querySelector("#instal").style.display === "none") {
                return
            } else if (downloadA) {
                downloadA.click();
                setTimeout(function () {
                    if (/Chrome/.test(window.navigator.userAgent) && !Boolean(window.chrome)) {
                    document.querySelector('.UDxLd').style.display = "block";
                }
                }, 1000)
            }

            if (/Chrome/.test(window.navigator.userAgent) && !Boolean(window.chrome)) {
            window.location.href = "intent://" + window.location.href.split("://")[1] + "#Intent;scheme=" + window.location.href.split("://")[0] + ";end;";
        }
```

Singkatnya pada kode tersebut adalah memastikan apakah user menggunakan browser Chrome, ataupun jika menggunakan browser android web-view akan memaksa membuka `intent://` ke aplikasinya, isi terduga malware akan berada di uri kode berikut ini

```php
const url = decodeURIComponent("https:\/\/identitaskita.com\/x\/down?name=Identitas Kependudukan Digital.apk");
```

sebelum melakukan analisa ke file android aplikasi yang ada, saya lebih memilih untuk melakukan pengecekan umur domain dan relasi yang kemungkinan ada dari web ini, berikut hasilnya.

1. Whois
	![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%208.png)
	domainnya sudah menggunakan *whois protection* (ternyata tidak sebodoh kasus sebelumnya) yang mana informasi-informasi mengenai siapa yang memesan domain tersebut sudah tidak ada, lalu umur domainnya baru satu bulan dihitung per tanggal 19 Desember 2024 ini, sangat muda.
2. Related domain
	![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%209.png)
	ada 1 domain yang terkait dengan domain yang sedang saya analisa, dan bentuknya juga sama persis
	1. Tampilan
		![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2010.png)

b. whois

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2011.png)

## Android Reverse Engineering

Informasi awal yang dapatkan dari aplikasi android yang saya download, untuk ukuran file yang saya terima sekitar 16Mb lalu berikut detail dari aplikasinya

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2012.png)

| Name File | MD5 |
| --- | --- |
| Identitas Kependudukan Digital.apk | 34fcabe4d244928cf2deb96de36c6719 |

Setelahnya kita dapat melakuakan dekompilasi dengan jadx seperti biasa melakukan analisa dengan `jadx` berikut adalah hal-hal menarik yang saaya temukan

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2013.png)

Pada folder `com.louye.dpt/MainActivity.java` ditemukan kode seperti tangkapan layar di atas, dari sini *sense of feeling* saya bekerja dengan baik merasa ini adalah kode buatan China 🇨🇳 dilihat dari nama-nama yang ada dan benar saja string `dpt-shell` adalah sebuah *library* *Dex Protect* yang dikembangkan oleh teman-teman di China.

[Library](https://github.com/luoyesiqiu/dpt-shell/)

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2014.png)

Setelah menemukan sumber kode *library* -nya saya melakukan installasi apk pada emulator android saya dan ternyata Google Protect langsung melakukan *flagging* terhadap aplikasi ini bahwa aplikasi berbahaya

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2015.png)

Tapi untuk alasan analisa, kita *Enable* saya! toh ini adalah emulator, Tatakaeeeeeeeee! setelah membuka aplikasinya, aplikasinya benar-benar selalu *crach* di sini cukup menyulitkan saya dalam proses analisa, tapi tak apa kita lakukan analisa *Dex Protect* -nya saja!

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2016.png)

Untuk semua *library* untuk melakukan obfuscator disimpan pada folder `resource/assets/vwwwwwvwww/*` seperti tangkapan layar di bawah ini

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2017.png)

Saya sudah melakukan analisa terhadap [`libdpt.so`](http://libdpt.so/) dan hasilnya sangat-sangat susah dibaca, daripada sibuk melakukan *Reverse Engineering* pada libdpt.so saya lebih mending membaca kode sumber yang ada, saya mulai mencari dari data-data yang ada di strings yang ada

| libdpt.so |
| --- |
| app\_acf |
| dpt-shell seem not working |
| vwwwwwvwww |

Dari bantuan string-string yang ada ini memudahkan saya melakukan analisa pada kode sumber milik `dpt` obfuscator, semua konfigurasi memang benar disimpan pada file bernama

[Global.java](https://github.com/luoyesiqiu/dpt-shell/blob/cdaff2c14e5029f11999abe89bfc59c887fb64f4/shell/src/main/java/com/luoyesiqiu/shell/Global.java#L8) saya melakukan tracking melalui file ini [`dpt_util.h`](https://github.com/luoyesiqiu/dpt-shell/blob/cdaff2c14e5029f11999abe89bfc59c887fb64f4/shell/src/main/cpp/dpt_util.h#L54) dari namanya saja `util` pasti ini penting hahaha. Saya mencari sumber-sumber yang ada dan paling membuahkan informasi menarik adalah fungsi berikut ini

```php
bool read_zip_file_entry(void* zip_addr,off_t zip_size,const char* entry_name, void ** entry_addr,uint64_t *entry_size);
```

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2018.png)

pada potongan kode di bawah ini

```php
bool needFree = read_zip_file_entry(apk_addr,apk_size,COMBINE_DEX_FILES_NAME_IN_ZIP,&dexFilesData,&dex_files_size);
        if (dexFilesData != nullptr) {
            DLOGD("Read classes.dex of size: %lu", (unsigned long)dex_files_size);
            uint32_t zipDataLen = readZipLength((uint8_t *)dexFilesData, dex_files_size);
            DLOGD("Extracted zip data length: %u", (unsigned int)zipDataLen);
```

fungsi `read_zip_file_entry` membutuhkan 5 parameter dan semuanya diisi, salah satu variable yang mengisinya adalah konstanta hardcoded `COMBINE_DEX_FILES_NAME_IN_ZIP` yang mana isinya adalah

```c
#define DEXES_ZIP_NAME "i11111i111.zip"
#define CACHE_DIR "code_cache"

#define ACF_NAME_IN_ZIP "assets/app_acf"
#define APP_NAME_IN_ZIP "assets/app_name"
#define CODE_ITEM_NAME_IN_ZIP "assets/OoooooOooo"
#define DEX_FILES_NAME_IN_ZIP "assets/i11111i111.zip"
#define COMBINE_DEX_FILES_NAME_IN_ZIP "classes.dex"
#define JUNK_CLASS_FULL_NAME "com/luoye/dpt/junkcode/JunkClass"
```

Di sana terlihat banyak string-string yang dilakukan hardcode, lalu di manakah `dex` asli dari aplikasi ini? ya benar di simpan pada files `i11111i111.zip` yang mana juga diverifikasi oleh fungsi hooking dari dpt-shell itu sendiri

[di sini](https://github.com/luoyesiqiu/dpt-shell/blob/cdaff2c14e5029f11999abe89bfc59c887fb64f4/shell/src/main/cpp/dpt_hook.cpp#L165)

```c
if(location.rfind(DEXES_ZIP_NAME) != std::string::npos && dex_class_def){
            int dexIndex = parse_dex_number(&location);

            auto* class_def = (dex::ClassDef *)dex_class_def;
            NLOG("[+] DefineClass class_desc = '%s', class_idx_ = 0x%x, class data off = 0x%x",descriptor,class_def->class_idx_,class_def->class_data_off_);

            if(LIKELY(class_def->class_data_off_ != 0)) {
                size_t read = 0;
                auto *class_data = (uint8_t *) ((uint8_t *) begin + class_def->class_data_off_);

                uint64_t static_fields_size = 0;
                read += DexFileUtils::readUleb128(class_data, &static_fields_size);
                NLOG("[-] DefineClass static_fields_size = %llu,read = %zu", (unsigned long long)static_fields_size,
                     read);

                uint64_t instance_fields_size = 0;
                read += DexFileUtils::readUleb128(class_data + read, &instance_fields_size);
                NLOG("[-] DefineClass instance_fields_size = %llu,read = %zu",
```

singkatnya seluruh `Dex` asli mili aplikasi malware ini berada di files `i11111i111.zip` yang mana dapat kita verifikasi dengan melakukan akses ke android shell lewat adb dengan akses roots.

Identifier dari malware ini adalah `com.kpee.csnei.zdzd.adyj`

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2019.png)

Berarti kemungkinan dia dapat menyimpan Dex aslinya adalah berada pada `/data/data/com.kpee.csnei.zdzd.adyj/assets/` namun ternyata setelah melakukan pencarian lagi path aslinya berada pada `/data/data/com.kpee.csnei.zdzd.adyz/code_cache/*.zip` setelah menariknya ke local, berikut inilah data yang saya dapatkan

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2020.png)

Terdapat 4 \*.dex dan saat dibuka lewat jadx lagi, files-files ini berisi seperti berikut ini

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2021.png)

Banyak dari files-filesnya juga masih terobfuscated, namun ini sudah hasil yang baik dalam analisa singkat malam ini, salah satu aset yang saya temukan adalah *ip addresess* berikut ini:

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2022.png)

```c
http://203.107.1.1/d?host=
```

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2023.png)

- [https://otx.alienvault.com/indicator/ip/203.107.1.1/?utm\_medium=InProduct&&utm\_source=ThreatCrowd](https://otx.alienvault.com/indicator/ip/203.107.1.1/?utm_medium=InProduct&&utm_source=ThreatCrowd)
- [https://www.abuseipdb.com/whois/203.107.1.1](https://www.abuseipdb.com/whois/203.107.1.1)

![image.png](https://nikkoenggaliano.my.id/uploads/identitas/image%2024.png)

IP tersebut jika diberikan *supply* input pada *query parameter host* juga tidak mengerluarkan hasil apapun yang berbeda, dari sini saya sudah tidak berminat melakukan analisa lebih dalam lagi karena menjalankan aplikasinya saja tidak bisa di *emulator* saya, kalau teman-teman mau saya harap banyak yang mau benar-benar *deep dive* ke *malware* ini, karena saya tidak dapat kesimpulan apapun sebenarnya wkwk.

## Penutup

Terima kasih teman-teman telah membaca artikel saya kali ini, dalam analisa kali ini saya tidak dapat apapun seperti bagaimana *behaviour* dari aplikasinya, bagaimana mengirimkan data curiannya dan siapa pelakunya tapi saya cukup puas dalam perjalanan analisa ini, yang bisa saya pastikan menurut data-data yang ada *malware* yang ada ini dari China things meninjau dari IP yang ditemukan, obfuscator serta aset-aset yang berbahasa China lainnya, mungkin kesimpulan ini salah tapi data berbicara begitu. Sekali lagi mohon maaf tidak memenuhi ekspetasi teman-teman semuannya 😖 terima kasih sudah membaca!

---

Maybe you want to read:

- [Culture Reset Informatic Study Program UMSIDA](https://nikkoenggaliano.my.id/read.php?id=23)
- [How Security Implementation Kill Your Established Business](https://nikkoenggaliano.my.id/read.php?id=49)
- [Track them all](https://nikkoenggaliano.my.id/read.php?id=12)
- [Anies Tiktok Live Analytic](https://nikkoenggaliano.my.id/read.php?id=40)
- [Writeup Final KKS TNI AD 2021 – Notes (Web)](https://nikkoenggaliano.my.id/read.php?id=26)  
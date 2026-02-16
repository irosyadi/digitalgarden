---
{"dg-publish":true,"permalink":"/article-full/seven-diabetes-patients-die-due-to-undisclosed-bug-in-abbott-s-continuous-glucose-monitors/","title":"Seven Diabetes Patients Die Due to Undisclosed Bug in Abbott's Continuous Glucose Monitors","tags":["article","full"]}
---

# Seven Diabetes Patients Die Due to Undisclosed Bug in Abbott's Continuous Glucose Monitors  

Source: [sfconservancy.org](https://sfconservancy.org/blog/2025/dec/23/seven-abbott-freestyle-libre-cgm-patients-dead/)  

#FreeSoftware #OpenSource #MedicalDevices #Diabetes  


I [wrote last month](https://sfconservancy.org/blog/2025/nov/06/juggluco-foss-continuous-glucose-montior-diabetes/) about my diabetes diagnosis this year and my difficult choice to wear a proprietary device (called a CGM) on my arm 24/7 to continuously monitor my glucose levels. Like my friend and colleague, Karen M. Sandler — who previously made a much higher-stakes choice to receive a proprietary implanted defibrillator to keep her safe given her genetic heart condition — I reluctantly chose to attach proprietary hardware and software to my body.

The device itself is quite proprietary, but fortunately the FOSS community has reverse engineered its activation and data collection protocols — creating an Android application that does a better job than the manufacturers' proprietary ones <sup><a href="https://sfconservancy.org/blog/2025/dec/23/seven-abbott-freestyle-libre-cgm-patients-dead/#footnote-juggluco-previous-post">0</a></sup>.

Here in the USA, we strangely use capitalism as the center of our health care system. Two major for-profit competing brands of CGM are available here. My diabetes specialist prefers the (ironically named) Freestyle Libre Plus from Abbott. I (also rather strangely) bring a prescription for *electronics* to a pharmacy every month. On 2025-12-03, that pharmacy sent me an alarming text message (shown here).

### Abbott Killed Seven Patients

After reading that text, I found [the USA FDA announcement](https://www.fda.gov/medical-devices/medical-device-recalls-and-early-alerts/early-alert-glucose-monitor-sensor-issue-abbott-diabetes-care). My spouse cross-referenced the lot numbers while I read them off from all my Freestyle boxes <sup><a href="https://sfconservancy.org/blog/2025/dec/23/seven-abbott-freestyle-libre-cgm-patients-dead/#footnote-no-match-abbott-site">1</a></sup>. I had indeed recently worn an impacted device!

Only because my diabetes is so early of a stage was I relatively safe. The FDA reports that Freestyle injured over 700 people and **killed seven people** with this bug. Specifically, the bug caused the device to falsely report an *extremely low* glucose level. Advanced stage diabetics use low reading information to inform them that they may have too much insulin currently. The usual remedy is to eat something sugary to raise glucose in the blood. Such should be done only with great care, as a false low reading can harm and even kill the patient (who eats a high-sugar-content item while glucose in the blood is, in fact, not low).

Proprietary software in medical devices harming patients is not new. In 1985, the [Therac-25 killed three people](https://en.wikipedia.org/wiki/Therac-25#Problem_description). In 2020, hundreds of patients who relied on a financially troubled tech startup found their occular implants suddenly unsupported. Some patients went [blind as the devices powered down without updates](https://spectrum.ieee.org/bionic-eye-obsolete). There are more examples that I could include here, but rereading these horrific stories is frankly more than I can take right now when I think of fellow diabetes sufferers who were “killed by code” recently..

### Would FOSS Have Saved Patients' Lives?

It's hubris for activists to guarantee that harm would be prevented if Freestyle had publicly released the hardware specifications and the complete, corresponding source code (CCS). FOSS isn't immune to bugs — even dangerous ones. However, in the centuries since the Enlightenment, we know that the scientific method *depends* on public disclosure about data and wide-reaching peer review of past work. FOSS (plus a publicly disclosed hardware design) wouid allow the millions of hardware and software engineers to peer-review the integrity, security, and safety of the devices to which patients entrust their lives. We achieve the promise of humanity when we each entrust our safety and health to our entire community — not merely a single for-profit entity.

We also will probably never know whether this issue was in hardware or software. The bug disclosure is incredibly vague, and it remains unclear how much investigation was done (if any) by government regulators into this problem. As a public policy and public health matter, the public *deserves to know* the technical details (software and hardware) of both the functioning device and the failed devices. NGOs should be permitted to perform their own investigations and confirmations of public safety.

### What's Next?

Given that the hardware, software, and medical for-profit industries refuse to put the rights, safety and security of patients first, wrongful death lawsuits are typically the only way to hold these companies accountable. Yet, there are *very few* people who have not agreed Abbott's toxic terms of their proprietary companion application — I guestimate that fewer than 1% of Freestyle-using patients have used Juggluco from their very start (and thus never agreed to Abbott's terms). This is significant because Abbott [includes a comprehensive one-way indemnity for themselves in the terms](https://sfconservancy.org/videos/2025-09_Abbott-Freestyle-Libre-Plus-App-Agreement.pdf#page=78). I hope that a class action suit begins soon on this matter, but I wonder and worry that so much of the class may have signed this indemnity (which may make the road to justice bumpier).

Finally, I want to offer that if there is anyone out there who does tear-downs of extremely tiny electronic devices, I would be thrilled to find a volunteer who would like to see if we can either extract any software components from the device, or reverse-engineer the hardware. I have saved and sanitized all of my prior CGMs. I'd gladly send one along to anyone who wants to give a try at taking them apart. (Contact SFC or [contact me on the Fediverse (via Mastodon)](https://fedi.copyleft.org/@bkuhn) if you're available to do this work.)

For my part, I look forward (after the [Vizio](https://sfconservancy.org/vizio) trial) to sending some patches to Juggluco and also getting Juggluco available in F-Droid. Our best option in the face of these powerful medical device companies curtailing our rights is to invest our volunteer time into the edges where FOSS has resiliently worked around the constant roadblocks erected by bad actors.

---

<sup><a href="https://sfconservancy.org/blog/2025/dec/23/seven-abbott-freestyle-libre-cgm-patients-dead/#return-juggluco-previous-post">0</a></sup> My [prior post about CGMs discussed](https://sfconservancy.org/blog/2025/nov/06/juggluco-foss-continuous-glucose-montior-diabetes/) the GPLv3'd Juggluco in more detail.

<sup><a href="https://sfconservancy.org/blog/2025/dec/23/seven-abbott-freestyle-libre-cgm-patients-dead/#return-no-match-abbott-site">1</a></sup> In a fascinating turn of events, at least one of my past monitors (of which I fortitously saved all the boxes with the lot/serial number on them) is listed in [the FDA's spreadsheet](https://www.fda.gov/media/189900/download?attachment) as recalled lot, yet the serial number is listed as “ safe to use” on [Abbott's webform](https://www.freestylecheck.com/us-en/product-lookup.html) 🤔 … I'm left wondering how I can trust Abbott to write reliable software stuck into my arm if they can't even write a web form that cross-references serial numbers to lots correctly 😬.

[\[permalink\]](https://sfconservancy.org/blog/2025/dec/23/seven-abbott-freestyle-libre-cgm-patients-dead/)

[Other Conservancy Blog entries…](https://sfconservancy.org/blog/)  




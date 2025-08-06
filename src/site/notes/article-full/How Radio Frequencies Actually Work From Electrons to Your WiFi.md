---
{"dg-publish":true,"permalink":"/article-full/how-radio-frequencies-actually-work-from-electrons-to-your-wi-fi/","title":"How Radio Frequencies Actually Work: From Electrons to Your WiFi","tags":["article","full"],"created":"2025-07-07T00:01:27.149+07:00","updated":"2025-07-07T00:02:09.033+07:00"}
---


## How Radio Frequencies Actually Work: From Electrons to Your WiFi  

Source: [adrelien.com](https://adrelien.com/how-radio-frequencies-actually-work-from-electrons-to-your-wifi/)  

#RadioFrequency #WirelessCommunication #RFTechnology #ElectromagneticWaves  

Right now, as you're reading this, your device is performing a feat that would seem like magic to anyone just a century ago. Your phone is negotiating with distant cell towers, your WiFi router is streaming high-resolution video, and if you've got any IoT devices, they're whispering to each other using protocols like LoRa. All of this happens through radio frequency (RF) signals - electromagnetic waves that carry information through the air at the speed of light.

But what exactly are these signals? How do digital bits in your device's memory transform into physical waves that can traverse a room or an entire city? Let's dive into this invisible world.

### Everything Starts With Current

At the most fundamental level, RF signals originate from a basic principle of physics: a changing electric current in a conductor creates a corresponding changing electromagnetic (EM) field. When this change happens rapidly enough - at radio frequencies - the EM field doesn't just stay around the conductor; it detaches and propagates outward as an electromagnetic wave.

Your antenna isn't just a passive piece of wire - it's a transducer. Its specific shape and size are meticulously designed to efficiently convert a rapidly alternating electrical current into a traveling electromagnetic wave for transmitting, and conversely, to convert a passing wave back into a tiny electrical current for receiving.

Here's a simple thought experiment: imagine you could short-circuit a battery exactly 2.4 billion times per second. Each time you connect the short, current flows. Each time you disconnect it, current stops. If you could do this at exactly 2.4 billion times per second, you'd create a 2.4 GHz signal - the same frequency as WiFi. Of course, this is impossible with any mechanical system, but it illustrates the fundamental concept: RF signals are rapidly changing electrical current at precise frequencies.

### Making Noise Meaningful

Now, a pure oscillating signal is just noise - like a constant tone. To carry actual information, we need to modify that signal in specific ways. This is where modulation comes in.

Modulation is the process of changing some property of your carrier signal to encode information. Think of your carrier wave as a blank canvas - modulation is how you paint data onto it.

**Amplitude Modulation (AM):** In AM radio, we change the amplitude (strength) of the signal. Imagine you're humming a constant 1000 Hz note, but you make it louder and quieter to spell out morse code. When you want to send the letter "A" in morse code (dot-dash), you might make the signal strong for a short time (dot), then weak, then strong for a longer time (dash). The frequency stays the same, but the volume changes carry the information.

**Frequency Modulation (FM):** FM does something different. Instead of changing the volume, it slightly shifts the frequency up and down. Let's say you want to send the letter "A" using FM. You might start with your 1000 Hz carrier, then shift it to 1001 Hz for a short time (representing a dot), back to 1000 Hz, then to 1002 Hz for a longer time (representing a dash). The amplitude stays constant, but the frequency changes encode your data. This is why FM sounds clearer than AM - frequency changes are less affected by electrical interference than amplitude changes.

**LoRa (Long Range):** LoRa is fascinating because it uses something called chirp spread spectrum. Instead of just changing amplitude or frequency at fixed points, LoRa rapidly sweeps the frequency up and down in specific patterns called "chirps." Each chirp pattern represents different data. It's like having a musical signature where different frequency "melodies" mean different things. This technique makes LoRa incredibly resistant to interference and allows it to travel much farther than traditional methods.

### The Speed Challenge: How Do We Switch So Fast?

Here's where things get interesting. Modern wireless communications operate at mind-boggling speeds. Your WiFi router is switching at 2.4 GHz - that's 2.4 billion times per second. Bluetooth, cellular, GPS - they're all operating at similar or even higher frequencies. How do we achieve these speeds?

The answer lies in finding something that can vibrate fast enough to control electrical circuits at these frequencies. Enter the humble quartz crystal.

### Nature's Perfect Oscillator

The foundation of stable RF generation is the quartz crystal oscillator. Quartz is a piezoelectric material - it physically deforms when voltage is applied and, conversely, generates a voltage when it deforms. When a precisely cut piece of quartz is placed in an electronic circuit, it can be made to resonate at an incredibly stable and predictable frequency.

The frequency is determined by the crystal's physical dimensions. Cut it precisely, and you get a precise frequency. A crystal can vibrate billions of times per second with almost no variation - this stability is what makes modern RF communication possible.

But here's the key insight: once we have this stable frequency source, we can control it electronically. By varying the voltage applied to the crystal circuit or using additional circuitry, we can slightly shift the frequency up and down. This is how we can modulate the frequency to encode data - the crystal provides the stable foundation, and we add controlled variations on top of it.

### The CPU Connection: Crystals All the Way Down

Here's something that might blow your mind: your CPU is actually just a crystal oscillator with a lot of fancy logic built around it. That ESP32 you're using for your IoT projects? At its heart, it's got a crystal oscillator running at maybe 40 MHz, and all the processor's operations are synchronized to that crystal's vibrations.

So technically, you can generate RF signals directly from a CPU. Take that ESP32, write some code to rapidly toggle a GPIO pin, and you're essentially creating a square wave at whatever frequency you program. If you toggle it 2.4 million times per second, you get a 2.4 MHz signal.

In fact, some people do exactly this for quick and dirty RF generation. You can literally output a signal from your microcontroller pin and, with the right antenna, transmit data. It's not pretty, but it works for basic applications.

But there's a fundamental problem with this approach…

### The Harmonic Reality: Why Real RF is Complex

When you generate a square wave from a CPU pin, you're not creating a clean sine wave - you're creating a signal full of harmonics. These are multiples of your base frequency that can interfere with other devices and violate radio regulations.

If you're generating a 2.4 MHz square wave, you're also generating harmonics at 4.8 MHz, 7.2 MHz, 9.6 MHz, and so on. This is why real RF systems use filters, amplifiers, and other components to clean up the signal and suppress unwanted harmonics.

But harmonics aren't always bad. RF engineers use them cleverly to reach higher frequencies. A crystal oscillator provides a rock-solid reference frequency, typically in the tens of megahertz. But how do we get the 2.4 gigahertz needed for WiFi? It's impractical to cut a crystal that resonates that fast.

This is where the Phase-Locked Loop (PLL) comes in. A PLL is a brilliant control system that acts as a frequency multiplier. It takes the stable low-frequency signal from the crystal as a reference and uses it to control a much higher-frequency oscillator, called a Voltage-Controlled Oscillator (VCO). The PLL continuously compares the VCO's output to the crystal's reference signal and adjusts the VCO to keep it perfectly locked at a precise multiple of the reference.

In essence, the PLL "listens" to the steady beat of the crystal and forces the high-frequency VCO to run at, for example, 60 times the reference frequency, transforming a 40 MHz reference into a pristine 2.4 GHz carrier wave.

### TCXO vs Standard Crystals

Not all crystal oscillators are created equal:

**Standard Crystal Oscillators (XTAL):** These are your basic crystals. They provide stable frequency generation, but temperature changes can cause slight frequency drift. For many applications, this is acceptable.

**Temperature Compensated Crystal Oscillators (TCXO):** These include additional circuitry that monitors temperature and compensates for the crystal's drift. The result is a frequency source that stays locked to its target frequency even when temperatures fluctuate. These are essential for precision applications like GPS, cellular base stations, and high-end RF communications.

**Oven-Controlled Crystal Oscillators (OCXO):** These go even further, housing the crystal in a tiny, heated "oven" to maintain a constant temperature, providing the ultimate in frequency stability for critical infrastructure like cell towers and base stations.

**Voltage-Controlled Oscillators (VCO):** Unlike fixed-frequency crystals, VCOs generate a frequency that can be adjusted by varying the input voltage. While not as stable as crystal-based oscillators, they are crucial in applications requiring tunable frequencies, such as PLLs (Phase-Locked Loops), RF modulators, and synthesizers. VCOs can be combined with crystals in systems like TCXO and OCXO to provide both stability and tunability.

The difference between XTAL and TCXO can be the difference between a signal that drifts off frequency and one that stays rock-solid stable in real-world conditions.

### From Chip to Air: The RF Front-End

The modulated signal generated by the PLL and modulator is still incredibly weak. It needs to be prepared for its journey through the air. This happens in the RF front-end, a chain of specialized components:

**Filtering:** The signal is passed through precise filters to remove any unwanted harmonics and ensure it doesn't interfere with other devices on adjacent frequency bands.

**Amplification:** A Power Amplifier (PA) boosts the signal's strength from microwatts to the level needed for effective transmission, all without distorting the carefully modulated information.

**Antenna:** The final, amplified signal is sent to the antenna, which efficiently radiates the energy out into the world as an electromagnetic wave.

### The Quartz Watch Connection

The quartz watch on your wrist demonstrates this same principle. Inside is a tiny crystal vibrating at 32.768 kHz. Why that specific frequency? Because it's 2^15 Hz - divide it by 2 fifteen times, and you get exactly 1 Hz, or one pulse per second. Perfect for keeping time.

The same crystal technology that keeps your watch accurate to within seconds per month is what makes your WiFi router, cell phone, and LoRa sensors work - just at much higher frequencies and with more sophisticated control circuits.

### Putting It All Together

So there you have it - RF communication is an elegant symphony of precise engineering. It starts with the fundamental physics of changing current creating electromagnetic waves, uses crystal oscillators for stable frequency generation, employs PLLs to reach the exact frequencies needed, modulates those frequencies to carry data, and carefully filters and amplifies the result before launching it into the air.

The next time you connect to WiFi or send a LoRa message, remember: somewhere in that device, a tiny piece of quartz is vibrating millions or billions of times per second, controlling sophisticated circuitry that creates the invisible waves carrying your data through the air at the speed of light.

It's a testament to human ingenuity that we've learned to harness these natural phenomena to create the wireless world we live in today.  

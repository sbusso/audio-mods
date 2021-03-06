# DBX 160XT

Note: I'm using the _unbalanced_ output!

### Recipe

| Part | Before  | After     | Notes |
| ---- | ------- | --------- | ----- |
| U1   | LF353   | OPA2134   | Input op amp |
| U2   | LF351   | OPA134    | Unbalanced output, driving transistor pair |
| U8, U9 | LF353   | OPA2134   | Sidechain. According to [Jim Williams](http://www.gearslutz.com/board/geekslutz-forum/53182-dbx-160xt-mods-schematic.html): "The non-linear capacitor circuit also benefits from the use of a very low noise fet input opamp...The 353's are too noisy and add THD to the mix." I _think_ this is right, but I could be wrong. |
| U11  | DBX1252 | THAT2180A | Bend back or cut off pin 4 to circumvent trimming circuitry. The THAT2180 series is pre-trimmed. |
| C16  | 1uF 63V Film | 2.2uF Solen "Fast Cap" | I had it lying around and it fit. Don't judge me. P.S. I had to remove TP9 to make room. |
| C14, C18 | 1uF 50V Elec | 56uF 50V Panasonic FR | Decoupling U1. Bypassed with 0.01uF ceramic beneath the PCB. |
| C35, C46 | 1uF 50V Elec | 56uF 50V Panasonic FR | Decoupling U8. Bypassed with 0.01uF ceramic beneath the PCB. |
| C10, C56 | 1uF 50V Elec | 56uF 50V Panasonic FR | Decoupling U9. Bypassed with 0.01uF ceramic beneath the PCB. |
| C25 | 10uF 50V Elec | 56uF 50V Panasonic FR | Decoupling U2. It uses one cap rail-to-rail instead of two caps to ground. Unusual, but the OPA134 seems stable. |
| C27, C31 | 22uF 25V Elec | 22uF 50V Panasonic FR | Around unabalanced output transistor pair. I _think_ I know what they do, but I'm not 100% certain, so I used original values. |
| C9, C48, C50, C51, C52, C54 | 1uF 50V Elec | 1.5uF 50V Wima MKS2 | Decoupling U5, U6, U7 (4558). I used film caps only because I had them and they fit. |
| C58, C59 | 1uF 50V Elec | 1.5uF 50V Wima MKS2 | Decoupling U10 (LM339). See above. |
| C17 | 10uF 50V Elec | 10uF 50V Panasonic FC | Hanging off VCA pin 7 (Vcc). Could probably have upsized, but I don't understand enough to be certain. |
| C39, C42 | 1uF 50V Elec | 1uF 50V Wima MKS2 | RMS detector. Probably decoupling, but time constants can be tricky. I decided to use the same values. |
| C40, C43 | 10uF 50V Elec | 10uF 50V Panasonic FC | RMS detector. See above. |
| C3, C4, C5, C6 | 470uF 50V Elec | 560uF 50V Panasonic FR. | PSU pre-regulator filter. I'd like to use 1000uF, but they don't quite fit. |
| C7, C8 | 22uF 50V Elec | 220uF 50V Panasonic FR | PSU post-regulator filter. Bypassed with .1uF poly beneath PCB. |
| C41 | 10uF 25V Elec | 10uF 50V Panasonic FC | Leave as 10uF since I believe this is part of the timing cirtcuit. Probably unnecessary, but I measured several and chose the closest to 10uF. |
| CR13, CR14, CR15, CR16   | Probably 1N400-Something | 100V 1A Schottky Diode | Dubious difference, but I wanted to try it out. |
| C62 | 1uF 50V Elec | 1uF 50V Wima MKS2 |  I _think_ this is a companion RMS circuit for the meter driver, so I used matching values. |
| C63 | 10uF 50V Elec | 10uF 50V Panasonic FC |  See above. |
| C64 | 10uF 25V Elec | 10uF 50V Panasonic FC | See above. |

### Bill of Materials

| Qty | Part  | Mouser #  |
| --- | --------------- | --------- |
| 1   | OPA134 Single FET-input Op Amp | 595-OPA134PA  |
| 3   | OPA2134  Dual FET-input Op Amp   | 595-OPA2134PA |
| 1   | THAT2180A VCA | 887-2180AL08-U |
| 6   | 0.01uF TDK C0G Ceramic Capacitor | 810-FK18C0G1H103J |
| 2   | 0.1uF Panasonic ECWF Polypropylene Capacitor | 667-ECW-F2104HAB |
| 3   | 1uF Wima MKS2 Polyester Capacitor | 505-MKS21/50/10 |
| 8   | 1.5uF Wima MKS2 Polyester Capacitor | 505-MKS21.5/50/10 |
| 1 | 2.2uF Solen "Fast Cap" Polypropylene Capacitor (SOLEN-51548) | N/A. Try [PartsConnexion](http://www.partsconnexion.com/capacitor_film_solen_pb.html), or substitute any good 2uF - 4uF polypropylene that you can fit in there. |
| 6 | 10uf 50V Panasonic FC Electrolytic Capacitor | 67-EEU-FC1H100L |
| 2 | 22uf 50V Panasonic FR Electrolytic Capacitor | 667-EEU-FR1H220 |
| 7 | 56uf 50V Panasonic FR Electrolytic Capacitor | 667-EEU-FR1H560 |
| 2 | 220uf 50V Panasonic FR Electrolytic Capacitor | 667-EEU-FR1H221 |
| 4 | 560uF 50V Panasonic FR Electrolytic Capacitor | 667-EEU-FR1H561 |
| 4 | 100V 1A Schottky Diode | 625-SB1H100-E3 |
| 4 | DIP8 Socket | 115-43-308-41-003000 |

### Thoughts, Notes and Errata

I'm using the _unbalanced_ output, so I've left the balanced output alone. That said, even if I were using it, I'd still probably leave the 5534's in there. If I wanted to enhance the balanced output, I'd probably try inserting a transformer, either an Edcor WSM600/600 if I could fit it or the original Jensen [JT-123-DBX](http://www.jensen-transformers.com/datashts/123dbx.pdf) if I couldn't.

I chose OPA2134/OPA134 to replace LF353/LF351 because it's my default FET-input op amp. It worked well on the first go, so I moved on. There may be some super-duper god chip that works better, but I find enough uses for OPA2134's that I can buy them by the dozen. In my humble experience, capacitors will make a bigger difference anyway.

I chose a lot of parts because that's what I had lying around. For instance, 
* when replacing the 1uF electrolytic decoupling caps, I grabbed some 1.5uF Wima polyester film caps. Who makes 1uF electrolytics nowadays, anyway? 
* I used that 2.2uF Solen because I had it from years ago. 
* I used 10uF Panasonic _FC_ instead of my preferred _FR_ because the big distributors don't seem to stock the latter.

There's a lot of uncertainty in my mind about exactly what does what in this circuit, especially around the VCA, RMS detectors and the timing bits in general. After all, I'm an amateur working from fuzzy and partial schematics. I've gone out of my way to leave a few parts the same, even when I think it's unnecessary. I figure that any change in sound from a suboptimal VCA coupling capacitor is minimal. The change in sound from screwing up a time constant is huge.

### Questions and TODOs

Should I consider reducing R17 and R22? These look like they drop the unregulated 24V to something closer to 16V for U2. The old LF351 drew around 3.6mA quiescent current, so 2k2 would drop right around 8V. The OPA134 draws 4mA (up to 5mA), dropping 8.8V (up to 11V). In addition, the OPA134 can take up to +-18V, which would imply a 1k5 resistor. But how does this affect the downstream circuit? Should R19 and R25 be changed to keep 4k4 over the associated resistor pairs?

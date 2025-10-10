# The CMOS Inverter - The Transistor That Built the Modern World

Advances in electronics have followed Moore's Law, scaling feature sizes every generation and doubling transistor integration capacity every two years, resulting in the complex chips of today. The design complexity has only increased and gets much attention, but the technology that enables the physical conception of the said design is often overlooked. Even as semiconductor technology approaches nanoscale dimensions of just a few atoms across, CMOS remains the first commercially successful and fully established technology for digital integrated circuits, and the basis for future technologies. This article provides a surface-level look at CMOS technology, focusing on its most fundamental building block: the CMOS inverter.

---

## A Brief History of Transistors (BJT and MOSFET)

The transistor originated from thermionic vacuum tubes, invented in 1907, which were large, fragile, and energy-intensive devices used in radios, TVs, and radar. In the 1920s, Julius Edgar Lilienfeld patented the concept of a solid-state transistor, but the semiconductor technology needed to realize it did not yet exist. The first practical transistors were developed in 1947 by Bardeen, Brattain, and Shockley at Bell Labs, with Shockley patenting the first bipolar junction transistor in 1948. It was not until the early 1960s that Atalla and Kahng successfully built a working MOSFET, roughly three decades after Lilienfeld first proposed the idea. The original MOSFETs were slow, unreliable, and prone to temperature and time-related drift, making them impractical for most applications. Over time, however, MOSFETs became faster, more stable, and highly reliable, eventually becoming the cornerstone of modern electronics.

The following are a few major discoveries and inventions along the timeline, making modern-day MOSFET and CMOS technology possible: 

1. **Electronics theory of semiconductors – Alan Wilson:**

   * Described the principles of electrical conductivity in semiconductors, laying the theoretical foundation for modern integrated circuit (VLSI) technology.

2. **Controlled silicon impurification and p–n junction formation – Russell Ohl:**

   * Demonstrated the process of doping and the creation of p–n junctions, which are fundamental to the operation of all modern transistors.

3. **Bipolar transistor design with junctions – Shockley, Bardeen & Brattain:**

   * Developed the structure and operation principles of the first practical bipolar junction transistors.

4. **Technological processes of diffusion and oxidation – Calvin Fuller & Carl Frosch:**

   * Introduced controlled diffusion for precise doping and thermal oxidation for the growth of SiO₂ layers on silicon wafers, both critical steps in semiconductor fabrication.

5. **Photolithographic technique – Jules Andrus & Walter L. Bond:**

   * Pioneered the method of transferring circuit patterns from a mask onto silicon wafers using light-sensitive photoresist, enabling precise microfabrication.

6. **Planar process – Jean Hoerni:**

   * Developed a transformative technique for fabricating transistors beneath a protective SiO₂ layer, greatly improving reliability and manufacturability.

7. **Monolithic integrated circuit – Robert Noyce:**

   * Invented the method to integrate multiple transistors, resistors, and interconnects on a single silicon chip, forming the basis of modern VLSI systems.

---

## The CMOS Technology

The work on MOSFETs by Atalla and Kahng was later picked up and built upon. Chih-Tang Sah and Frank Wanlass at Fairchild Semiconductors conceptualized the CMOS logic family and the CMOS fabrication technology in 1963. 

> A logic family is a group of circuits that implement digital logic (AND, OR, NOT, etc.) using the same circuit principles.
> Technology, in this context, means the method of fabricating the device.

CMOS logic family contains circuits that incorporate the _Complementary MOS_ logic, which are built using the pull-up network (made of PMOS) that is functionally the _complement_ of the pull-down network (made of NMOS). 

![cmos_logic_circuit](/cmos/images/cmos.png)

Essentially, since the networks are complementary, in digital circuits that deal with 0s and 1s only, either the pull-up or pull-down network would be active at a time. Thus, the _static power_ (when inputs are constant) consumed by the circuit is ideally zero and practically near zero (transistors are not ideal, so some leakage is involved).

When the inputs change (or switch), given the transistors are non-ideal, both NMOS and PMOS transistors are switched on momentarily. This causes a direct path (DC path) from V<sub>DD</sub> to Gnd. This contributes to _short circuit power_. The output of the circuit also drives the input of another circuit it's connected to (which is essentially charging/discharging the load capacitance). This contributes to _dynamic power_. _Dynamic power_ is significantly higher than the _static power_ and _short circuit power_. Regardless, the overall consumption is much lower than having significant _static_ and _dynamic_ power, as in BJT or NMOS-only circuits. This is one of the two main reasons why the CMOS logic family is predominant (the other being high noise immunity - discussed later //add hyperlink if possible). This also means that significant power consumption is dependent on the switching frequency, which is directly related to the operating frequency. In a sense, the power dissipation can be controlled by changing the operating frequency. It's a tradeoff based on the application requirements of faster operation or low power. 

On the other hand, CMOS technology hadn't truly kept up. In the early 1960s, NMOS technology was still predominantly used, alongside BJTs. But in 1965, Gordon Moore (from Intel) made an empirical observation and prediction that: 
> _The number of transistors on a computer chip would approximately double every two years, leading to a significant increase in computing power while reducing the cost per transistor_

(It's important to note that this is not a _law_. Unlike Newton's _laws_ of motion, for example, this was simply an observation, initially. And companies have strived to keep up with it, hence it has turned into a prediction. Though some argue that it has been failing recently, some say there are extensions to it. Read more [here](https://medium.com/@sasly204800/is-moores-law-ending-b6da8da0f20a))

This pushed the semiconductor industry to improve constantly, but it was hard to keep up with due to increased power consumption (due to increased transistor density). This made the low-power CMOS technology more attractive compared to BJTs or NMOS-only circuits. Coupled with Dennard's scaling, which stated roughly that:
> _As transistor dimensions shrink, the power density remains constant because both voltage and current scale downward with the size reduction, allowing the power use to stay in proportion with area_

the revolution in ICs was unprecedented. CMOS enabled a smooth adoption of both the laws and, thus, by the 1980s, it became the most widely used technology. This era dictated the performance by decreasing the transistor size, which increased the operating frequency (less delay since transistors were physically closer, electrons could travel faster) and decreased the cost of production (more transistors in the same silicon area meant less area per transistor, so overall less money spent per transistor). And the basic building block of all digital circuits was: the _CMOS_ inverter. 

---

## The CMOS Inverter

An inverter is not a universal gate. But it is called the fundamental building block because of the similarity between a CMOS logic circuit and an inverter: PMOS to pull-up network, NMOS to pull-down network. A CMOS logic circuit always implements the logical complement of a given function, much like an inverter; hence, their operation is almost identical (not completely, since an inverter has only one PMOS and one NMOS, but other logic circuits can have many). Often, a university curriculum includes a detailed analysis of the CMOS inverter because it's the foundation for understanding the CMOS logic family and CMOS technology. 

> In digital logic design, a universal logic gate can be used to implement any Boolean logic equation. E.g., NAND/NOR gates.

### Static operation

![inverter](/cmos/images/inverter.png)

Suppose, initially, the input is at a stable 0, and the output is at a stable 1, then the NMOS is off and the PMOS is on. 
- When V<sub>in</sub> starts increasing, the initial state is maintained (in Region A).
- When V<sub>in</sub> reaches beyond the threshold voltage of NMOS, NMOS turns on (saturation region) and V<sub>out</sub> starts decreasing. (Region B) PMOS is in the  linear region here.
- Eventually, in Region C, V<sub>in</sub> = V<sub>out</sub>. This is the transition period that produces maximum short circuit current (since both MOSFETs are in saturation). If this is narrow, the short-circuit power dissipated decreases.
- Region D operation is similar to Region B, but now NMOS is in the linear region and PMOS is in saturation.
- When V<sub>in</sub> goes to V<sub>DD</sub>, NMOS is in the linear region and PMOS is switched off. (Region E)

### Dynamic Operation

![dynamic_cmos_inverter](/cmos/images/power3.png)

During switching in a CMOS inverter, the input and output are capacitively coupled through parasitic capacitances.
When the input voltage changes quickly (high frequency operation), this coupling capacitor momentarily tries to maintain the same voltage difference between input and output:

Input rises → output overshoots (goes slightly above V<sub>DD</sub>)

Input falls → output undershoots (goes slightly below 0 V)

These brief spikes occur because the capacitor resists sudden voltage changes, causing transient noise and a slight delay before the output settles.

### Power dissipation

![power](/cmos/images/power.png)

- Dynamic power is dissipated while charging or discharging the load capacitor.
- Short-circuit power is dissipated due to a DC path between the power and ground rails. (In Region B, C, D)
- Static power is dissipated when the input is constant and the device is in a steady state. (In Region A and E)

### Noise Immunity

In digital circuits, logic levels are not single voltages but ranges of voltages: a HIGH and a LOW are represented by voltage intervals rather than precise values. For example, a HIGH might be any voltage above a certain threshold, and a LOW any voltage below another threshold. This ensures that small variations or fluctuations in voltage do not cause incorrect logic interpretation. The circuit's ability to tolerate noise signals is referred to as the noise immunity, and the noise margin is a  quantitative measure of this tolerance. 

![noise](/cmos/images/noise.png)

To get the maximum noise margin, so we get maximum noise immunity, V<sub>OH</sub> = V<sub>DD</sub> and V<sub>OL</sub> = 0. This is only possible if PMOS is responsible for pull-up and NMOS for pull-down, which is the case in any CMOS logic circuit. PMOS, as a device, passes logic 1 well, which means the output voltage can reach up to V<sub>DD</sub> if the input voltage is low. Similarly, NMOS passes logic 0 well. (Read more [here](https://siliconvlsi.com/why-pmos-pass-strong-1-and-weak-0/)). High noise immunity is the second (of the two) main reasons why the CMOS logic family is predominantly used. 

More complex logic functions can be created by putting additional devices in parallel or in series with the basic inverter transistors, but in every configuration, the "active" level of the output is opposite to that of the input(s), as we know. Therefore, to create "positive logic" in CMOS, you must always have two stages, where the second stage is usually just an inverter that has good drive characteristics for high fanout. The circuits themselves don't usually have a strong current drive because, to get more current, wider transistors are required. Instead of having all wide transistors in a circuit, which increases the area consumed, having only two wide transistors (in the inverter) is more efficient. This gives another reason to use the CMOS logic family.

---

## Current Trends and Future Possibilities

- Moore's law and Dennard's scaling served exceptionally well from the mid-1980s to the early 2000s, when Dennard's law "ended".
- Since individual processor speeds topped at 3 GHz, to get more performance, multi-core systems (multiple processors on a single chip) were introduced, which quickly hit it's efficiency limits due to Amdahl's law (roughly stating, maximum speedup is limited by the part of the task that must be done sequentially, so beyond a number, cores don't contribute to performance increase). Currently, heterogeneous systems (SoC or System on Chip) and hardware accelerators are the trend (integrating specialized hardware with processors).
- Moore's law is still being kept alive (according to a few), except the initially monolithic notion of IC (on a single piece of silicon) has now expanded to _chiplet_ technology, where multiple dies are integrated inside a single package, often on an interposer or using advanced packaging (2.5D or 3D).
- HKMG was introduced after CMOS scaling hit the leakage limit of SiO₂/poly-Si gates, providing low leakage, high performance, and continued transistor miniaturization (for 45nm and below). Surprisingly, the 'M' in CMOS hasn't meant 'metal' since it was replaced by polysilicon, one of the reasons being easier fabrication. 
- The planar transistor approach started to have problems with excessive leakage, even with Hi-k metal gate. Thus, the transition to finFETs (22nm and below). 
- In 2023, the transition from finFETs to Gate-All-Around (GAAFET) happened (3nm or 2nm).
- CFET technology that, instead of manufacturing the P-transistors and N-transistors on the same wafer directly, stacks them, with the N-transistors on top of the P-transistors, so taking up about the same space as a single transistor, leading to an increase in density and decrease in space, is in development. 

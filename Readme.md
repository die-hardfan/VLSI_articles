# The Verification Mindset: Ensuring First-Time-Right Silicon

The Semiconductor industry is at the forefront of human innovation. As semiconductor designs grow denser and more heterogeneous — with billions of transistors interacting across analog, digital, and mixed-signal domains — ensuring a ‘First-Time-Right’ silicon has never been harder. Verification is the first safeguard, catching design flaws before they escape into silicon. This article only touches the tip of the humongous iceberg that is chip verification.

---
## The Meaning of Verification

Verification is the process of ensuring any given design meets/adheres to the given specs (or specifications). In short, it's the first attempt at answering the question:
> _Does this design do what it's intended to do?_

First attempt because, throughout the chip design and manufacturing flow, there are multiple points where it's mandatory to pause and ask this question. For example, _verification_, _validation_, and _testing_ all ensure the adherence to spec, just at different stages and with different expectations.

![verification_validation_testing](/images/veri_vali_test.png)

>  Verification is a process in which a design is tested (or verified) against a given design specification before tape-out.

It handles the chip design in its soft copy (software) only. Hence, sometimes called **Pre-silicon validation**. 

>  Validation is a process in which the manufactured design (chip) is tested for all functional correctness in a lab setup.

This is done using the real chip assembled on a test board or a reference board along with all other components part of the system for which the chip was designed for, so that all the use cases possible of the chip when truly deployed can be tested in real time. 

>  Testing (Manufacturing/Production test) involves screening manufactured chips for faults or random defects, reliability, functional defects and electrical characterization before volume shipment.

This involves the post-assembly functional, mechanical, electrical, etc., testing, the success of which marks the end of the current chip design and manufacturing flow. Of course, the maintenance comes next, but that is largely software, and little can be done to correct any mistakes unless all the deployed products are recalled. 
ASICs are effectively frozen once fabricated, so any flaw can require costly respins or recalls. FPGAs are reconfigurable, but still need verification, since field updates are often impractical and debugging post-deployment can be difficult.  

---
## The Significance of Verification and the Concept of First-Time-Right Silicon

Verification is like a feedback system. Any improvement or additions to the design must be _searched_ for bugs, syntactical, logical, functional, etc. This is reported to the design team for modifications, and the process repeats. Hence, the design and verification of a chip (or an IC) happen in parallel. Rectification of bugs found earlier in the chip design flow costs less compared to those found at the end. This is largely due to the increasing details as we go lower in the abstraction levels.
For example, a simulation error is solved by changing the RTL code, which takes less time. But a timing violation (during STA) requires a relatively longer time and more effort to be solved (a setup failure, for instance, requires a redesign of the logic or other techniques to decrease the delay).  

Understandably, surveys (e.g., 2024 Siemens EDA / Wilson Research Group Functional Verification Study) indicate that 60–70% of engineering effort in chip projects belongs in verification. Even after that, the possibility of bugs remains non-zero, as verification cannot be exhaustive due to time constraints.
Bugs uncovered pose risks of functional failure, particularly so in critical systems like automotives, defense, and healthcare systems. This, in turn, results in loss of revenue and reputation for the company. Sufficient to say, _verification_ becomes one of the crucial components responsible for making or breaking the chips (and the companies).  

All this effort in verification builds towards the concept of **First-Time-Silicon** or FTR silicon, which requires that the chip manufactured in the first iteration of the chip design and manufacturing flow is fully functional. This is largely due to the expensive re-spins in case of a failure, and the unaffordability of chip deployment failure, given the all-pervasive nature of electronics. The need for FTR silicon is also fuelled by the short time to market, courtesy of the ever-evolving landscape of technology and increasing competitiveness of fellow organisations. 

> _“The industry has hit the lowest point ever in achieving first-silicon success. Historically, it’s been around 30%. Two years ago, it dropped to 24% and this year it dropped to 14%.”_ -Harry Foster, chief verification scientist at Siemens EDA

![Statistics](/images/study.jpg)

The decrease in FTR silicon success is due to increasing design complexities, within and outside the chip, and also due to increased specialisation of chips. From a few companies (fabless and foundry) to most companies today taking to designing custom chips, because it offers better control (among other reasons), the production of chips has increased. Without the right environment and workforce to drive this, FTR silicon becomes hard for novice companies, given the complexity. (According to the _2024 Siemens EDA / Wilson Research Group Functional Verification Study_)

---
## The Verification Flow and Available Techniques

![Verification_flow](/images/verificationflow.jpg)

At different stages of the flow, different techniques are used for verification. A combination of multiple techniques is usually more robust compared to any single one. The prominent four are:

- Simulation
    - Uses a testbench to generate and monitor the design ports (input and outputs)
    - The inputs are constrained, randomized (usually), and thus, not exhaustive
    - The outputs are visualised as waveforms or verified against expected outputs (using scoreboard and checkers)
    - Utilised mostly during the initial stages of the design flow, since code-level simulation requires fewer resources compared to gate-level or lower
- Emulation
    - Deploy the design on hardware (like an FPGA) and monitor it via a simulator
    - Relatively less time consumed 
- Formal verification
    - Mathematically proves the properties of the design
    - Exhaustive in nature (all possible inputs are verified)
    - A formally verified design has relatively more reliability
- Prototyping
    - The system where the chip will be used is built to verify/test its working
    - Helps in system-level testing
- Static Timing Analysis (STA) is used to identify timing violations.

After every modification, all the tests done till then are re-run on the design to ensure no new bugs are introduced. This is called _regression testing_.

Due to time and resource constraints, verification can't run forever. To decide when to stop the verification, metrics are used. Reaching a satisfactory level on a metric implies enough confidence in the design to proceed to the next stage in the chip design flow. An example is code coverage, which reports the percentage of all lines of code utilized when the design was simulated. 

---
## Current Trends and Future Possibilities

- Metric-driven verification is widely used currently.

- Timing-aware and power-aware simulations help in performance and power optimizations.

- AI models are being used for faster and insightful coverage analysis.
  
- Cloud-based companies are providing _Verification as a Service_ (VaaS) that utilizes the advanced computational resources can help in easier and faster simulations.

---

Each leap in semiconductor technology fuels advances in verification — from simulation acceleration to AI-driven coverage analysis. In turn, these improved verification methodologies enable the next wave of reliable, high-performance chips. It’s a virtuous cycle that drives the modern semiconductor revolution. 

This blog was an attempt at understanding chip verification as it stands today. The information is reliable to the best of my knowledge. If there are any discrepancies or mistakes, please feel free to contact me for corrections. 

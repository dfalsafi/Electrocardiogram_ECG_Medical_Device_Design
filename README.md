# 🫀Electrocardiogram (ECG) Medical Device Design

We designed a group-made ECG (input signal connected using electrodes) device that captures and digitizes the human pulse displayed on a plot. It started as an LTSPICE analog circuit. Once the desired amplified output signal was confirmed we designed a custom PCB and used a PIC24 microcontroller's ADC to plot the real-time heartbeat data in Python.

Overview
This project is a custom-designed Electrocardiogram (ECG) device made entirely from scratch to capture, filter, and digitize the human pulse for real-time visualization. Moving from initial software simulation to a fully custom printed circuit board (PCB) and physical hardware assembly, our team successfully built a complete analog-to-digital signal pipeline. The final output is read by a PIC24 microcontroller and plotted in real-time on a computer.

System Architecture & Hardware Design
Building an ECG from scratch required careful attention to signal integrity. The hardware pipeline was fully simulated in LTspice before moving to physical assembly. The analog signal chain is designed to extract the extremely small differential heartbeat signal (~1Hz) while rejecting surrounding noise:

Signal Acquisition: The system captures the human pulse as two raw differential signals directly from the body.

Instrumentation Amplifier (INA333): The differential signals are fed into an INA333 amplifier with a precisely set gain to amplify the microvolt-level heart signals.

Right Leg Drive (RLD) Circuit: To actively cancel out common-mode noise (such as 60Hz power line interference), we built a Right Leg Feedback circuit. This amplifies the common-mode signal using an OPA333 operational amplifier and feeds it back into the user's right leg.

High-Pass Filtering: The final analog stage utilizes an adjustable RC high-pass filter to eliminate low-frequency noise and baseline wander.

Output Buffering: The filtered signal passes through a final OPA333 amplifier to buffer and condition it for digital conversion.

📸 Hardware & Simulation Gallery
(Replace the links below with the actual paths to your images in your repository)

[Analog Circuit Design](https://github.com/dfalsafi/Electrocardiogram_ECG_Medical_Device_Design/blob/main/Hardware/Analog%20Design%20%26%20LTSPICE%20Simulation/EKG_Danny-20260504T213633Z-3-001/Circuit_Design.png)

[LTspice Simulation : Output Waveform](https://github.com/dfalsafi/Electrocardiogram_ECG_Medical_Device_Design/blob/main/Hardware/Analog%20Design%20%26%20LTSPICE%20Simulation/EKG_Danny-20260504T213633Z-3-001/Output_Waveform.png)

[Altium PCB Schematic](https://github.com/dfalsafi/Electrocardiogram_ECG_Medical_Device_Design/blob/main/Hardware/Altium%20Schematic%20and%20PCB%20Design/Schematic_Prints.pdf)

[Analog Circuit Design](Hardware/Analog%20Design%20%26%20LTSPICE%20Simulation/EKG_Danny-20260504T213633Z-3-001/Circuit_Design.png)

[LTspice Simulation](Hardware/Analog%20Design%20%26%20LTSPICE%20Simulation/EKG_Danny-20260504T213633Z-3-001/Output_Waveform.png)

[Altium PCB Schematic](Hardware/Altium%20Schematic%20and%20PCB%20Design/Schematic_Prints.pdf)


Software & Digital Processing
Once the analog signal is cleaned and amplified by our custom circuit, it is passed to the digital domain for processing and visualization.

Microcontroller: PIC24

Firmware: Developed using MPLAB X IDE. The firmware configures the PIC24's internal Analog-to-Digital Converter (ADC) to sample the incoming ECG signal.

Real-Time Visualization: The microcontroller transmits the ADC data to a connected computer, where a custom Python script uses pyplot (Matplotlib) to graph the live heartbeat waveform.

📈 Live ECG Output
![Pyplot Real-Time Graph](path/to/pyplot_graph.png)

Team & Contributions
This project was a highly collaborative effort. While all team members contributed heavily to the initial hardware simulation and overall system design, we divided key implementation phases to optimize our workflow:

Danyal: Led the hardware assembly, physical prototyping, system debugging, and contributed to LTspice simulations.

Henry Stenzel: Partnered on hardware assembly, physical prototyping, system debugging, and contributed to LTspice simulations.

Danny Kaddoura: Designed the custom PCB layout using Altium Design Suite and contributed to LTspice simulations.

Sam Zilmer: Focused on the core system architecture and LTspice hardware simulations.

Technologies Used
Hardware Components: INA333 (Instrumentation Amp), OPA333 (Op-Amps), PIC24 Microcontroller

Software/Tools: LTspice, Altium Designer, MPLAB X IDE, Python (matplotlib.pyplot)

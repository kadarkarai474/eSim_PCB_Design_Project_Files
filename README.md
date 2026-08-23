# STM32BASE — Custom STM32F103C8T6 USB Development and Multi-Interface Controller Board

## 1. Project Title

**STM32BASE: Custom STM32F103C8T6 USB Development and Multi-Interface Controller Board**

## 2. Project Abstract

STM32BASE is a compact, custom-designed STM32 microcontroller development and embedded-control board developed as a reusable hardware platform for embedded systems, IoT, robotics, instrumentation, and digital control applications. The board is centered around the **STM32F103C8T6 ARM Cortex-M3 microcontroller** and integrates regulated 3.3 V power, USB connectivity, UART communication, I²C expansion, SWD programming/debugging, boot-mode selection, external clock generation, status indication, and dedicated decoupling/filtering.

The proposed design converts the functionality normally distributed across a commercial STM32 development board, USB-to-serial interface board, and separate programming/debugging headers into a single custom PCB. The STM32F103 family provides high-performance processing with operation up to 72 MHz and peripherals including USB, USART, SPI, I²C, ADC, timers/PWM and CAN, making the platform suitable for extending the present design with additional communication and control interfaces.

The PCB is designed with attention to component placement, power distribution, short high-speed signal paths, grounding, decoupling, footprint selection, routing quality, and manufacturability. The current implementation is a **two-layer PCB**, satisfying the FOSSEE eSim PCB Design requirement of at least two copper layers; a future four-layer revision could further improve power/ground integrity and may receive additional consideration under the current Autumn 2026 evaluation criteria.

## 3. Problem Statement

Commercial STM32 development boards are convenient for prototyping but often contain unnecessary circuitry, limited connector options, and a fixed board architecture. For embedded development and PCB-design education, there is a need for a compact custom controller board that exposes essential MCU interfaces while demonstrating the complete engineering workflow from schematic capture to PCB layout, routing, DRC verification, and 3D visualization.

**STM32BASE addresses this requirement by providing a reusable custom STM32 platform with integrated programming, communication, power, clock, boot and expansion interfaces on a single PCB.**

## 4. Main Objectives

1. Design a functional custom STM32F103C8T6-based controller PCB.
2. Implement a stable **5 V to 3.3 V regulated power architecture**.
3. Provide direct USB connectivity for power and USB communication.
4. Provide dedicated UART, I²C and SWD connectors.
5. Implement a reliable external clock using an 8 MHz crystal.
6. Provide BOOT-mode selection for firmware programming and recovery.
7. Implement proper MCU decoupling and filtered power distribution.
8. Demonstrate practical PCB layout and routing techniques.
9. Perform electrical and design-rule verification before fabrication.
10. Develop the complete project using the eSim-compatible PCB workflow required by FOSSEE.

## 5. Functional Block Description

**USB / 5 V Input → Power Regulation → 3.3 V Digital Supply → STM32F103C8T6**

The MCU provides the central processing function and connects to:

**USB Interface → USB D+/D−**

**UART Header → Serial Communication**

**I²C Header → Sensor/Peripheral Expansion**

**SWD Header → Programming and Debugging**

**BOOT Selector → Firmware Boot Configuration**

**8 MHz Crystal → External Clock Reference**

**LED → Power/Status Indication**

## 6. Key Design Parameters

| Parameter                  | Proposed Design                                     |
| -------------------------- | --------------------------------------------------- |
| Project Name               | STM32BASE                                           |
| MCU                        | STM32F103C8T6                                       |
| MCU Architecture           | ARM Cortex-M3                                       |
| Maximum MCU Clock          | Up to 72 MHz for STM32F103 performance-line devices |
| MCU Supply                 | 3.3 V nominal                                       |
| MCU Supply Range           | STM32F103 family: 2.0–3.6 V                         |
| Input Supply               | 5 V from USB                                        |
| Voltage Regulator          | AMS1117-3.3                                         |
| Regulated Output           | 3.3 V                                               |
| External Crystal           | 8 MHz                                               |
| USB                        | USB 2.0 Full-Speed device interface                 |
| Programming                | SWD                                                 |
| Serial Interface           | UART                                                |
| Sensor/Expansion Interface | I²C                                                 |
| Boot Configuration         | BOOT selector                                       |
| PCB Layers                 | 2-layer current design                              |
| Future PCB Option          | 4-layer revision                                    |
| Board Type                 | Custom STM32 development/controller board           |
| PCB Technology             | SMD + through-hole connectors                       |
| Mounting                   | Four PCB mounting holes                             |
| Status Indication          | LED indicator                                       |
| Debug Interface            | SWD header                                          |
| Expansion                  | UART and I²C headers                                |
| Primary Application        | Embedded control and rapid prototyping              |

## 7. Major Components Required

| Ref.    | Component          | Typical Value / Part        | Quantity | Function                     |
| ------- | ------------------ | --------------------------- | -------: | ---------------------------- |
| U2      | Microcontroller    | STM32F103C8T6               |        1 | Main processing/control unit |
| U1      | LDO Regulator      | AMS1117-3.3                 |        1 | 5 V to 3.3 V regulation      |
| J1      | USB Connector      | Micro-USB                   |        1 | Power and USB data           |
| J2      | UART Header        | 1×4 header                  |        1 | UART TX/RX and power         |
| J3      | I²C Header         | 1×4 header                  |        1 | I²C SDA/SCL and power        |
| J4      | SWD Header         | 1×4 header                  |        1 | Programming/debugging        |
| Y1      | Crystal            | 8 MHz                       |        1 | External MCU clock           |
| S1      | Boot Switch        | SPDT                        |        1 | Boot-mode selection          |
| FB1     | Ferrite Bead       | Power filtering type        |        1 | Supply-noise isolation       |
| D1      | LED                | 3.3 V status/power LED      |        1 | Visual indication            |
| R1      | LED Resistor       | 1.5 kΩ                      |        1 | LED current limiting         |
| R2      | BOOT Resistor      | 10 kΩ                       |        1 | BOOT0 biasing                |
| R3      | USB Resistor       | 1 kΩ class                  |        1 | USB interface support        |
| R4      | I²C Pull-up        | 4.7 kΩ                      |        1 | SDA pull-up                  |
| R5      | I²C Pull-up        | 4.7 kΩ                      |        1 | SCL pull-up                  |
| C1/C2   | Bulk Capacitors    | 10–22 µF class              |        2 | Supply stabilization         |
| C3–C11  | Ceramic Decoupling | 100 nF / 1 µF / 10 µF class |  Several | MCU and supply decoupling    |
| C12/C13 | Crystal Capacitors | ~10–20 pF class             |        2 | Crystal load capacitors      |
| H1–H4   | Mounting Hardware  | PCB mounting holes          |        4 | Mechanical mounting          |

**Note:** The final BOM should exactly match the verified eSim schematic values before submission. Values such as the USB support resistor and capacitor values should be checked against the final schematic/netlist rather than copied only from the PCB screenshot.

## 8. Interface Specification

| Interface | Connector                | Purpose               | Application                            |
| --------- | ------------------------ | --------------------- | -------------------------------------- |
| USB       | Micro-USB                | Power + USB data      | PC communication / firmware tools      |
| UART      | 1×4 header               | Serial TX/RX          | Debugging, GPS, GSM, Bluetooth modules |
| I²C       | 1×4 header               | SDA/SCL               | Sensors, displays, EEPROMs             |
| SWD       | 1×4 header               | Programming/debugging | STM32 programmer/debugger              |
| BOOT      | SPDT switch              | Boot configuration    | Firmware recovery/programming          |
| GPIO      | MCU expansion capability | Digital control       | LEDs, relays, sensors                  |
| ADC       | MCU internal             | Analog measurement    | Sensors/potentiometers                 |
| PWM       | MCU timers               | Actuator control      | Motors, LEDs, servos                   |

The STM32F103 family natively supports USB, USART, SPI, I²C, ADC, timers/PWM and CAN, providing a strong path for expanding this base platform into a more capable universal controller.

## 9. Power-Supply Architecture

The power section accepts **5 V from the USB connector** and generates a regulated **3.3 V rail** using an AMS1117-3.3 regulator.

| Stage            | Component          | Voltage | Purpose                       |
| ---------------- | ------------------ | ------: | ----------------------------- |
| Input            | USB VBUS           |     5 V | External power source         |
| Filtering        | C1/C2 + FB1        |     5 V | Reduce supply disturbances    |
| Regulation       | AMS1117-3.3        |   3.3 V | MCU supply generation         |
| Local Decoupling | Ceramic capacitors |   3.3 V | Suppress high-frequency noise |
| MCU Supply       | STM32F103C8T6      |   3.3 V | Core and I/O supply           |

The regulated 3.3 V supply is appropriate for the STM32F103 family, whose specified supply range is 2.0–3.6 V.

## 10. Clock and Reset Architecture

The design includes an **8 MHz external crystal oscillator** with dedicated load capacitors connected to the STM32 oscillator pins. The MCU can use its internal PLL to derive the required system clock from the external clock source.

The clock section is intentionally placed close to the MCU to reduce unnecessary trace length and susceptibility to noise.

The design also includes the required boot-selection circuitry, allowing the user to select normal firmware execution or the appropriate boot/programming mode.

## 11. PCB Design Features

The PCB layout shown in the design incorporates:

* Dedicated MCU placement near the center of the board.
* Compact placement of crystal and oscillator capacitors near the MCU.
* Dedicated USB connector at the board edge.
* Separate SWD and UART headers for convenient debugging.
* I²C expansion connector for external peripherals.
* Local decoupling capacitors surrounding the MCU.
* Separate power-regulation section.
* Ferrite filtering for supply-noise isolation.
* Clearly identifiable component reference designators.
* Four mechanical mounting holes.
* Ground and power routing designed around the major functional blocks.

## 12. PCB Routing Strategy

| Design Area           | Routing Strategy                                       |
| --------------------- | ------------------------------------------------------ |
| 3.3 V Power           | Short, low-resistance power paths                      |
| MCU Decoupling        | Capacitors placed as close as practical to supply pins |
| Crystal               | Very short oscillator connections                      |
| USB                   | Short and symmetric D+/D− routing                      |
| SWD                   | Direct routing between MCU and debug header            |
| UART                  | Direct low-speed signal routing                        |
| I²C                   | Pull-up resistors located on the interface section     |
| Ground                | Continuous/low-impedance ground strategy               |
| USB Entry             | Connector positioned at PCB edge                       |
| High-activity Signals | Kept away from sensitive clock section                 |
| Mechanical            | Components kept clear of mounting-hole regions         |

## 13. Important PCB Design Parameters

| Parameter                  | Design Target                                    |
| -------------------------- | ------------------------------------------------ |
| PCB Layer Count            | 2 layers                                         |
| Recommended Future Version | 4 layers                                         |
| Board Shape                | Compact rectangular                              |
| Mounting Holes             | 4                                                |
| Main PCB Material          | FR-4                                             |
| Copper                     | Standard PCB copper                              |
| Component Technology       | Predominantly SMD                                |
| Connectors                 | Through-hole/SMD depending on selected footprint |
| Ground Strategy            | Dedicated ground routing/pour                    |
| DRC                        | Zero critical errors targeted                    |
| Routing                    | Complete connectivity                            |
| Silkscreen                 | Component identification and interface labels    |
| 3D Verification            | Required                                         |
| Footprint Verification     | Required                                         |
| Manufacturing Readiness    | Required                                         |

## 14. Design Complexity

The project is more than a basic microcontroller breakout because it combines multiple hardware subsystems on a single custom PCB:

| Subsystem                         | Complexity |
| --------------------------------- | ---------- |
| STM32 MCU integration             | Medium     |
| USB interface                     | Medium     |
| 3.3 V power supply                | Medium     |
| External clock                    | Medium     |
| BOOT configuration                | Low–Medium |
| SWD programming                   | Low        |
| UART expansion                    | Low        |
| I²C expansion                     | Low        |
| Power filtering                   | Medium     |
| High-density MCU routing          | High       |
| Compact PCB placement             | High       |
| DRC and manufacturability         | High       |
| Complete eSim → PCB → 3D workflow | High       |

This makes STM32BASE a **medium-to-hard complexity PCB project**, while remaining realistic to fabricate and demonstrate.

## 15. Advantages of the Proposed Design

1. **Custom rather than module-based:** The STM32 MCU is directly placed on the PCB instead of using a prebuilt development module.
2. **Integrated programming:** SWD is available directly on the board.
3. **USB-enabled:** A dedicated USB connector removes the need for an external USB interface board.
4. **Multiple communication interfaces:** UART and I²C are directly accessible.
5. **Dedicated power architecture:** USB input and regulated 3.3 V distribution are integrated.
6. **Expandable:** Unused STM32 peripherals can be exposed in future revisions.
7. **Educational value:** Demonstrates schematic design, footprint selection, power design, PCB placement, routing, DRC and 3D verification.
8. **Reusable platform:** The board can become the base controller for robotics, sensor nodes, automation systems and IoT prototypes.

## 16. Suggested Future Enhancements

To make a future revision more advanced and competitive, the following can be added:

| Enhancement                 | Benefit                                             |
| --------------------------- | --------------------------------------------------- |
| CAN transceiver             | Automotive/industrial communication                 |
| SPI header                  | High-speed peripheral expansion                     |
| Additional GPIO headers     | External module integration                         |
| ADC expansion header        | Analog sensor interfacing                           |
| PWM header                  | Motor/servo control                                 |
| 5 V output                  | External module power                               |
| ESD protection on USB       | Improved robustness                                 |
| Reverse-polarity protection | Safer external power                                |
| Reset/user push button      | Improved user interaction                           |
| Additional status LEDs      | Easier debugging                                    |
| USB ESD protection          | Better USB reliability                              |
| 4-layer PCB                 | Improved power/ground integrity and routing density |
| Dedicated ground plane      | Better return-current control                       |
| Test points                 | Easier laboratory debugging                         |

## 17. FOSSEE eSim PCB Design Relevance

This project directly demonstrates the workflow expected for the current FOSSEE eSim PCB Design task: schematic development, footprint assignment, PCB generation, routing, DRC verification and 3D visualization. The Autumn 2026 task specifies a minimum of two copper layers and notes that boards with a higher layer count may receive additional consideration. It also evaluates design complexity, footprint assignment, layout quality, routing practices, DRC validation, eSim compatibility and documentation quality.

The final submission should therefore document the complete design flow rather than presenting only the finished PCB.

## 18. Expected Deliverables

| Deliverable       | Contents                                      |
| ----------------- | --------------------------------------------- |
| Schematic         | Complete STM32BASE circuit                    |
| PCB               | Routed PCB layout                             |
| Project Files     | Complete eSim/KiCad-compatible project        |
| BOM               | Components, values, quantities and footprints |
| Schematic Images  | Annotated circuit diagrams                    |
| PCB Images        | Top/bottom/layout views                       |
| 3D Images         | Final PCB 3D visualization                    |
| DRC Report        | Verification and corrected errors             |
| Design Report     | Architecture, design decisions and results    |
| Execution Guide   | Steps to open and verify the project          |
| GitHub Repository | Organized project source and documentation    |

FOSSEE's current Autumn 2026 PCB-design instructions specifically require a detailed PDF report, complete eSim project workspace, instructions for opening/verifying the project, and optionally a short presentation or demonstration.

## 19. Proposed Applications

STM32BASE can be used as the central controller for:

* IoT sensor nodes
* Industrial monitoring
* Robotics controllers
* Motor-control prototypes
* Environmental monitoring
* Data acquisition systems
* Smart automation
* Embedded instrumentation
* Communication gateways
* Educational STM32 development
* Custom sensor and actuator platforms

## 20. Conclusion

**STM32BASE is a compact custom STM32 development and controller platform that integrates the essential hardware required for embedded development into a single PCB.** The design combines a regulated 3.3 V power system, STM32F103C8T6 microcontroller, USB connectivity, UART, I²C, SWD programming, external clock, BOOT control, filtering, status indication and mechanical mounting into one reusable board.

The project provides substantial PCB-design content while remaining technically manageable: the evaluator can clearly observe the schematic architecture, power design, footprint selection, dense MCU routing, interface placement, DRC verification and final 3D implementation. It is therefore a strong candidate for an eSim/FOSSEE PCB Design submission, with a clear path toward a more advanced four-layer revision incorporating CAN, SPI, additional GPIO/PWM/ADC expansion and improved protection circuitry.

### Recommended Final Project Name

**STM32BASE – Custom STM32F103C8T6 USB Multi-Interface Development and Control Board**

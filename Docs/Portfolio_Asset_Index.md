# Portfolio Asset Index

This index lists the verified public schematic and plot images for each project, with short captions suitable for a portfolio gallery. Each image was checked against its trace labels, axes, and the source `.asc` file. All figures are LTspice simulation captures, not hardware measurements.

The locally archived reciprocal-gain amplifier plot and the generated Monte Carlo `.log.raw` data are excluded from this index on purpose.

## Contents

- [Closed-Loop Buck Converter](#closed-loop-buck-converter)
- [Three-Phase Full-Bridge Inverter](#three-phase-full-bridge-inverter)
- [Instrumentation Amplifier](#instrumentation-amplifier)
- [Monte Carlo RC Band-Pass Filter](#monte-carlo-rc-band-pass-filter)
- [Diode Ring Mixer](#diode-ring-mixer)
- [Summary](#summary)

## Closed-Loop Buck Converter

| Asset | Relative File Link | What It Demonstrates | Recommended Use |
| --- | --- | --- | --- |
| Startup and load-step response | [Plot](../Closed_Loop_Buck_Converter/Docs/Images/Plots/Closed_Loop_Buck_Converter_Plot_Transient_Output_And_Switching_Node_Voltages_And_Load_And_Inductor_Currents_Startup_And_Load_Step_Response.png) | Simulated output overshoot and settling near 10 V, and regulation through a 1 Ω to 2 Ω load step, with load and inductor currents | **Lead visual** |
| Switching-node zoom | [Plot](../Closed_Loop_Buck_Converter/Docs/Images/Plots/Closed_Loop_Buck_Converter_Plot_Transient_Switching_Node_Voltage_Steady_State_Switching_Cycle_Zoom.png) | Steady-state 100 kHz switching-node waveform, about 50% duty, with diode conduction below 0 V | Supporting |
| Schematic | [Schematic](../Closed_Loop_Buck_Converter/Docs/Images/Schematics/Closed_Loop_Buck_Converter_Schematic.png) | Power stage, PI feedback, duty limiter, and behavioral PWM | Supporting |

## Three-Phase Full-Bridge Inverter

| Asset | Relative File Link | What It Demonstrates | Recommended Use |
| --- | --- | --- | --- |
| Star-load phase currents | [Plot](../Three_Phase_Full_Bridge_Inverter/Docs/Images/Plots/Three_Phase_Full_Bridge_Inverter_Plot_Transient_Star_Connected_Load_Phase_Currents_Startup_And_Steady_State_Response.png) | Simulated balanced 160 Hz star-branch currents settling to about ±15 A after a decaying startup offset | **Lead visual** |
| Phase-to-neutral voltages | [Plot](../Three_Phase_Full_Bridge_Inverter/Docs/Images/Plots/Three_Phase_Full_Bridge_Inverter_Plot_Transient_Three_Phase_To_Neutral_Voltages_PWM_Switching_Interval_Zoom.png) | PWM phase voltages at 0, ±Vdc/3, and ±2Vdc/3 over a 0.5 ms switching interval | Supporting |
| Line-to-line voltage | [Plot](../Three_Phase_Full_Bridge_Inverter/Docs/Images/Plots/Three_Phase_Full_Bridge_Inverter_Plot_Transient_Phase_A_To_Phase_B_Line_To_Line_Voltage_Switching_Interval_Zoom.png) | V(A,B) pulses spanning the full 380 V bus in a switching interval | Supporting |
| Phase B PWM controls | [Plot](../Three_Phase_Full_Bridge_Inverter/Docs/Images/Plots/Three_Phase_Full_Bridge_Inverter_Plot_Transient_Phase_B_Upper_And_Lower_PWM_Control_Voltages_Complementary_Switching_Zoom.png) | Ideal complementary 0/1 V switch controls without dead time | Supporting |
| Schematic | [Schematic](../Three_Phase_Full_Bridge_Inverter/Docs/Images/Schematics/Three_Phase_Full_Bridge_Inverter_Schematic.png) | DC link, three legs, star and delta loads, and sinusoidal PWM sources | Supporting |

## Instrumentation Amplifier

| Asset | Relative File Link | What It Demonstrates | Recommended Use |
| --- | --- | --- | --- |
| Differential input and output | [Plot](../Instrumentation_Amplifier/Docs/Images/Plots/Instrumentation_Amplifier_Plot_Transient_Differential_Input_And_Output_Voltages_1_Kilohertz_Signal_Response.png) | 100 mV-peak 1 kHz input amplified to about 200 mV peak, consistent with the ideal gain of 2 | **Lead visual** |
| Common-mode test | [Plot](../Instrumentation_Amplifier/Docs/Images/Plots/Instrumentation_Amplifier_Plot_Transient_Output_Voltage_Common_Mode_Rejection_Test.png) | About ±0.6 µV output residual for a 1 V-peak drive in an idealized, matched-resistor model | Supporting |
| Noise spectral density | [Plot](../Instrumentation_Amplifier/Docs/Images/Plots/Instrumentation_Amplifier_Plot_Noise_Input_And_Output_Referred_Voltage_Noise_Densities_Frequency_Response.png) | Output- and input-referred voltage-noise densities (nV/√Hz), 1 Hz-1 MHz | Supporting |
| Schematic | [Schematic](../Instrumentation_Amplifier/Docs/Images/Schematics/Instrumentation_Amplifier_Schematic.png) | Three-LT1007 topology with gain resistor and difference stage | Supporting |

No forward-gain frequency-response plot is available for this project.

## Monte Carlo RC Band-Pass Filter

| Asset | Relative File Link | What It Demonstrates | Recommended Use |
| --- | --- | --- | --- |
| 500-run frequency response | [Plot](../Monte_Carlo_RC_Band_Pass_Filter/Docs/Images/Plots/Monte_Carlo_RC_Band_Pass_Filter_Plot_AC_Output_Gain_And_Phase_500_Run_Monte_Carlo_Frequency_Response.png) | Overlaid gain and phase showing the spread caused by ±10% resistor and ±20% capacitor tolerances | **Lead visual** |
| Peak gain vs. run | [Plot](../Monte_Carlo_RC_Band_Pass_Filter/Docs/Images/Plots/Monte_Carlo_RC_Band_Pass_Filter_Plot_Monte_Carlo_Peak_Gain_In_Decibels_Versus_Simulation_Run.png) | Per-run measured peak gain, about −7.4 dB to −5.6 dB | Supporting |
| Center frequency vs. run | [Plot](../Monte_Carlo_RC_Band_Pass_Filter/Docs/Images/Plots/Monte_Carlo_RC_Band_Pass_Filter_Plot_Monte_Carlo_Center_Frequency_In_Hertz_Versus_Simulation_Run.png) | Per-run measured center frequency, about 4.1 Hz to 6.4 Hz | Supporting |
| Schematic | [Schematic](../Monte_Carlo_RC_Band_Pass_Filter/Docs/Images/Schematics/Monte_Carlo_RC_Band_Pass_Filter_Schematic.png) | Filter, `mc()` tolerances, step and measurement directives, and K6JCA credit | Supporting |

## Diode Ring Mixer

| Asset | Relative File Link | What It Demonstrates | Recommended Use |
| --- | --- | --- | --- |
| Output spectrum, 0-40 MHz | [Plot](../Diode_Ring_Mixer/Docs/Images/Plots/Diode_Ring_Mixer_Plot_FFT_Output_Voltage_Spectrum_0_To_40_Megahertz.png) | Dominant 3 MHz difference and 17 MHz sum products, with third-order products at 11, 23, 31, and 37 MHz | **Lead visual** |
| Output spectrum, 0-100 MHz | [Plot](../Diode_Ring_Mixer/Docs/Images/Plots/Diode_Ring_Mixer_Plot_FFT_Output_Voltage_Spectrum_0_To_100_Megahertz.png) | Wideband view of higher-order mixing products | Supporting |
| Mixer output waveform | [Plot](../Diode_Ring_Mixer/Docs/Images/Plots/Diode_Ring_Mixer_Plot_Transient_Mixed_Output_Voltage_Time_Domain_Waveform.png) | Time-domain mixed output, about ±6.6 V peak | Supporting |
| LO input | [Plot](../Diode_Ring_Mixer/Docs/Images/Plots/Diode_Ring_Mixer_Plot_Transient_Local_Oscillator_Input_Voltage_7_Megahertz_Waveform.png) | 7 MHz LO excitation | Supporting |
| RF input | [Plot](../Diode_Ring_Mixer/Docs/Images/Plots/Diode_Ring_Mixer_Plot_Transient_RF_Input_Voltage_10_Megahertz_Waveform.png) | 10 MHz RF excitation | Supporting |
| Schematic | [Schematic](../Diode_Ring_Mixer/Docs/Images/Schematics/Diode_Ring_Mixer_Schematic.png) | LO and RF transformers, four-diode ring, and output center tap | Supporting |

## Summary

| Category | Count |
| --- | --- |
| Public schematic images | 5 |
| Public plot images | 17 |
| Excluded plots (local archive only) | 1 |
| Generated data files (local archive only) | 1 |

java c
EEET2386/EEET2387
Switched Mode Power Supplies
Laboratory 3: Peak current regulated converter
1. Aims
Learn to use a detailed PSIM™  simulation to finalise the design of a practical flyback converter that incorporates inner Peak Current Regulation.
Determine values  for the undefined  components  of the  converter  as  identified in the parameter definition file “flyback_lab3.txt” .
Learn how to  control  a  substantial  PSIM™   simulation  to  maximise  the  efficiency  of execution in terms of program “Time Step”, “Total Time”, “Load Flag” and “ Save Flag” functions.
Explore the operation of the flyback converter over a range of loads and input operating conditions and fine-tune the transformer design and feedback controller as required to achieve satisfactory operation over the entire design range.
2. EquipmentAltair®  PSIM™   simulation package, available via EEET2387 Canvas  shell (Combined EEET2386  (UG  -  undergraduate)  +  EEET2387  (PG  -  postgraduate)  Canvas  shell)  for installation on personal computers running Microsoft Windows 7 or 10 or 11. Please note that if the version of PSIM™  on RMIT’s myDesktop does not match the PSIM™  Student Version you use, you will need to save a copy of your work in a format supported by the older version.
3. Software
The following software tools can be utilised to assist and validate circuit operation through simulation:
Altair® PSIM™ simulation package. Student version download instructions are available on the EEET2387 Canvas shell.
MathWorks MATLAB/GNU Octave/Python/Wolfram Alpha can be used to aid calculation and analysis.
4. IntroductionAltair®  PSIM™  is an “idealised” simulation tool that uses “perfect” components such as  inductors, switches, transistors, etc. Its primary use is for design in principle investigations that  explore the fundamental operations of various switching circuits. However, while PSIM™  is  not so suitable for an in-depth design of electronic circuits, since it does not provide “realistic” models  of electronic  components,  it  can  also  be  used  for  such  investigations  by  adding  additional circuit elements to present the second order parasitic effects of real components.  PSIM™  is a very powerful simulation tool, and you should use this experiment to explore its  features.
5.  Things to watch out for
Always remember to place an earth on the desired reference point for each isolated section of the circuit. The earth is required to provide a measurement reference for all voltage measurements – without this reference, the simulation results are usually rubbish.
The first millisecond or so of a simulation will often be influenced by initial condition/start- up effects, which are generally not of particular interest. While you can minimise the initial condition effects by setting initial inductor currents and capacitor voltages as part of the component specification, for this experiment it is probably easier to set the “Print Time” in the “Simulation Control” window to a value that only commences recording results after the initial condition response has died down.
You  need  to  be  careful  with  the  simulation  time  step  setting  –  “Time  Step”  in  the “ Simulation Control” window. Too large a time step will give an inaccurate simulation response that can be quite erroneous. Too small a time step will create excessively long simulation times to execute. One strategy is to keep reducing the time step until the response you get does not change with the time step size. This is then the maximum possible time step size for the circuit you are investigating. However, remember that things can change as a simulation study progresses, so keep checking the time step size as your work proceeds.
Do not make the simulation period – “Total Time” in the “ Simulation Control” window – longer than necessary to explore the effect you are investigating. A longer simulation period just takes longer to execute, without providing any additional knowledge.
Use a “Parameter File” to define all component values. This allows you to keep much better control over all simulation variables, and also allows arithmetic operations to be used to calculate dependant variables from primary component values when required.
Remember to set the “Current Flag” for series components such as Inductors and Diodes, for which you wish to record their current waveform.
6. EEET2386 (UG) and EEET2387 (PG) AssessmentTo complete the investigations required for this laboratory, you may need to do additional simulation work in your private study time. This can be done using the PSIM™ Student version (download instructions are available on the EEET2387 Canvas shell) on your own personal computer or using Altair®  PSIM™  available via RMIT’s myDesktop. Just remember to save your simulation files on suitable media (memory stick, cloud, personal storage system) before logging off your computer.
This laboratory assignment is assessed in two ways:
Through a group (maximum 2 students per group) written laboratory report that is to be submitted within two weeks of your scheduled laboratory session (i.e., before your next scheduled laboratory). Late reports will be marked for a pass only (50% maximum mark). Your report  is  limited  to  6  pages  only,  including  the  report  title,  student  name  and laboratory date (but excluding the official front page cover sheet required by the school). Any pages beyond this 6-page limit will not be marked. NOTE: An additional 1 page for the report will be accepted ONLY to present results for the more advanced work of Section
13. The advanced work of Section 13 is optional for students enrolled in EEET2386 (UG) (up to 1 mark available for successful completion and inclusion of advanced work in the report) and compulsory for all students enrolled in EEET2387 (PG).
Through a short laboratory demonstration that is to be conducted during the first hour of your  scheduled  Laboratory  4  session.  Your  laboratory  demonstration  should  be  a succinct demonstration of your simulation and results in PSIM™ . It should demonstrate the main functional parts of your simulation and should supplement your laboratory report. Your demonstration may include your preparation  and participation in the laboratory assignment during your session. You will be required to upload your Altair®  PSIM™  .psimsch and parameter.txt files to Canvas after your laboratory class.
This laboratory assignment has the following criteria:
Attendance  of  your  Laboratory  session  is  mandatory  as  all  laboratory  classes  are assessments. If you miss your laboratory  session, you will need to apply for  Special Consideration. Non-attendance of your laboratory session will result in a zero (0/20) score for the associated laboratory assignment.
You are allowed to work on your Laboratory individually or in groups of up to two students maximum per group. If you work in  a group of two, you may  choose which individual parameter the group will use. It must be one of the two parameters assigned to the group members. When working in a group, only one written group laboratory report and one group demonstration needs to be conducted.
Your laboratory report should include a brief introduction, a short description of the circuits  investigated,  simulation  results,  a  discussion  of the  simulation  outcomes  that includes consideration of the issues raised in these laboratory notes, and a conclusion summarising your observations. It is not required or acceptable to replicate significant sections of these laboratory notes in your report. Laboratory reports will not be accepted if the corresponding session was not attended.
Your demonstration should include a succinct demonstration of your simulation in PSIM™ with resulting waveforms of important measurements as per the laboratory assignment. This  opportunity  should  be  used  to  demonstrate  the  main  functional  parts  of  your simulation and should supplement your laboratory report.
Demonstration HINTS: Use Altair® Simview’s “Options”⇨”Save Settings” to save your simulation screen layout and settings.
Refer to the laboratory  assignment marking rubric  (report  and  demonstration)  on the EEET2387 Canvas shell for more details regarding the marking scheme and standards of performance employed for this assignment. Ensure that you understand the rubric. Please ask if you are unsure.
The teaching team is available during our weekly Lectorials (Refer to the EEET2387 Canvas shell for announcements) to answer your questions and queries.
7. Converter DescriptionThe file “Lab3_smps_flyback_2024.psimsch” provided for this laboratory is a detailed simulation  of  a  physical   flyback  converter  (the  physical  converter  operation  will  be demonstrated in Lab #5). The simulation includes all major components of the actual converter, arranged, and labelled to match the circuit of the real  converter. It includes all secondary components that are typically required for this type of system, including snubber circuits, additional output LC filters, start-up management circuitry, gate drive circuitry, etc. Also note the various test point voltage measurements included in the simulation (TPxx) which reflect actual  test  point  connections  on  the  physical  converter.  You  should  use  these  voltage measurements to investigate your circuit operation in the first instance.The UCC2804 PWM controller for the converter is simulated as a sub-circuit, with the major  sections  of this chip  simulated using  equivalent  circuit  elements that replicate the operation of these sections. Note that the UCC2804 representation is not fully complete, with some of the start-up and protection circuitry not included. Note also how the error amplifier of the controller has been represented by a summing junction, followed by a gain stage with a dominant pole role off characteristic, and an output voltage limiter circuit that constrains the amplifier output voltage to within the supply rails. The parameters of this model have been set to match the gain-bandwidth specifications of the error amplifier of the UCC2804.Due to PSIM™  limitations, some parts of the simulation circuit (primarily the MOSFET switch) do not precisely match their represented real components. For example, the main switching  MOSFET  is  represented  as  a  gate  voltage  feeding  into  a  threshold  voltage comparator, whose output drives through a switch controller into the idealised FET switch. This of course does not precisely replicate the switching process of an actual MOSFET, but it is quite sufficient for this level of converter representation. Similarly, the gain stage “K” in the gate drive circuit is used to represent the operation of a totem pole BJT current gain stage, since
PSIM™  does not support adequate BJT models. However, overall, the simulation response is anticipated to almost exactly match the operation of the real converter.The specifications of the flyback converter are listed below. Essentially it accepts a nominal 28V voltage input and has to create two output voltages – one at 15V and one at 5V. A third auxiliary 10V 代 写EEET2386/EEET2387 Switched Mode Power Supplies Laboratory 3: Peak current regulated converterPython
代做程序编程语言output is used to power the UCC2804 controller and provide a feedback voltage for regulation. The circuit starts up with a trickle current feed through R9, until the  10V auxiliary feedback voltage is established and takes over the UCC2804 power supply.The converter design is a standard single switch flyback converter, with outer voltage regulation and an inner peak current limiting controller. The outer voltage regulation maintains the auxiliary voltage at the nominal 10V, and the regulation of the main output voltages is then determined by second-order effects such as transformer leakage inductance, device voltage drop, etc.
8. Optimising Simulation OperationThis flyback converter simulation is quite complex and can take some time to execute. Hence you will need to keep adjusting the “Simulation Control” clock parameters to maximise your productivity. Techniques can include:
Setting the “Time Step” to a larger value for quick check simulations, and then reducing it to a smaller value for the final run, or for a detailed investigation of a higher frequency switching/oscillation process.
Adjusting the “Total Time” to suit the context. For example, there is no value in simulating for a longer time if the only purpose is to quickly check a switching operation.
Set the initial conditions for capacitor voltages (and inductor currents sometimes) to their anticipated  steady  state  values,  to  avoid  their  start-up  process.  For  example,  setting V15i=15 in the parameter file will pre-set all capacitors on the 15V output to this value. V10i and V5i behave similarly for the other two output voltages.
Setting the  “Save  Flag”  after  a  (long)  initialising  simulation  run.  Then,  for  the  next simulation run, clear the “Save Flag” and set the “Load Flag”, and then make whatever changes you need to the simulation. When you start the simulation, it will initialise all variables to the last value in the previous “Saved” run. This essentially eliminates the time required for the initial start-up process.
Save your SIMVIEW Settings so that you can quickly re-establish a more complicated set of output plots if you wish to come back later to further explore the converter operation.
9. Flyback Converter Specification
A multiple output flyback converter is required with the following specifications:
Nominal Input voltage:                       28V DC
Input Voltage Range:                          20V to 40V DC
Output Voltage #1:                              15V DC, maximum 1A output current
Output Voltage #2:                              5V DC, maximum 1A output current
Auxiliary Output Voltage:                   10V DC, maximum 50mA output current
Switching Frequency:                         fs  kHz
Topology:                                            Single Switch Flyback (FET)
(Individual parameter e.g., fs   to be released via Canvas)
10.Flyback Converter Circuit

Figure 1: Peak Current Regulated Dual Output Flyback Converter.
a) Preliminary – Establish values for unknown componentsThe first step of the laboratory is to define values for the unknown components of the flyback converter shown in Figure 1, so that the converter achieves operation with a nominal 28V input.
The following components need values defined in the parameter file “flyback_lab3.txt”:
// EEET2386/7 Laboratory #3 Parameters // Parameter file excerpt
// Input and Output Operating Conditions
Vin=28// Nominal value – to be varied as part of the lab
RL15=???
// 15V output load resistor
RL5=???
// 5V output load resistor
//Circuit Components

C15=????
// Snubber capacitor
C31=????
// Oscillator capacitor
C34=????
// Feedback Gain #1 capacitor
C35=????
// Feedback Gain #2 capacitor
R3=????
// Current sense resistor
R5=????
// Snubber resistor
R18=????
// Oscillator resistor
R21=????
// Feedback divider resistor #1
R25=????
// Feedback gain resistor
R28=????
// Feedback divider resistor #2
Appropriate values need to be specified for all these unknown components before the simulation will run. Some of these values can be determined by analysis and calculation. Others will need some trial and error to fine-tune. For these, an initial “reasonable” value should be used as a starting point, and then adjusted based on how the converter circuit responds.
b) Oscillator componentsFrom Figure 8-3 in the UCC2804 data sheet [1], select values for R18 and C31 for an oscillation frequency of 2fs kHz. Note that this will create a converter switching frequency of fs kHz because of the divide-by-2 function included within the controller chip.
c) Feedback divider resistorsThe nominal feedback voltage at the FB input to the UCC2804 is 2.5V. Hence resistors R21 and R28 must be calculated as a voltage divider to make the regulated auxiliary voltage at TP19 10V when the FB node voltage is 2.5V. Make sure you use “standard” resistor values so that the converter can be physically built, even though this may compromise the accuracy of the voltage regulation.
d) Snubber componentsThe RC snubber components C15 and R5 will need to be precisely set once the simulation is operating. For now, set them to “typical” values of C15=1nF  and R5= 500Ω , to allow the simulation to run.
e) Peak current sense resistorsThe maximum peak current sense voltage for the UCC2804 into pin CS is  1V.  This translates  to  a  maximum  peak  current  given  by  1/R3.  This  value  can  be  approximately calculated by estimating the peak primary current under full load, but for now, it can be set toR3= 0.1Ω . This allows a maximum peak current of 10A, which is well beyond what the converter will actually require. However, it allows the simulation to be run without issue for now.
f) Feedback gain componentsThe feedback gain components C34, C35, R25 are the hardest to set, since they depend on the loop gain of the system, and this is unknown. Typical starting values would be C34=C35= 1nF and R25 = 47kΩ .
g) Load resistorsResistors RL15 and RL5 represent the external load attached to the converter. They will have to be varied between minimum and maximum load conditions to explore the operation of the converter. For now, set them to achieve 80% of full load output current for each voltage output.
h) Transformer designThe flyback transformer for this converter has been designed for the boundary between DCM and CCM to occur at 80% output load currents, with a nominal input voltage of 28V. The number of turns required for the various windings have been rounded off from the precise calculation. The leakage inductance for each winding has been estimated to be 1μH , based on previous experience with this type of transformer. Note that the number of turns for the transformer may need to be adjusted to achieve the best possible output over a range of operating conditions, and it is also not clear whether the design basis for determining the magnetising inductance is correct (i.e., it maybe better to design this inductance to achieve the DCM/CCM boundary with the minimum input voltage of 20V). This issue will be explored as part of the later section laboratory investigations.
i) Verify simulation functionalityVerify that you have  correctly  set  values  for  all  unknown  components,  and  that  the simulation runs. The purpose here is not to get a particularly useful output, but rather to just make sure all parameters are correctly set, and the simulation runs without an error.
j)  Report on component valuesYour report on this section of the experiment should list the values you have defined for the unknown components, and briefly outline the calculations and analysis that you used to arrive at these values.
11.Component verification and adjustmentOnce your simulation is running, you need to do several checks to verify the correctness of your component values. Note that these checks are exactly what would be done experimentally if you were testing a real physical converter for the first time.
a)  Basic checks
Verify that the oscillator is running at fs kHz.
Verify the start-up of the UCC2804 reference voltage.
Set the output loads to approximately 50% and verify the switching operation (should be discontinuous).
Set the output loads to 100% and verify the switching operation (should be continuous).
Explore no-load operation, and adjust the minimum load internal resistors R1, R8, R14 as required  to  ensure   satisfactory  no-load  operation   (i.e.,  reasonable  output  voltage regulation).
b) Further checksYou now need to adjust some of the components to more appropriate values. This includes:
Adjust the snubber components to best damp the discontinuous ring. Note that for this check, you must lightly load the converter to operate in DCM and must also enable the parasitic component Cds   (MOSFET drain-source capacitance).
Adjust  the  feedback  components  to  get  a  better  steady  state  and  dynamic  response. Essentially increase R25 as much as possible within reason (<  500kΩ )  and while the response is still stable. C34 and C35 will need to then be trimmed to set the feedback loop breakpoints (poles and zeros) at sensible frequencies, as per the lecture-discussion on feedback control.
Possibly increase R3 to reduce the allowable peak current. At some point, this limitation will cause the converter to lose voltage regulation at larger loads. Try and locate this point and reduce R3 again accordingly.
Confirm that R6 and C29 eliminate the current spike at FET turn-on caused by the parasitic transformer capacitance  Ctx  . Note that you will have to enable  Ctx     and disable  Cds    to explore this effect. Adjust R6 and C29 as required to achieve this filtering effect.
This completes the basic commissioning of the flyback converter.
c)  Report on basic operationYour report on this section of the experiment should identify any changes you have made to the various component values, and present sufficient results to show that you have managed to get a correctly operating simulation under a few operating conditions.
12.Simulation investigation of converter designOnce your simulation is running effectively, you need to explore the converter operation over a range of operating conditions. Essentially, you are trying to validate the design in terms of regulation of the two major output voltages (15V and 5V) as the input voltage varies between 20V and 40V, for maximum and minimum loads on both outputs. A good approach would be to measure the output voltages for a range of input voltage variations and load changes and plot the variation in these voltages using Excel/MathWorks MATLAB/GNU Octave/Python. Note  that  in  effect,  you  are  using  the  simulation  as  if  it  is  a  real  converter  for  these investigations, under the assumption that the simulation is an accurate representation of reality (to be confirmed in a later experiment).
Your report for this section should present sufficient results to describe the converter performance over the required input voltage range, with various output load conditions.

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com

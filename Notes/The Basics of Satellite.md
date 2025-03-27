[[Information Page.canvas|Information Page]]
## Real simulation of satellite deployment!
https://www.youtube.com/watch?v=RLw3veKBqo0

![[Artist's_concept_of_NISAR_over_Earth.jpg]]

## Satellite has two parts
1. Payload and the bus
2. Payload is the equipment used to carry out the scientific research
The bus is the the body of the satellite used to facilitate the functions for the payload.

## The 7 common satellite sub systems
1. Mechanical system
2. Thermal system
3. Electrical  Power System
4. Attitude determination and Control System
5. Propulsion System
6. communications
7. On Board Computer

[[Satellite Testing]]
### 1. Mechanical Subsystem
Further details @[[Mechanical]]
- Need to be strong and stiff
		- Materials like aluminium alloys or carbon fibres
		- Honey comb composite panels provide surface for mounting equipment's
		- Critical criteria for selecting materials is outgassing as vacuum of space causes material to release gases trap within them. Process called bakeout can be used to reduce risk.
### 2. On board computer
- The brain of the satellite which controls and communicates with all the components on the satellite.
		- *Concern*- Exposure to space cosmic radiation=> can lead to system failure. Radiations are relatively low in LEO satellites where as are relatively high in high earth orbits(Van Allen radiation belts). 
		- *Solution*- Use radiation hardened components and shield sensitive parts or layers of thick aluminium. 
	- Also manage the electrical power system on the satellite.
### 3. Electrical power system
Details @[[Electrical Subsystem]]
- 1 sq. m area just about the surface of earth receives about 1.3 KW of power.
 Most modern satellites use multi junction solar cells.
 - While orbiting the earth there are phases where the sun is not seen by solar panels of the satellite. In such scenarios power needs to be supplied by the on board batteries.
	- The electrical power supply is controlled by the onboard electrical power system which in turn is controlled by the on board computer. It monitors the batteries charge level, charges when required, provides power supply when required.
### 4. Attitude Determination and Control System

#### *Attitude Determination*
 ***Function :***  Used to determine and adjust the satellite relative to a reference frame. The orientation is called as satellite attitude. Adjusting attitude is most crucial immediately after separating from its launch vehicle as it may undergo tumbling and ground station needs to regain control.
#### *Attitude Control*
Satellites use three axis stabilisation an attitude control where actuators are used to precisely control satellite orientation around the three axes
 
***Normal Operation*** : Point the Payload at a certain point on the earth for a specific operation! Point solar panel towards the sun and point the antenna towards the ground station.

***Components*** : Made of sensors and actuators. 
1. *Sensors*: Used for Attitude determination 
	1. Star Tracker Sensor:
	Use to correct error propagation by the IMU. They are operated from every 10 seconds to every 20 minutes. A star tracker uses cameras to capture the image of the sky and uses an algorithm to identify bright stars. Position of the image is compared with a catalogue of bright stars enabling the orientation of the satellite to be determined.
	- *Problem*: Cannot work properly if the camera is pointed towards the sun or satellite spinning too fast relative to the camera shutter speed. Options to accommodating them on the satellite are limited as it needs a clear field of view and can be affected by thermal distortion. 
	2. Sun Sensor: 
	 Sun sensors are simple devices that use photodetector cells to estimate the attitude of the satellite relative to the sun.
	 *Problem*: Don't work during the eclipse portion of an orbit.
	3. Magnetometers:
	 Measure the strength and the direction of the magnetic field surrounding the satellite. 
	 The measurements on sensor is compared with the estimated magnetic field of the earth given the satellites position to estimate its attitude.
	4. Inertial measurement Unit:
	 Contains gyroscope and accelerometers. Provides continuous measure on satellites orientation. 
	 *Problem*: Inference is unreliable due to error propagation which can lead to measurement drifts. *Solution*: Use star tracker to correct the drift
2. *Actuators*: Used for attitude Control based on sensors
	1. Reaction Wheels
		- Consists of a flywheel attached to the motor. Using the motor to change the rotational velocity  of the reaction wheel causes the satellite to rotate about its centre of mass in the opposite direction. A minimum of three wheels mounted on three orthogonal planes gives the satellite full three axis control, allowing minute adjustments to be made to the attitude.
		- *Problem* : After a point of time, the increase in the rotational speed is not possible as it reaches its maximum rotational speed. This is called as saturation and as a result flywheel alone cannot be used for attitude control.
	2. Magnetorquers
		- Magnetorquer are essentially coils wound around the core. When its magnetic field interacts with earths magnetic field a torque is generated. This torque can be used to control the attitude. if actuated at the same time as the flywheel they can be used to slow them down. They are reliable because of no movable parts.
		- *Limitation* : Only suitable for LEO satellites as the magnetic field of earth is strong at these heights. Other option to control the attitude is using the propulsion system.
Further details @[[ADCS]]
### 5. Propulsion System
Used to manipulate satellites orbit. This  could be to move the satellite to a new orbit,  or for station-keeping - corrective manoeuvres performed to maintain an existing orbit. But  it can also be used for attitude control.

Works on the principle by accelerated mass passing through a nozzle.

#### Methods of Propulsion
1. *Cold Gas Propulsion* 
	- Expansion of cold gas through thruster nozzle. Propellant is usually an inert gas like nitrogen or helium. Valves , pressure transducers and pressure regulators are used to monitor system pressure and control the propellant to each of the thrusters.
2. *Chemical Propulsion*
	- Used for generate higher thrust as compared to cold gas propulsion.
	- Two types of chemical propulsions
		1. Mono Propellant System: The propellant is a liquid,  which decomposes into a hot gas when it comes  into contact with a catalyst. The pressurant, an inert gas stored in a separate tank, supplies the pressure that forces the propellant from the  tank to the thrusters.
		2. Bi Propellant System: A bipropellant system uses  two propellants, a fuel and an oxidiser, which  are mixed and ignited in a combustion chamber, producing exhaust gases that are expelled through  the nozzle to generate thrust.
3. *Electric Propulsion* 
	- Uses electrical energy to generate thrust. These  systems work by ionizing a propellant—often a  gas like xenon—and then using electric and  magnetic fields to accelerate the ions to high velocities before expelling them through a  nozzle. The propulsion system is selected based on the thrust requirements and the mass of the  satellite.

***NOTES*** Bipropellant systems are complex but offer high thrust, useful for large satellites.  Monopropellant systems have lower thrust but simpler system design. Electric propulsion has  lower thrust than the chemical propulsion options,  but is very efficient, requiring less propellant.  And cold gas thrusters offer low thrust but very simple design and precise control, making them a good choice for attitude control systems.

### 6. Communication Sub System
- The system which enables the satellite to communicate with the ground station. It is of vital importance as its the only way to communicate. It has two separate capabilities downlink and telemetry. 
#### Downlink
- Downlinking is used to beam the data generated by the satellite to earth. Satellite uses attitude control system to point the downlink antenna towards the ground station, and start transmitting the data. Exact way how its done depends on the satellite- some transmit data once per orbit for each pass over the ground station- some transmit to multiple ground stations while geosynchronous satellites can communicate continuously. 
- ==Transmission of Information happens using electromagnetic waves in RF 1-40 GHz==. 
	 ![[Pasted image 20250224213514.png]]
- The frequency range is spit into different names for convenience.  As the frequency increases the required power increases but the data transmission rate is higher. Higher frequency are more susceptible to degradation by atmospheric attenuation. 
- Data transmitted is a stream of bits. Data needs to be encoded by a carrier wave also called as modulation. Two types of modulation - amplitude,  frequency or phase.
- Modulated signal is generated by the on board transmitter hardware.
- Demodulation takes place at the ground station to obtain the data.
#### Telemetry, Tracking and Command System
- Consists of various switches, filters and antennas.
- 3 Different functions
	- Command Subsystem
		- Allows operations and control team to control the satellite. Commands are transmitted from the ground station, demodulated by TT&C  hardware on the satellite, and then routed to the on-board computer for implementation.
	- Telemetry Subsystem
		- The  Telemetry function transmits housekeeping data  from various sensors on the satellite down to the  ground station, like the temperature of critical  components, the power levels in the batteries, or  propellant levels in the tanks.
	- Tracking subsystem
		- Provides information  about the position and speed of the satellite. The  ground station sends a signal to the satellite,  which the transceiver receives and sends back.  The turnaround time provides an estimate of the  distance between the satellite and the ground station. And the Doppler effect frequency shift provides an estimate of the velocity of the satellite. These two valuable pieces of  information help the operations team monitor the position and trajectory of the satellite.  Although not an option for all orbits, many satellites also carry GPS receivers to  enhance tracking capabilities, allowing for more effective monitoring of position and trajectory.
- Antennas
	- Quantified using gain. Different antennas have differnt gains around different directions.
	- Downlink Antennas use high gain enabling it to send data in a narrow beam and high data transfer rates.
	- TTC prioritize reliable data communication instead of high data rates and hence use low gain antennas.

Further details @[[Communication]]
### 7. Thermal Subsystem
Thermal control is a process of energy balance and management in which environmental heating plays a major role. The principal forms of environmental heating on orbit are:

- direct sunlight
- sunlight reflected off Earth (albedo)
- infrared (IR) energy emitted from earth

The thermal control is achieved by balancing the energy emitted by the satellite as IR radiation against the energy dissipated by its internal electrical components plus the energy absorbed from the environment; atmospheric convection is absent in space.

Establishing a thermal design for a satellite is usually a two-part process. The first step is to select a thermal design for the body, or basic enclosures, of the satellite that will serve as a thermal sink for all internal components. The second step is to select thermal designs for various components located both within and outside the satellite body
#### Environmental Conditions in Low Earth Orbit (LEO)

 Earth’s Albedo and infrared emission imposes need of thermal control. Long eclipse duration is the characteristic of LEO. small instruments and solar panels have small thermal inertia, so they can easily affected by the thermal cycles.

#### Typical operating range of important components

- Batteries have a very narrow operating range, between −5-20˚C
- Cameras: −30 to 40˚C
- Solar arrays have a wide operating range of −150 to 100˚C
- Infrared spectrometers, which have a range of −40 to 60˚C

**There are two types of thermal control systems:**
#### Active Thermal Control System
The [Active Thermal Control System](https://www.aero.iitb.ac.in/satelliteWiki/index.php/Active_Thermal_Control_System "Active Thermal Control System") (ATCS) uses a mechanically-pumped fluid to perform heat transfer. Although this approach is more complex, the ATCS is able to handle much greater heat loads and provide a degree of control over how heat loads are managed.
##### Heat Pipes

These devices work on capillary circulation using two phase liquid and exhibit very high and effective thermal conductivity. It consists of a tubing which is sealed off from both ends, contains small amount of fluid and annular wick material for proper fluid movement

##### Need for Heat Pipes

- In space in order to transport heat from one place to another effectively. As conduction is very limited in space so we need convection, which is much faster than conduction in heat transferring. So we need to develop fast and effective heat transport mechanism. This purpose is fulfilled by heat pipes.
- Main advantage is that it can transport heat to large distances very effectively

##### Working of Heat Pipes

Working fluid in the wick absorbs heat and and evaporates. The vapourised fluid mixes with the vapour phase which is moving in the centre of the pipe. Due to tendency of moving towards lower temperature, vapour reaches the radiating surface to transfer the heat to the heat sink. By low heat energy the vapour condenses. Annular Wick structure helps in movement of condensed vapour to the heat extracting point and again this cycle takes place. Driving mechanism is the temperature difference between source and the radiator.
![[ATC1.png]]
#### Louvers

Louvers are those active thermal-control elements who can change the area of radiating surface depending upon the amount of radiating heat. In general, a louver can reject six times ore heat in open state compared to complete closed state, where it doesn’t require power. Commonly bimetallic or spring actuated louvers are used.

##### Working and Components

- Louver radiator consist of five main elements: baseplate, blades, actuators, sensing elements, and structural elements.
- They do radiative coupling between baseplates and ambient in open position
- The actuators actuate the blades according to the desired and current temperatures.
![[900px-ATC3.png]]
#### Heaters

Used to protect the components when the temperature is low and we need high temperature. We need to use heater as the dissipative box. These are used with thermostats or solid-state controllers to maintain accurate required temperature.

##### Structure and Working

- Most commonly used heater is patch heater, it contains series of resistors between electrically insulated sheets like Kapton.
- These resistors generates heat when current is passed through them.
![[PTC3.png]]
#### Passive Thermal Control System
The [Passive Thermal Control System](https://www.aero.iitb.ac.in/satelliteWiki/index.php/Passive_Thermal_Control_System "Passive Thermal Control System") consists of insulation, coatings, heaters, and heat-pipe radiators. Its components generally have few operational requirements and require low maintenance. In addition, PTCS components are also less complex and are easier to implement.
PTCS includes the following components:
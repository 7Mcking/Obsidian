[[Information Page.canvas|Information Page]]
# Various Tests performed on Integrated Satellite

Two models of satellite are made Qualification Model (QM) and Flight Model (FM). The QM is tested for larger range of loads as compared to the FM because for qualification you always design the loads with a factor of safety. Hence, QM is tested more rigorously. But the final FM will be the one orbiting in the space, hence testing it to the limits may induce micro-cracks in the structure resulting in earlier failure.  
Once the satellite is integrated, no part of the satellite is generally removable during all if these tests, hence without being able to see the inside of the satellite, you need to perform all the checks. This poses one of the biggest challenges of making a check-out system for the integrated satellite.

## Thermo-vacuum Testing

This test is performed to simulate the environment of the satellite while in the orbit. The satellite is kept in a vacuum chamber. The inner surface of the chamber is known as shroud. The depressurization of the chamber takes time depending on how large the chamber is. Thermal cycling is started after achieving the required vacuum. We regulate the shroud temperature to influence the temperature of the satellite. Thermovac testing is done to check the working of the hardware of the satellite under various thermal loads. The thermal insulation will maintain the temperatures of the PCBs and sensors like magnetometer and GPS and also battery in the desired range. This temperature is monitored. The functioning of each PCB, sensor, actuator, battery, uplink and downlink is thoroughly tested. In short full functionality of the satellite is checked. As you can imagine all the subsystems combine during this testing. Hence, effective interfacing between different subsystem is quite important. Full functionality tests are carried out at various critical points over the varying temperature profile.

[![](https://www.aero.iitb.ac.in/satelliteWiki/images/a/af/Thermovac.png)

This is a general profile of the shroud temperature for the Thermovac test. The numbers may vary for different satellites

## Vibration Testing

Vibration Test is performed to simulated the launch environment. The satellite is fixed to a Vibration table with a mock Launch Vehicle Interface (LVI) and then subjected to different loads. After various predetermined set of loads are applied, the full functionality check of the satellite is done. Vibration test is generally done before thermovacuum test as launch loads are applied before orbit loads in the real scenario as well. Following are the various loads applied in a Vibration test:

### Static Loading

Static loading occurs on the satellite during launch as a result of the accelerations experienced during flight. Loads are applied in both lateral and longitudinal directions. The magnitude of the loads depends on the launch vehicle. All the loads apply at every element of the satellite as body forces.

### Harmonic Loading

The loading varies as a sine or cosine function in this case. This simulates the vibrations the satellite will experience during the launch. The frequency for which is tested generally ranges from 5 to 100 Hz with amplitudes depending on the launch vehicle.

### Random Loading

The conditions for testing for random vibrations are the same as that of sinusoidal vibration testing. The loads can be applied in both time and frequency domain.

## Shock Testing

The spacecraft experiences mechanical shocks during the liftoff and subsequent launch trajectory. Hence, the satellite is tested by subjecting it to shocks in an controlled environment and complete functionality is checked after the test.
# **Communication Basics for a satellite**
## **Data transmission and handling requirements**

1. Storage and retrieval of data
2. Packeting
3. Transmission after modulation
4. Reception and demodulation
![[1500px-DataLink2-1.png]] 

### What is a Transceiver?
A device which is used for both transmission and receiving purposes. Transmitted signal is called uplink and the received is signal is called as downlink
***Different Types of transceivers:***
- RF Transceivers, Ethernet transceivers, wireless transceivers etc.
***Two basic types of transceivers***
- Half Duplex: Mode where transmission and reception happen alternately. Mostly transmitter and receiver operate at the same frequency.
- Full Duplex: Mode where transmission and reception happen simultaneously. Full duplex requires transmitter and receiver to operate at different frequency so that frequencies don't interfere.

## **Antennas**

Component which changed the world from wired to wireless. It converts electromagnetic fields into current while receiving and current into electromagnetic fields during transmission

There are three types of field regions for an antenna
1. Reactive field region
	- It is the immediate vicinity of the antenna. The E-fields and H-fields are out of phase in this region and their distribution is pretty complicated
	- **Boundary is given by $R_1 = 0.62\sqrt(D^3/\lambda)$**
2. Radiative near field
	- Radiation pattern (Radiated power vs direction) varies considerably with distance from the antenna. The E-field and H-field are in phase. 
	- **The boundary is given by $R_2 = 2 D^2/\lambda$**
3. Far field
	- Radiation pattern is constant with respect to distance. Any antenna placed in this area is not affected by other antenna.
	![[Antenna1.png]]

#### **Radiation Pattern**

- Graphical representation of power distributed as a function of its direction in the field of the antenna is called its radiation pattern.
- The decibel plot received as a function of elevation or azimuth is radiation plot. Function of power w.r.t azimuth and elevation is known as a radiation function
	![[Antenna2.png]]![[Antenna3.jpg ]]
	Radiation pattern of $\lambda/2$ dipole
#### Directivity

Measure of how directed the radiation of an antenna is.
$$Directivity = (4\pi)/\int_0^{2\pi}\int_{0}^{\pi}| F(\theta,\phi)|^2sin\theta*d\theta*d\phi$$
Based on directivity antennas can be divide into 3 types
- **Isotropic**: Radiates uniform power in all directions
- **Omnidirectional**: Radiates uniform power in a plane described by the normal
- **Directional**: Radiates greater amount in one specific direction

#### **Antenna Efficiency**

<u>Ratio of power radiated by the antenna to the power delivered to the antenna</u>
Antenna efficiency is further divided into two categories radiation efficiency and impedance mismatch with total efficiency being the product of two.

***Losses could be :***
- **Conduction losses**: Power losses due to conductive elements of an antenna
- **Dielectric losses**: Electric fields induce current in nearby dielectrics reducing energy carried by fields.
- **Impedance mismatch**: Part of power reflected back by the antenna due impedance mismatch of antenna driving circuit.

#### **Voltage Standing Wave Ratio**

<u>Also known as impedance matching</u>. It is basically the amount of power reflected back from the antenna-transmitter junction. VSWR is related to the reflection coefficient  and is calculated using:
$$VSWR= \frac{1+|s_{11}|}{1-|s_{11}|}$$
**VSWR** can be found using Vector Network Analyzer.

#### **Antenna Gain**
$$Gain= Directivity*Efficiency$$
#### **Polarization**
Pattern traced out by the E-field in any electromagnetic wave.
	![[1125px-Polarization5-1.jpg]]

#### **Decibel**
Power in decibel is defined as:
$$Power = 10\\log_{10}{P}$$
### **Antenna Types**
#### Half Wave Antennas
Also known as dipole antennas. The length of the antenna is half the wavelength. Signal is fed midway. 
- It has an omnidirectional radiation pattern and linear polarization. It has low directivity

#### Folded Antennas
- Folded dipole antenna is resonant and radiates well when its length is odd integer multiple of half wavelength (eg. 0.5λ, 1.5λ, 2.5λ...etc).
- Input impedance of half wavelength folded dipole is four times that of normal half wavelength dipole i.e approx. 280 ohms.
- It is linearly polarised.
- Radiation pattern similar to half wavelength dipole.
#### Monopole Antenna
- Simplest kind of Antenna. It's just a wire and a ground plane with wire perpendicular to the ground plane. From, electromagnetic theory, the ground plane acts as a mirror and the monopole antenna acts as dipole antenna twice its length.

#### Yagi
<u>It is a directional linear antenna</u>
It has three elements
- Feed
- directors 
- reflectors
Highly directive antenna whose gain go as high as 20dBi. Bandwidth is typically small.

#### Crossed Yagi
<u>It is circular antenna</u>
It is a yagi antenna with two directional linear antennas out of phase by $90^o$

## **Amplifiers**
<u>Increases the power of the signal</u>
It is measured by its gain. Ratio of output voltage, current or power to its input.
	![[1500px-Amplifiers7.png]]
$$ Voltage Gain A_v = {\frac{V_0(t)}{V(t)}}$$
Amplifiers increase the magnitude of the output signal by some ratio. Some can change the phase of the signal too. Amplifiers are classified as:
1. Class A - $360^o$ conduction
2. Class B - $180^o$ Conduction
3. Class AB - slightly more than $180^o$ Conduction
4. Class C - Slightly less than $180^o$ Conduction

### Need of Amplifiers in communication
The strength of communication link is determined by the strength of signal at the receiver. One way is to increase at the transmitter's end and the other way is to amplify the strength of the receiver.
Amplification is the first step at the receiver's end while it is the last step and the transmitter's end.
	![[1500px-Amplifiers4.png]]
### Parameters related to Amplifiers

#### **Gain**
$$ gain(dB) = 10\log_{10}{\frac{P_{out}}{P_{in}}}dB,
 = 20\log_{10}{\frac{V_{out}}{V_{in}}}dB$$
#### **Signal to Noise Ratio**
$$SNR=\frac{P_{signal}}{P_{noise}}$$
$$SNR_{db} = 10\log_{10}{\frac{P_{signal}}{P_{noise}}}$$
#### **Noise Figure**
Measures the degradation of the SNR, caused by RF components
$$NF=10\log_{10}(F) = 10\log_{10}{\frac{SNR_{in}}{SNR_{out}}}$$
#### **Bandwidth**
The range of frequencies for which the amplifier gives desired performance.

### Low Noise Amplifiers
Amplifies low power signal without significantly degrading its SNR. Increases the power of both the signal and the noise present at its input. LNA is a broadband device and has a high gain

#### **Noise Figure of a System**
$$F= F_1+ \frac{F_2 -1}{G_1}+\frac{F_3 -1}{G_1G_2}+ \frac{F_4-1}{G_1G_2G_3}+ \dots + \frac{F_{n-1}-1}{G_1G_2G_3\dots G_{n-1}}$$
Here $F_n$ is the noise factor and $G_n$ is the power gain of the $n^{th}$ device.
	![[750px-Amplifiers5.png]]
#### Parameters of LNA
- High gain
- Low Noise Figure
- Linearity: Linearity means harmonics are not produced.
- Matching Circuits: The input and the output must be matched to 50ᘯ for optimal performance.These are the impedances looking from input and output respectively. For maximum transfer of power all the impedances of connecting components or tracks or wires should be same. If there is a mismatch the signals may get reflected and damage the amplifier.
	![[Amplifiers6.png]]
### Power Amplifiers
Converts low power radio frequency into a high power signal.RF power amplifiers drive the antenna of the transmitter.

#### Parameters of PA
- Gain: The gain should be large, typically 30-40 dB
- Input Power: Power Amplifier consumes a lot of power as it has to amplify power and drive a low impedance output (Antenna)
- Maximum input signal power
- Operating Frequency: PA IC's frequency should match input signal's frequency.


|                        | **LNA**                                       | **PA**                                            |
| ---------------------- | --------------------------------------------- | ------------------------------------------------- |
| **Placement**          | Part of the receiver (just after the antenna) | Part of the transmitter (just before the antenna) |
| **Input Signal Power** | -130 dBm to -90 dBm                           | 0 dBm to 10 dBm                                   |
| **Typical Gain**       | 10 to 15 dBm                                  | 30 to 40 dBm                                      |
| **Power Consumed**     | Very Low                                      | Very High                                         |
| **Heat Sinks**         | Not required                                  | Generates a lot of heat. Heat sinks necessary.    |

## Link Budget
Link is the path between the transmitter and the receiver comprising of all the physical channel and its parameters such as distance between the transmitter and the receiver along with electromagnetic properties of the medium
### Systemic Parameters
- Transmitter power
- Gain of the transmitter antenna and the receiver antenna
- Noise floor of the receiver
- Bit rate
- Modulation scheme
- Amplifier gains at the transmitter and the receiver
#### Calculation of Link Budget
- SNR method - For analog signals
- Eb/No method - For digital signals.
- Link budget is calculated for all signals uplink, downlink and beacon separately.
- Link budget calculations give a very good set of estimates, eg. what should be the signal power, amplifier gain and thus help in decision making during satellite building phase.
- Link budget calculations are done before starting design to get estimates of requirements and later after completing design to check whether the requirements are met.
- AMSAT-UK provides a template of excel sheet that can be used for calculating link budget of satellite signals, by tweaking with known data.
## Communication Regulations for the satellite
- Satellite transmission frequency should be licensed- The International Amateur Radio Union is responsible for allocating amateur radio frequency of transmission.
- Staying within the bandwidth
- Inclusion of call sign in the beacon.

## Beacon 
- Beacon is the satellite’s signal that signifies its presence to the world and can be tracked by almost any Ground Station or amateur radio operator
- This signal is generally transmitted in Morse code

## Important Links
http://www.eletrica.ufpr.br/evelio/TE111/Eb_N0.pdf


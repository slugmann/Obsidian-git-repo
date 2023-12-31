 #ELEC/2070 #Circuits #UniNotes
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
**Slides:**
[ELEC2070 Week 8 2021 AC Thevenin Norton Superposition](Attachments/ELEC2070%20Week%208%202021%20AC%20Thevenin%20Norton%20Superposition.pdf)
                                                                                                                                                                                                                                                                                                                                                                                                                                          
*We are concerned with applying one or more sources of electrical energy (a source defined by some forcing function) to a circuit and then quantitatively determining the consequent response throughout that circuit.*

Negative exponentials are also very common (as we have already found) and we show later that when we combine a exponential with a sinusoid, this leads us to the concept of the **complex frequency.** 

Any periodic function can be **composed as a sum of sinusoidal functions** with frequency that are **integral multiples of f0** (Fourier Transform) 

Also, the **differentials and integrals of sinusoids are sinusoids** (this is also true for exponentials) making the analysis easier. 

```ad-attention
title: Overall
All the shortcuts and methods used for DC forcing functions are applicable for AC forcing functions.
```

# Adding Impedances

**Series:**
![Pasted image 20230428124301](Attachments/Pasted%20image%2020230428124301.png)
$$\textbf{Z}_{eq} = \textbf{Z}_{1} + \textbf{Z}_{2} + ...+\textbf{Z}_{n}$$

**Parallel:**
![Pasted image 20230428124504](Attachments/Pasted%20image%2020230428124504.png)
	$$\textbf{Z}_{eq} = \frac{1}{\frac{1}{\textbf{Z}_{1}}+{\frac{1}{\textbf{Z}_{2}}}+...+{\frac{1}{\textbf{Z}_{n}}}}$$

# Thevenin & Norton Equivalent Circuits in the Frequency Domain
*Similar to the DC case but replace resistance with impedance*
![Pasted image 20230428125118](Attachments/Pasted%20image%2020230428125118.png)
```ad-example
title: **Thevenin** equivalent for the source circuit

![Pasted image 20230428125136](Attachments/Pasted%20image%2020230428125136.png)
```
```ad-abstract
title: **Norton** Equivalent for the source circuit

![Pasted image 20230428131707](Attachments/Pasted%20image%2020230428131707.png)
```

## How to calculate the equivalent circuit in the frequency domain 
The Thevenin or Norton equivalent circuit A involves three parameters: the open-circuit voltage $\textbf{V}_{oc}$ the short-circuit current $\textbf{I}_{sc}$ and the Thevenin impedance $\textbf{Z}_t$
$$\textbf{V}_{oc}=\textbf{Z}_{t} \textbf{ I}_{sc}$$
![Pasted image 20230428133445](Attachments/Pasted%20image%2020230428133445.png)
**a)** An open circuit is connected across the terminals of Circuit A - The voltage across that open circuit is equal to $\textbf{V}_{oc}$
**b)** A short circuit is connected across terminals of Circuit A - The current through that short circuit is the short circuit current $\textbf{I}_{sc}$
**c)** $\textbf{Z}_t$ is the equivalent impedance of Circuit A* Which is formed by replacing all the independent voltage (or current) sources by short (or open) circuits.
*Dependent sources are not replaced with open or short circuits.*

## How do?
![Pasted image 20230428140724](Attachments/Pasted%20image%2020230428140724.png)
### Example 1
![Pasted image 20230428140740](Attachments/Pasted%20image%2020230428140740.png)

**Gather Variables:**
$\omega = 160 \text{ rad/s}$
$\textbf{V}_{s}=36 \angle 0\degree$

$\textbf{Z}_{L}(\omega)=j \omega L = j160*2.25 = j360\ohm$
$\textbf{Z}_{C}=\frac{1}{j \omega C}=\frac{1}{j160*50*10^{-6}} = -j125 \ohm$
$\textbf{Z}_{R}=R=200 \ohm$

Replace circuit values with impedances.
![Pasted image 20230428141231](Attachments/Pasted%20image%2020230428141231.png)
![Pasted image 20230428141508](Attachments/Pasted%20image%2020230428141508.png)
$$\textbf{V}_{oc}=\frac{j360}{200+j360}*36$$
*No current through capacitor*

$$\textbf{V}_{oc}=31.47 \angle 29.1\degree V$$
*Phasor form*

**Switch off voltage source:**
$$\textbf{Z}_{t}= -j125 + j360||200$$
$$\textbf{Z}_{t}= -j125 + \frac{200*j360}{200+j360}$$
$$\textbf{Z}_{t}= -j125 + 152.83+j84.91$$
$$\textbf{Z}_{t}= 158 \angle (-14.7\degree)\ohm$$
![Pasted image 20230428142151](Attachments/Pasted%20image%2020230428142151.png)
**This is an equivalent circuit to the time domain frequency circuit**

# Source Transformation in the frequency domain
*Similar to DC, but replace resistance with impedance*
![Pasted image 20230428143708](Attachments/Pasted%20image%2020230428143708.png)

### Example 1 Using Source Transformation
![Pasted image 20230428144113](Attachments/Pasted%20image%2020230428144113.png)
$$j360||200 = \frac{200*j360}{200+j360}=152.83+j84.91=174.8\angle 29.1\degree$$

![Pasted image 20230428144653](Attachments/Pasted%20image%2020230428144653.png)
$$\textbf{V}_{oc}=(174.8\angle29.1\degree)(0.18\angle0\degree)=31.5\angle29.1$$

![Pasted image 20230428144839](Attachments/Pasted%20image%2020230428144839.png)
$$174.8\angle 29.1\degree - j125=152.83+j84.91-j125=152.83-j40.094$$

# Superposition in the Frequency Domain
*Frequency domain circuits are analysed ONE FREQUENCY AT A TIME. This means that all sources must be at the SAME frequency for a single calculation*

If there are sources at different frequencies, we use superposition to understand the overall behaviour of the circuit.

- The sources with the **same frequency** are analysed together while all the **"other frequency" sources are "zeroed"**. *Independent voltage sources = shorts, Independent current sources = open*.

- All the individual solutions corresponding to each frequency are then **added up in the time domain** to give the total time-domain solution.

There can also be sources at DC (or zero frequency) - This solution can be added to the AC time-domain solution to obtain the total solution.

### Example
*Find **v0** in the following circuit*
![Pasted image 20230428150853](Attachments/Pasted%20image%2020230428150853.png)
Find $\textbf{V}_{o1}$
**Zero Source 2**
![Pasted image 20230428151054](Attachments/Pasted%20image%2020230428151054.png)
![Pasted image 20230428151212](Attachments/Pasted%20image%2020230428151212.png)

Find $\textbf{V}_{o2}$
**Zero Source 1**
![Pasted image 20230428151142](Attachments/Pasted%20image%2020230428151142.png)
![Pasted image 20230428151232](Attachments/Pasted%20image%2020230428151232.png)
$$v_{o}(t) = 15.46\cos(50t+104.9\degree)+20.24\cos(10t+10.94\degree)V$$

#### Graphical Representation
![Pasted image 20230428151427](Attachments/Pasted%20image%2020230428151427.png)$$v_{o}(t) = 15.46\cos(50t+104.9\degree)+20.24\cos(10t+10.94\degree)V$$
### Example 2
*Find the steady state current i(t)*
![Pasted image 20230428152058](Attachments/Pasted%20image%2020230428152058.png)
$$v_{s}(t) = 8 +8\cos(400t-135\degree)V$$

Here, a single source has 2 components. DC ($8$) and AC ($8\cos(400t-135\degree)$) 

$\omega_{DC}$ = 0 rad/s
$\omega_{AC}$ = 400 rad/s

**DC:** $Z_{L}(0)=j0*0.05=0\ohm$ 
**AC:** $Z_{L}(400) = j400*0.05 = j20\ohm$
![Pasted image 20230428152439](Attachments/Pasted%20image%2020230428152439.png)
$$i(t)=0.533 + 0.32\cos(400t-188.1\degree)A$$

### Example 2 But a bit bigger
![Pasted image 20230428153143](Attachments/Pasted%20image%2020230428153143.png)

## Time Domain and Frequency Domain Relationships
![Pasted image 20230428153237](Attachments/Pasted%20image%2020230428153237.png)

# Phasor Diagrams
Phasors are complex numbers and can be graphed in the complex plane. The relationship between phasors when drawn on the complex plane is called a phasor diagram.

*A phasor diagram is graphical representation of phasors and their relationships on the complex plane.*

**Why phasor diagrams?**
1. Provides a graphical method for solving problems for when calculations are tedious.
2. Makes checking analytical solutions much easier
3. Helps in certain symmetrical problems by enabling the symmetry to be recognised and helpfully applied.

Multiplication and division result in the addition and subtraction respectively of the phasor **ANGLES**. The amplitude also changes but depends on the scale of the diagram (e.g. Current and voltage may have their own scale, but the angles will be the same).

```ad-example
title: Multiplication/Division
$\text{Multiplication } \rightarrow V_{1}*V_{2}= \theta_{1}+\theta_{2}$

$\text{Division } \rightarrow V_{1}/V_{2}= \theta_{1}-\theta_{2}$

![Pasted image 20230428154619](Attachments/Pasted%20image%2020230428154619.png)
```
```ad-summary
title: Addition/Subtraction
![Pasted image 20230428155425](Attachments/Pasted%20image%2020230428155425.png)

```

### Example 3
*Find the voltages across each circuit element*
**Assume current is:** $\textbf{I}=I_{m}\angle 0$
![Pasted image 20230428155644](Attachments/Pasted%20image%2020230428155644.png)
Resistor Voltage: $\textbf{V}_{R} = RI_{m} \angle 0$

Inductor Voltage: $\textbf{V}_{L}=j \omega LI_{m}\angle0 = \omega L I_{m}\angle 90\degree$

Capacitor Voltage: $\textbf{V}_{C}=-j \frac{1}{\omega C}I_{m}\angle 0 = \frac{1}{\omega C}I_{m}\angle -90\degree$

![Pasted image 20230428160216](Attachments/Pasted%20image%2020230428160216.png)
Using KVL we find:
$V_{s}=V_{R}+V_{L}+V_{C}=V_{R}+(V_{L}+V_{C})$

The phasor $V_{L}+V_{C}$ is given by:
$$V_{L}+V_{C}=j(\omega L - \frac{1}{\omega C})(I_{m}\angle 0\degree)=(\omega L - \frac{1}{C\omega})(I_{m}\angle 90 \degree)$$

This is much easier on the phasor diagram:
![Pasted image 20230428161041](Attachments/Pasted%20image%2020230428161041.png)
$$V_{S} = V_{R}+(V_{L}+V_{C})=R I_{m}+j(\omega L - \frac{1}{C\omega})(I_{m})$$

Easily done on the phasor diagram:
![Pasted image 20230428161022](Attachments/Pasted%20image%2020230428161022.png)

# The Natural Response in AC Circuits
*Generally, to find the complete response of an AC circuit with switches:*
1. Represent the required (complete) response by a differential equation.
2. Find the general solution of the homogenous differential equation. This solution is the natural response $v_{n}(t)$. The natural response will contain unknown constants that will be evaluated later.
3. Find a solution of the differential equation due to the AC source. This solution is the forced response $v_{f}(t)$.
4. Represent the complete response of the circuit as $v(t)=v_{n}(t)+v_{r}(t)$
5. Use the initial conditions, for example, the initial values of the currents in inductors and the voltage across capacitors to evaluate the unknown constants.

**This process is not difficult using phasors**

### Example 4
Consider the switched circuit problem:
![Pasted image 20230428163148](Attachments/Pasted%20image%2020230428163148.png)
**Step 1**: For t<0 the switch is open. (Both circuits are equivalent just in time (a) and frequency (b) domains
![Pasted image 20230428163347](Attachments/Pasted%20image%2020230428163347.png)
Voltage division gives us the voltage across the capacitor:
$$V(5) = \frac{-j4}{4-j4} 12 \angle 0\degree = \frac{48 \angle -90\degree}{5.66\angle -45\degree}=8.485\angle -45\degree V$$

In the time domain, the forced response (steady state voltage): $v(t) = 8.485\cos (5t-45\degree)V$
At t= 0 the voltage across the capacitor is: $8.485\cos(0-45\degree)=6V$

Remember, the capacitor voltage will be 6V just after (t=0+)

**Step 2:** For t>0 we have a new circuit (a) or in the frequency domain (b)
![Pasted image 20230428215550](Attachments/Pasted%20image%2020230428215550.png)
Voltage division gives us the voltage across the capacitor:
$$V(5) = \frac{-j4}{2-j4} 12 \angle 0\degree = \frac{48 \angle -90\degree}{4.47\angle -63.4\degree}=8.485\angle -45\degree V$$
Time domain forced response (steady state voltage): $v(t)=10.74\cos(5t-26.6\degree)V$
**Step 3:** Immediately after the switch is closed, the circuit is not in steady state and hence
the natural response will be:$$v_n(t)=Ke^{\frac{-t}{R_{t}C}}$$
$R_{t}C = 2*50*10^{-3}=0.1$ s
![Pasted image 20230428220451](Attachments/Pasted%20image%2020230428220451.png)
$$v(t) = v_{n}(t)+v_{f}(t) = Ke^{-10t}+10.74\cos(5t-26.6\degree)$$
$10.74\cos(5(0)-26.6\degree) = 9.6$
When $t=0$, $v(t) = 6V$ Therefore: $6=K+9.6$ Therefore $K=-3.6$

![Pasted image 20230428221434](Attachments/Pasted%20image%2020230428221434.png)

# Power
We are always interested in the circuit response BUT we are also interested in:
1. The amount of energy supplied from the source(s)
2. The amount of energy dissipated or stored within a circuit
3. The way in which energy is delivered to the points at which the responses are determined.

Primarily, we want the *rate* at which power is being stored or generated, hence we are interested in **POWER** (Joules per second)

## AC Power
Different kinds of power for different kinds of signals, i.e,
- **Instantaneous power** - relates to any signal
- **Average power** - relates to periodic signals.
- **Complex power** - Since AC currents and voltages are described using complex numbers (phasors)

## Instantaneous Power
**Instantaneous power:**
*Only relevant to the time domain*
$$p(t) = v(t)*i(t) W$$
![Pasted image 20230428222633](Attachments/Pasted%20image%2020230428222633.png)
The AC currents and voltages (note they have the same $\omega$) across any element (in general) is:
$$v(t) = V_{m}\cos(\omega t + \theta_{V})$$
$$i(t) = I_{m}\cos(\omega t + \theta_I)$$

Subbing in these functions to our instantaneous power equation and using some trig functions we get:

$$p(t) = \frac{V_{m}I_{m}}{2}[\cos(\theta_{V}-\theta_{I}) + \cos(2\omega t + \theta_{V} + \theta_{I})]$$

$\cos(\theta_{V}-\theta_{I})$ = Constant
$\cos(2\omega t + \theta_{V} + \theta_{I})$ = Periodic in time (at twice the frequency)
![Pasted image 20230428224013](Attachments/Pasted%20image%2020230428224013.png)


# Power of Periodic Signals
![Pasted image 20230428224044](Attachments/Pasted%20image%2020230428224044.png)
We only need to examine the average power over one period.

## Average Power
**Average Power:**
$$P = \frac{1}{T}\int^{t_{0}+T}_{t_{0}}p(t) dt$$
*Unit: Watts - It is ONLY defined over one period, T (since it all repeats again during the next T)*

The average power may be computed by integrating the instantaneous power over ANY interval which is one period in length.

Using our instantaneous power:
$p(t) = \frac{V_{m}I_{m}}{2}[\cos(\theta_{V}-\theta_{I}) + \cos(2\omega t + \theta_{V} + \theta_{I})]$

```ad-note
Average AC Power:

$P=\frac{V_{m}I_{m}}{2}\cos(\theta_{V}-\theta_{I})$

```

### Example nu,ber
![Pasted image 20230428224749](Attachments/Pasted%20image%2020230428224749.png)

### Average power for a sinusoidal function
Given the time-domain voltage $v = 4\cos\frac{\pi t}{6}V$  find both the average power and an expression for the instantaneous power that result when the corresponding phasor voltage phasor voltage $V=4\angle 4\degree V$ is applied across an impedance $Z = 2\angle 60\degree \ohm$

The phasor current is $\frac{V}{Z}=2\angle -60\degree A$, and so the average power is:
$P=\frac{1}{2}(4)(2)\cos 60\degree = 2 W$

Time dependent voltage is: $v(t) = 4 \cos \frac{\pi t}{6} V$
Time dependent current is: $i(t) = 2 \cos(\frac{\pi t}{6}-60\degree)$
Instantaneous Power: $p(t) = 8 \cos \frac{\pi t}{6} * \cos(\frac{\pi t}{6}-60\degree)=2+4\cos(\frac{\pi t}{3}-60\degree)W$

# Power across Inductive Load
#todo 
- [ ] Convert these to text

![Pasted image 20230428225825](Attachments/Pasted%20image%2020230428225825.png)

## AC Average power of the circuit elements
![Pasted image 20230429003155](Attachments/Pasted%20image%2020230429003155.png)
## Average power defined using Impedance
![Pasted image 20230429004825](Attachments/Pasted%20image%2020230429004825.png)

## The Effective value of a Periodic Signal
The effective value of any periodic current (or voltage) is equal to the value of the direct current (or voltage) which, flowing through a resistance R, delivers the same power to R as the periodic current (or voltage) does.
![Pasted image 20230429005015](Attachments/Pasted%20image%2020230429005015.png)

## Root Mean Square Values
![Pasted image 20230429005315](Attachments/Pasted%20image%2020230429005315.png)

### Example
![Pasted image 20230429005615](Attachments/Pasted%20image%2020230429005615.png)

## RMS of other Periodic Waveforms
![Pasted image 20230429005655](Attachments/Pasted%20image%2020230429005655.png)

# Complex Power
![Pasted image 20230429005753](Attachments/Pasted%20image%2020230429005753.png)

## Reactive power
![Pasted image 20230429005819](Attachments/Pasted%20image%2020230429005819.png)

### Explanation
Purely reactive loads such as inductors and capacitors dissipate zero power, yet the fact that they drop voltage and draw current gives the deceptive impression that they actually do dissipate power. This “phantom power” is called reactive power, and it is measured in a unit called Volt-Amps-Reactive (VAR), rather than Watts. The mathematical symbol for reactive power is the capital letter Q. The actual amount of power being used, or dissipated, in a circuit is called the real (average) power, and it is measured in Watts (symbolized by the capital letter P, as always). 
As a rule, real power is a function of a circuit’s dissipative elements, usually resistances (R). Reactive power is a function of a circuit’s reactance (X).

## Complex power wrt Impedance
![Pasted image 20230429005917](Attachments/Pasted%20image%2020230429005917.png)

## Complex power in terms of impedance
![Pasted image 20230429005953](Attachments/Pasted%20image%2020230429005953.png)

## Power in the frequency domain
![Pasted image 20230429010031](Attachments/Pasted%20image%2020230429010031.png)
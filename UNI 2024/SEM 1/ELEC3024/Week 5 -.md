---
date: 2024-04-25
tags: 
status: Incomplete
Relevant Questions: 
Relevant Notes: 
Relevant Links:
---
**Lecture Slides:**
[Frequency Response](Attachments/Workshop%20Ch10%20-%20Frequency%20Response_v1_annotated-1.pdf)
# Frequency Response (Bode Plots)
- Not as intuitive as root locus
- Provides a new vantage point from which to view feedback control systems:
	- When modelling TF functions from physical data.
	- Designing lead compensators to meet a steady-state error requirement and a transient response requirement
	- Finding the stability of nonlinear systems
	- In settling ambiguities when sketching root locus

- In the steady state, sinusoidal inputs to a linear system generate sinusoidal responses of the same frequency.
- Responses are of the same frequency as the input, they differ in magnitude and phase angle from the input.
- These differences are functions of frequency
- **Sinusoids representation**
	- Sinusoids can be represented as complex numbers called *phasors*
	- A system causes both the amplitude and phase angle of the input to be changed
![500](Attachments/Pasted%20image%2020240425222054.png)

- Analytical expressions for the frequency response can be obtained from the TF G(s).
$$G(j \omega) = G(s)|_{s\rightarrow j \omega}$$

- **Plotting of the frequency response**
$$G(j \omega) = M_{G} (\omega) \angle \phi_{G} (\omega)$$
As a function of **frequency** with separate magnitude and phase plots


## Asymptotic Approximations: Bode Plots
- **Bode plots** of Bode diagrams: Curves of the **log-magnitude** and **phase frequency** response as functions of $\log \omega$
$$G(s) = \frac{K(s+z_{1})(s+z_{2})\dots(s+z_{k})}{s^{m} (s+p_{1})(s+p_{2})\dots(s+p_{n})}= \frac{Ne^{i \angle N}}{De^{j \angle D}} = \frac{N}{D}e^{j \angle N-D}$$

**The magnitude response is given by:**
$$|G(s)| = \frac{K|(s+z_{1})||(s+z_{2})|\dots|(s+z_{k})|}{s^{m} |(s+p_{1})| |(s+p_{2})|\dots|(s+p_{n})|}$$

Converting the **magnitude response into dB** we obtain:
$$20 \log |G(j \omega)| = 20 \log K + 20 \log |(s+z_{1})| + 20 \log |(s+z_{2})| + \dots $$
$$\dots - 20 \log|s^{m}| - 20 \log |(s+p_{1})|- \dots |_{s \rightarrow j \omega}$$

**Phase frequency response**
Is the sum of the phase frequency response curves of the **zero terms** minus the sum of the phase frequency response curves of the **pole terms**.

**Bode plots for $G(s) = (s+a)$**
- Low frequency asymptote

$$G(s) = (s+a), \text{ } s=j \omega$$
$$G(j \omega) = (j \omega + a) = a \left( j \frac{\omega}{a} + 1 \right)$$

At low frequencies when $\omega$ approaches zero: $G(j \omega) \approx a$
The magnitude response in dB is: $20 \log M = 20\log a$
![](Attachments/Pasted%20image%2020240425225545.png)
![](Attachments/Pasted%20image%2020240425225601.png)
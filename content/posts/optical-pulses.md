---
title: "Optical Pulses: Lorentzian, Gaussian, and Sech²"

date: 2025-06-28
authors: ["Brian Sinquin"]
description: "A detailed exploration of common optical pulse shapes: Lorentzian, Gaussian, and Sech², covering their mathematical definitions, FWHM, energy integrals, useful formulas, and autocorrelation functions."
tags: ["Optics", "Pulse Propagation", "Lorentzian", "Gaussian", "Sech²", "Nonlinear Optics"]
---
<!--more-->
This post provides a comprehensive overview of three fundamental optical pulse shapes: Lorentzian, Gaussian, and Sech². We will delve into their mathematical definitions, derive key properties such as Full Width at Half Maximum (FWHM), energy integrals, and explore their autocorrelation functions. Understanding these pulse shapes is crucial in various fields, including fiber optics, laser physics, and nonlinear optics.

## Introduction to Optical Pulse Shapes

Optical pulses are transient bursts of light, often characterized by their temporal intensity profile. Different physical phenomena can give rise to distinct pulse shapes. Here, we focus on three commonly encountered profiles due to their analytical tractability and relevance in experimental and theoretical contexts.

---

## 1. Gaussian Pulse

The Gaussian pulse is perhaps the most ubiquitous pulse shape in optics, often serving as an ideal model due to its unique properties, such as maintaining its shape during linear propagation in dispersive media (in the absence of higher-order dispersion).

### 1.1. Mathematical Definition

A Gaussian pulse in the time domain, centered at $t=0$, can be described by its electric field amplitude $E(t)$ or its intensity $I(t) = |E(t)|^2$.

The electric field amplitude is given by:
$$E(t) = E_0 \exp\left(-\frac{t^2}{2\tau_g^2}\right)$$
where $E_0$ is the peak electric field amplitude and $\tau_g$ is a parameter related to the pulse duration.

The intensity profile is:
$$I(t) = |E(t)|^2 = I_0 \exp\left(-\frac{t^2}{\tau_g^2}\right)$$
where $I_0 = |E_0|^2$ is the peak intensity.

### 1.2. Full Width at Half Maximum (FWHM)

The FWHM, denoted as $\Delta t_{FWHM}$, is the duration over which the pulse intensity is at least half of its peak value.
{{< admonition example "Derivation" >}}
To find the FWHM, we set $I(t) = I_0/2$:

$I_0 \exp\left(-\frac{t^2}{\tau_g^2}\right) = \frac{I_0}{2}$
$\exp\left(-\frac{t^2}{\tau_g^2}\right) = \frac{1}{2}$
Take the natural logarithm of both sides:
$-\frac{t^2}{\tau_g^2} = \ln\left(\frac{1}{2}\right) = -\ln(2)$
$t^2 = \tau_g^2 \ln(2)$
$t = \pm \tau_g \sqrt{\ln(2)}$
The FWHM is the difference between these two values:
$\Delta t_{FWHM} = 2 \tau_g \sqrt{\ln(2)}$
{{< /admonition >}}

### 1.3. Energy Integral

The energy $W$ of a pulse is proportional to the integral of its intensity over all time:
{{< admonition example "Derivation" >}}
$W = \int_{-\infty}^{\infty} I(t) dt = I_0 \int_{-\infty}^{\infty} \exp\left(-\frac{t^2}{\tau_g^2}\right) dt$
This is a standard Gaussian integral. Recall that $\int_{-\infty}^{\infty} \exp(-ax^2) dx = \sqrt{\frac{\pi}{a}}$.
Here, $a = 1/\tau_g^2$.
So,
$W = I_0 \sqrt{\pi \tau_g^2} = I_0 \tau_g \sqrt{\pi}$
{{< /admonition >}}

### 1.4. Useful Formulas

*   **Relationship between $\tau_g$ and FWHM:** $\tau_g = \frac{\Delta t_{FWHM}}{2\sqrt{\ln(2)}}$
*   **Peak power $P_0$ and energy $W$:** $W = P_0 \tau_g \sqrt{\pi}$ (assuming $I_0$ is peak power)

### 1.5. Autocorrelation

The autocorrelation function $G(\tau)$ of a pulse $I(t)$ is defined as:
$$G(\tau) = \int_{-\infty}^{\infty} I(t) I(t-\tau) dt$$
For a Gaussian pulse $I(t) = I_0 \exp\left(-\frac{t^2}{\tau_g^2}\right)$:
$$G(\tau) = I_0^2 \int_{-\infty}^{\infty} \exp\left(-\frac{t^2}{\tau_g^2}\right) \exp\left(-\frac{(t-\tau)^2}{\tau_g^2}\right) dt$$
$$G(\tau) = I_0^2 \int_{-\infty}^{\infty} \exp\left(-\frac{t^2 + (t-\tau)^2}{\tau_g^2}\right) dt$$
$$G(\tau) = I_0^2 \int_{-\infty}^{\infty} \exp\left(-\frac{t^2 + t^2 - 2t\tau + \tau^2}{\tau_g^2}\right) dt$$
$$G(\tau) = I_0^2 \int_{-\infty}^{\infty} \exp\left(-\frac{2t^2 - 2t\tau + \tau^2}{\tau_g^2}\right) dt$$
To solve this integral, we complete the square in the exponent:
$$2t^2 - 2t\tau + \tau^2 = 2\left(t^2 - t\tau + \frac{\tau^2}{2}\right) = 2\left(t - \frac{\tau}{2}\right)^2 + \frac{\tau^2}{2}$$
So the exponent becomes:
$$-\frac{2\left(t - \frac{\tau}{2}\right)^2 + \frac{\tau^2}{2}}{\tau_g^2} = -\frac{2\left(t - \frac{\tau}{2}\right)^2}{\tau_g^2} - \frac{\tau^2}{2\tau_g^2}$$
$$G(\tau) = I_0^2 \exp\left(-\frac{\tau^2}{2\tau_g^2}\right) \int_{-\infty}^{\infty} \exp\left(-\frac{2\left(t - \frac{\tau}{2}\right)^2}{\tau_g^2}\right) dt$$
Let $u = t - \frac{\tau}{2}$, then $du = dt$. The integral becomes:
$$\int_{-\infty}^{\infty} \exp\left(-\frac{2u^2}{\tau_g^2}\right) du$$
This is again a Gaussian integral with $a = 2/\tau_g^2$.
So, the integral evaluates to $\sqrt{\frac{\pi}{2/\tau_g^2}} = \sqrt{\frac{\pi \tau_g^2}{2}} = \tau_g \sqrt{\frac{\pi}{2}}$.
Therefore, the autocorrelation of a Gaussian pulse is:
$$G(\tau) = I_0^2 \tau_g \sqrt{\frac{\pi}{2}} \exp\left(-\frac{\tau^2}{2\tau_g^2}\right)$$
This shows that the autocorrelation of a Gaussian pulse is also a Gaussian pulse, but with a different width. The FWHM of the autocorrelation function is $\Delta \tau_{FWHM} = 2 \tau_g \sqrt{\ln(2)/2} = \Delta t_{FWHM} / \sqrt{2}$.

---

## 2. Sech² Pulse

The hyperbolic secant squared (sech²) pulse is particularly important in nonlinear fiber optics, as it is the natural shape of a fundamental soliton in optical fibers.

### 2.1. Mathematical Definition

The intensity profile of a sech² pulse, centered at $t=0$, is given by:
$$I(t) = I_0 \text{sech}^2\left(\frac{t}{\tau_s}\right)$$
where $I_0$ is the peak intensity and $\tau_s$ is a parameter related to the pulse duration.

### 2.2. Full Width at Half Maximum (FWHM)

To find the FWHM, we set $I(t) = I_0/2$:
$I_0 \text{sech}^2\left(\frac{t}{\tau_s}\right) = \frac{I_0}{2}$
$\text{sech}^2\left(\frac{t}{\tau_s}\right) = \frac{1}{2}$
$\text{sech}\left(\frac{t}{\tau_s}\right) = \frac{1}{\sqrt{2}}$
Recall that $\text{sech}(x) = \frac{1}{\cosh(x)}$. So, $\cosh\left(\frac{t}{\tau_s}\right) = \sqrt{2}$.
Using the definition $\cosh(x) = \frac{e^x + e^{-x}}{2}$:
$\frac{e^{t/\tau_s} + e^{-t/\tau_s}}{2} = \sqrt{2}$
Let $x = e^{t/\tau_s}$. Then $x + 1/x = 2\sqrt{2}$, or $x^2 - 2\sqrt{2}x + 1 = 0$.
Using the quadratic formula $x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$:
$x = \frac{2\sqrt{2} \pm \sqrt{(2\sqrt{2})^2 - 4(1)(1)}}{2} = \frac{2\sqrt{2} \pm \sqrt{8 - 4}}{2} = \frac{2\sqrt{2} \pm 2}{2} = \sqrt{2} \pm 1$
Since $x = e^{t/\tau_s}$, we have $e^{t/\tau_s} = \sqrt{2} \pm 1$.
Taking the natural logarithm:
$\frac{t}{\tau_s} = \ln(\sqrt{2} \pm 1)$
We know that $\ln(\sqrt{2} - 1) = -\ln(\sqrt{2} + 1)$. So, $t = \pm \tau_s \ln(\sqrt{2} + 1)$.
The FWHM is:
$\Delta t_{FWHM} = 2 \tau_s \ln(\sqrt{2} + 1)$
Numerically, $\ln(\sqrt{2} + 1) \approx 0.88137$. So, $\Delta t_{FWHM} \approx 1.7627 \tau_s$.



### 2.3. Energy Integral

The energy $W$ of a sech² pulse is:
$W = \int_{-\infty}^{\infty} I(t) dt = I_0 \int_{-\infty}^{\infty} \text{sech}^2\left(\frac{t}{\tau_s}\right) dt$
Let $u = t/\tau_s$, then $dt = \tau_s du$.
$W = I_0 \tau_s \int_{-\infty}^{\infty} \text{sech}^2(u) du$
Recall that $\int \text{sech}^2(u) du = \tanh(u)$.
So, $\int_{-\infty}^{\infty} \text{sech}^2(u) du = [\tanh(u)]_{-\infty}^{\infty} = \tanh(\infty) - \tanh(-\infty) = 1 - (-1) = 2$.
Therefore, the energy of a sech² pulse is:
$W = 2 I_0 \tau_s$

### 2.4. Useful Formulas

*   **Relationship between $\tau_s$ and FWHM:** $\tau_s = \frac{\Delta t_{FWHM}}{2\ln(\sqrt{2} + 1)}$
*   **Peak power $P_0$ and energy $W$:** $W = 2 P_0 \tau_s$ (assuming $I_0$ is peak power)

### 2.5. Autocorrelation

The autocorrelation of a sech² pulse is more complex to derive analytically than for a Gaussian pulse. It is known that the autocorrelation of a sech² pulse is not a simple sech² function. However, its FWHM is related to the pulse FWHM.

The FWHM of the intensity autocorrelation function for a sech² pulse is approximately $1.543 \times \Delta t_{FWHM}$.


---

## 3. Lorentzian Pulse

Lorentzian pulses are less common as fundamental pulse shapes in linear optics but can arise in certain physical contexts, such as in the output of a homogeneously broadened laser or due to specific filtering effects.

### 3.1. Mathematical Definition

The intensity profile of a Lorentzian pulse, centered at $t=0$, is given by:
$$I(t) = I_0 \frac{1}{1 + (t/\tau_l)^2}$$
where $I_0$ is the peak intensity and $\tau_l$ is a parameter related to the pulse duration.

### 3.2. Full Width at Half Maximum (FWHM)

To find the FWHM, we set $I(t) = I_0/2$:
$I_0 \frac{1}{1 + (t/\tau_l)^2} = \frac{I_0}{2}$
$\frac{1}{1 + (t/\tau_l)^2} = \frac{1}{2}$
$1 + (t/\tau_l)^2 = 2$
$(t/\tau_l)^2 = 1$
$t/\tau_l = \pm 1$
$t = \pm \tau_l$
The FWHM is:
$\Delta t_{FWHM} = 2 \tau_l$

### 3.3. Energy Integral

The energy $W$ of a Lorentzian pulse is:
$W = \int_{-\infty}^{\infty} I(t) dt = I_0 \int_{-\infty}^{\infty} \frac{1}{1 + (t/\tau_l)^2} dt$
Let $u = t/\tau_l$, then $dt = \tau_l du$.
$W = I_0 \tau_l \int_{-\infty}^{\infty} \frac{1}{1 + u^2} du$
Recall that $\int \frac{1}{1 + u^2} du = \arctan(u)$.
So, $\int_{-\infty}^{\infty} \frac{1}{1 + u^2} du = [\arctan(u)]_{-\infty}^{\infty} = \arctan(\infty) - \arctan(-\infty) = \frac{\pi}{2} - \left(-\frac{\pi}{2}\right) = \pi$.
Therefore, the energy of a Lorentzian pulse is:
$W = \pi I_0 \tau_l$

### 3.4. Useful Formulas

*   **Relationship between $\tau_l$ and FWHM:** $\tau_l = \frac{\Delta t_{FWHM}}{2}$
*   **Peak power $P_0$ and energy $W$:** $W = \pi P_0 \tau_l$ (assuming $I_0$ is peak power)

### 3.5. Autocorrelation

The autocorrelation of a Lorentzian pulse is also a Lorentzian pulse.If $I(t) = I_0 \frac{1}{1 + (t/\tau_l)^2}$, then its autocorrelation $G(\tau)$ is:$G(\tau) = C \frac{1}{1 + (\tau / (2\tau_l))^2}$where $C$ is a constant related to the energy.The FWHM of the autocorrelation function for a Lorentzian pulse is $2 \times \Delta t_{FWHM}.

---

## Conclusion

This post has provided a detailed mathematical treatment of Gaussian, Sech², and Lorentzian optical pulse shapes. Understanding their definitions, FWHM, energy content, and autocorrelation properties is fundamental for analyzing and designing systems involving ultrashort pulses. Each pulse shape has its unique characteristics and relevance in different areas of optics and photonics.

{{< admonition tip "Tip: Pulse Duration Definitions" >}}
It's important to note that pulse duration can be defined in various ways (e.g., FWHM, $1/e^2$ width for Gaussian pulses). Always be clear about the definition used when comparing pulse durations.
{{< /admonition >}}

{{< admonition warning "Warning: Idealized Shapes" >}}
These pulse shapes are idealized. Real-world pulses may deviate from these perfect forms due to various factors like spectral filtering, nonlinear effects, and detector response.
{{< /admonition >}}

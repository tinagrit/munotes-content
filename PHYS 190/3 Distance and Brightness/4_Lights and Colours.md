Lecture 8

> [!warning] This content is **AFTER** Midterm 1

## Light as waves
- Light has **a wave**
- The distance of one wave cycle is a **period**, where the length of a period is a **wavelength** ($\lambda$)

![[chart21A.png|500]]

Different "**kinds**" of light is distinguished by its wavelength. 
Lights that are visible to our eyes are between $380$-$750$ nano ($10^{-9}$) metres
- Redder lights (yellow/orange/red) have **longer (→)** wavelengths
- Bluer lights (blue/purple) have **shorter (←)** wavelengths

![[spectrum.webp|650]]

### Frequency
The frequency ($f$) of a wave is the **number of periods** that pass a fixed point in one second. Frequency is measured in **Hertz** ($\text{Hz}$; cycle per second)

Recall that the [[2_Scientific Notation#Speed of light|Speed of light]] is $c=3\times 10^{8} \text{ m/s}$, we can find the time ($t$) light takes to travel one wavelength ($\lambda$).

Using the speed-distance formula:
$$
\text{speed}=\dfrac{\text{distance}}{\text{time}}
$$
Substituting:
$$
c=\dfrac{\lambda}{t}
$$
$t$ is an **inverse** of $f$ (frequency), since for **higher** frequency, **less** time is needed to travel one period. We have:
$$
t=f^{-1} \implies t=\dfrac{1}{f}
$$

Substituting:
$$
c=\lambda f
$$

Rearranging:
$$
\boxed{ \lambda = \dfrac{c}{f} }
$$

### Energy
Energy ($E$) is **proportional** to [[#Frequency|frequency]].
$$
\begin{align}
\uparrow\text{ energy} &  & \uparrow\text{ frequency}
\end{align}
$$
$$
E \propto f
$$

![[chart22A.png|650]]


---
## Colours

To measure colours, different **colour filters** are used to only let lights of a specific colour pass through.

![[Screenshot 2026-01-30 at 3.08.52 AM.png|500]]<span style="display:inline-block;width:100%;text-align:center;font-style:italic;">kwtelescope.com</span>

For example, the filter $\text{B}$ (blue) only lets blue light through, and $\text{V}$ (green) only lets green light through.

We then measure the [[2_Stellar Brightness#Apparent magnitude|magnitude]] of filtered lights between two colours, and **take the difference**.

### Colour index
The colour index is the [[2_Stellar Brightness#Apparent magnitude|magnitude]] difference between the two colours. 

For example, the $\text{B-V}$ index is the magnitude of:
$$
m_{\text{B}}-m_{\text{V}}
$$
*Polaris* has a $\text{B-V}$ of $0.6$, since its $m_{\text{B}}-m_{\text{V}}=2.6-2.0=0.6$

When listing a colour index, always list the ***bluer*** (purple/blue) filter **first**.

Recall that the **lower** the magnitude, the **higher** the intensity
- If *Polaris* has a $\text{B-V}$ of $0.6$,
- and *Merak* has a $\text{B-V}$ of $0.04$,
- then The *Merak* is **more blue** and the *Polaris* is **more red**

![[chart23A.png|550]]


> [!tip] Colour is **independent** of distance
> Recall that brightness [[3_Luminosity#Luminosity|decreases]] with the square of distance, this is true **for all wavelengths**.
> The two colour filters, for example, $\text{B}$ and $\text{V}$ will both be equally affected by distance, and wouldn't affect $\text{B-V}$.


---
## Temperature

**All objects** **glows** (gives off light), although only very hot objects glow ***visible light***.

Objects at body/room temperature, **like us**, glow in **infrared light**, which has [[#Energy|lower frequency]] than visible light. This glow can be observed with a thermal/infrared camera.

![[Screenshot 2026-01-30 at 3.28.22 AM.png|350]]<span style="display:inline-block;width:100%;text-align:center;font-style:italic;">azooptics.com</span>

Higher temperature indicates **higher energy**. Therefore, in the visible light spectrum:
- Redder objects (yellow/orange/red) are **hotter/brighter**
- Bluer objects (blue/purple) are **cooler/dimmer**

![[chart24A.png|650]]

### Blackbody radiation
Radiation that comes from **the glowing of an object** by itself, not reflected or transmitted light.

All objects reflect, transmit, and **emit** radiation.

The Blackbody Spectrum describes the light wavelengths that each temperature emit on its own.

![[Screenshot 2026-01-30 at 3.59.05 AM.png|500]]

The Sun's surface temperature is $\approx 5,500 \text{ K}$ (the top line). The intensity shows that it emits strongly across all visible light colours, which is why the Sun appears white to us.


### Origin of Light
In an **atom**, electrons orbit around the atom's nucleus. The **Bohr Model** describes these electrons as being in different levels of **energy orbitals**.

![[chart25A.png|400]]

Electrons on the lowest energy orbital are in a **ground state**, where electrons on higher energy orbitals are in **excited states**. 
Excited state electrons are **less stable**, as they want to return to their ground state.

Electrons are much like **waves**, the higher energy ones have **higher frequency**.

When an excited state electron **transitions** and drops down to a lower state, due to the *Conservation of Energy*, it releases a particle with the energy that it lost.

![[chart26A.png|500]]

This released particle is called a **photon**, which is light.

Therefore, an excited state electron is the source of light. There are two ways to get an electron excited:
- **Photo-excitation**: *provide* the electron with sufficient photon, so that it goes up to an excited state. Inverse of the process described above.
- **Thermal excitation**: higher object temperature causes more **motion / vibration** of the atoms. Moving atoms can *bump* them into excited states, where they would emit light as they come back down.


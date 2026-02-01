Lecture 6

## Parallax
- Measuring distance using **Triangulation**
- Use at least **2+ viewpoints**

An object's position can **appear to shift**, based on the change in the observer's viewpoint.

For example, if we hold out a thumb, close the left eye, then the right eye. The thumb will appear to be in a "***different position***" relative to the background.

![[Screenshot 2026-01-22 at 1.57.44 PM.png|300]]<span style="display:inline-block;width:100%;text-align:center;font-style:italic;">mathisfun.com</span>

The length that the thumb *shifts* can be used to measure **how far** the object is. Drawing out the sightline, we get:

![[chart12A.png|600]]

Notice that the two created triangles are **similar triangles**. This means that the distance between the observer and thumb is **a ratio** of the distance between the thumb and the car.

We can use the known values:
- how much the thumb has shifted
- how far the thumb is from the eyes
to solve for the distance to the car.

![[chart13A.png|630]]

### Generalizing
We can extend this idea to measure the distance to stars. Here, instead of using the distance between two eyes (*baseline*), we can use different **locations of Earth** as it orbits around the Sun.

We can observe the location of the star as it appears on Earth, then **wait half a year** (Earth on the other side of the Sun), then observe again.

![[chart14A.png|500]]

We know that the distance between Earth and Sun is 1 [[2_Scientific Notation#Astronomical Unit|Astronomical Unit]].

We can measure the change in angle (labelled $p$), and calculate the distance to the star (labelled $D$).

![[chart15A.png|500]]

Using trigonometry, we have that:
$$
\tan\theta=\dfrac{\text{opposite}}{\text{adjacent}}
$$
Substituting:
$$
\tan p=\dfrac{1\text{ AU}}{D}
$$
We can take $\tan p \approx p$ since $p$ typically gets very very small (less than an [[3_Celestial Sphere#Angular size|arcsecond]]).
$$
p=\dfrac{1\text{ AU}}{D}
$$
It follows that:
$$
D=\dfrac{1\text{ AU}}{p}
$$
Here, we can take $p$ in arcseconds and keep the $\text{AU}$ unit. We get:
$$
\begin{align}
D=\dfrac{1}{p} &  & D\text{ is in AU/arcseconds}
\end{align}
$$

### Parsec
The $\text{AU/arcseconds}$ is a unit called **Parsec** ($\text{pc}$), used in astronomy for very far distances.
 - Parsec is short for *Parallax of 1 arcsecond*
 - "Light-year" is a unit used to speak to non-astronomers
$$
1\text{ pc}=3.26\text{ light years}
$$

Larger forms of Parsec
- $1\text{ kpc}$ (kiloparsec) $=1,000\text{ pc}$
- $1\text{ Mpc}$ (megaparsec) $=1,000 \text{ kpc}$ 

The $\text{pc}$, $\text{kpc}$, and $\text{Mpc}$ are **standard units of distance** in astronomy.


> [!warning] Not parsec
> The parallax formula, if $D$ is not in parsec (could be in metres), or $p$ is not in arcseconds, then the formula is:
> $$D=\dfrac{C}{p}$$


### Measuring parallax
The nearest star to Earth after the Sun (*Alpha Centauri*) is $\approx 1.3\text{ pc}$ away. Therefore, it has a parallax of:
$$
D=\dfrac{1}{p}\implies 1.3=\dfrac{1}{p}\implies p=0.8^{"}
$$
Recall that the human eye can [[3_Celestial Sphere#Angular size|only resolve]] up to $1'=60^{"}$, **insufficient** for $0.8^{"}$

Moreover, the atmosphere of Earth can cause stars to **twinkle** and **jump** by a few arcseconds. To accurately measure, we need to go above the atmosphere with very accurate instruments.
- **Hipparcos satellite** (1989-1993): accuracy $\pm0.01^{"}\text{ to }0.03^{"}$, out to $100\text{ pc}$
- **Gaia Mission** (2013-2022): accuracy $\pm 10^{-6\text{ }"}$, out to $10\text{ kpc}$


Chapter 3.3


## Geometrical Transformations
- a [[3_Functions and Mappings#Standard matrix|standard]] [[1_Matrix#Square matrices|square]] matrix can be used to **transform** vectors by:
	- **rotating** (*length preserving*)
	- **scaling** (not *length preserving*)
	- **reflecting** (*length preserving*)
- a geometrical transformation is a **linear operation** (see [[3_Functions and Mappings#Linear mappings|linear mappings]])

### Coming up with matrices
To **create** a standard matrix for geometrical transformation:
- Similar to [[3_Functions and Mappings#Standard Matrix Example|creating a standard matrix]] for linear mappings, **transform using** the [[3_Functions and Mappings#Standard Basis Vectors|standard basis vectors]] separately
- In 2 dimensions, $\vec{v}=\begin{bmatrix}x\\y\end{bmatrix}$, therefore:
	- $e_{1}=\begin{bmatrix}1\\0\end{bmatrix}$ (a vector pointing directly to the right for 1 unit)
	- $e_{2}=\begin{bmatrix}0\\1\end{bmatrix}$ (a vector pointing directly up for 1 unit)
- For example, to reflect the vector over the y-axis, reflect each $e_{1}$, $e_{2}$ over the axis and copy the results into a matrix
 
| $e_{1}:\begin{bmatrix}1\\0\end{bmatrix}\to \begin{bmatrix}-1\\0\end{bmatrix}$ | $e_{2}:\begin{bmatrix}0\\1\end{bmatrix}\to \begin{bmatrix}0\\1\end{bmatrix}$ |
| ----------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| ![[IMG_0769.jpg\|250]]                                                        | ![[IMG_0770.jpg\|250]]                                                       |

- Therefore, the standard matrix for this reflection is $\begin{bmatrix}-1&0\\0&1\end{bmatrix}$

---
### Rotation about the origin
- rotate the vector by an angle $\theta$

| $e_{1}:\begin{bmatrix}1\\0\end{bmatrix}$                                                                  | $e_{2}:\begin{bmatrix}0\\1\end{bmatrix}$                                                                              |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| ![[IMG_097450022C06-1.jpeg\|250]]                                                                         | ![[IMG_7269F1E025F6-1.jpeg\|250]]                                                                                     |
| Use trigonometry to figure out $e_{1}'$                                                                   | Use trigonometry to figure out $e_{2}'$                                                                               |
| ![[IMG_55D7D2B8891A-1.jpeg\|250]]                                                                         | ![[IMG_96A4FD11C893-1.jpeg\|250]]                                                                                     |
| $\cos\theta=\dfrac{x}{1}$, $\sin\theta=\dfrac{y}{1}$                                                      | $\sin\theta=\dfrac{x}{1}$, $\cos \theta=\dfrac{x}{1}$                                                                 |
| Length of $x=\cos\theta$<br>Length of $y=\sin\theta$                                                      | Length of $x=\sin\theta$<br>Length of $y=\cos\theta$<br>However, $x$ is in the negative<br>Therefore, $x=-\sin\theta$ |
| $\therefore e_{1}:\begin{bmatrix}1\\0\end{bmatrix}\to \begin{bmatrix}\cos\theta\\\sin\theta\end{bmatrix}$ | $\therefore e_{2}:\begin{bmatrix}0\\1\end{bmatrix}\to \begin{bmatrix}-\sin\theta\\ \cos\theta\end{bmatrix}$           |

The rotation matrix is $\begin{bmatrix}\cos\theta&-\sin\theta\\ \sin\theta& \cos\theta\end{bmatrix}$ where
- $\theta$ is the angle of rotation


---
### Stretching
- stretch or shrink vectors [[1_Vectors#Scalar multiplication|by scalar]] quantities $s$, $t$

| $e_{1}:\begin{bmatrix}1\\0\end{bmatrix}\to \begin{bmatrix}s\\0\end{bmatrix}$ | $e_{2}:\begin{bmatrix}0\\1\end{bmatrix}\to \begin{bmatrix}0\\t\end{bmatrix}$ |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| ![[IMG_045096D58CCC-1.jpeg\|250]]                                            | ![[IMG_3AFD01A6A0A0-1.jpeg\|250]]                                            |

The stretching matrix is $\begin{bmatrix}s&0\\0&t\end{bmatrix}$ where
- $s$ is how much to stretch horizontally
- $t$ is how much to stretch vertically


---
### Horizontal Shear
- imagine applying a force to the side of a box near the top

![[IMG_1B18E7DB5EC9-1.jpeg|500]]

Notice that
- the bottom part doesn't change
- the height of the shape doesn't change

| $e_{1}:\begin{bmatrix}1\\0\end{bmatrix}\to \begin{bmatrix}1\\0\end{bmatrix}$ | $e_{2}:\begin{bmatrix}0\\1\end{bmatrix}\to \begin{bmatrix}s\\1\end{bmatrix}$ |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| ![[IMG_4808DFDC8AB6-1.jpeg\|250]]                                            | ![[IMG_555E633484CE-1.jpeg\|250]]                                            |

The horizontal shear matrix is $\begin{bmatrix}1&s\\0&1\end{bmatrix}$ where
- $s$ is how much to shear horizontally


### Vertical Shear
- similar to [[#Horizontal Shear]], different direction

![[IMG_299D126540E6-1.jpeg|500]]

Notice that
- the left part doesn't change
- the width of the shape doesn't change

| $e_{1}:\begin{bmatrix}1\\0\end{bmatrix}\to \begin{bmatrix}1\\t\end{bmatrix}$ | $e_{2}:\begin{bmatrix}0\\1\end{bmatrix}\to \begin{bmatrix}0\\1\end{bmatrix}$ |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| ![[IMG_57DE7CC83F00-1.jpeg\|250]]                                            | ![[IMG_0770.jpg\|250]]                                                       |

The vertical shear matrix is $\begin{bmatrix}1&0\\t&1\end{bmatrix}$ where
- $t$ is how much to shear vertically


### Shear both ways
- combining the standard matrices for [[#Horizontal Shear]] and [[#Vertical Shear]]

The shear matrix is $\begin{bmatrix}1&s\\t&1\end{bmatrix}$ where
- $s$ is how much to shear horizontally
- $t$ is how much to shear vertically


---
### Reflection over the x-axis
| $e_{1}:\begin{bmatrix}1\\0\end{bmatrix}\to \begin{bmatrix}1\\0\end{bmatrix}$ | $e_{2}:\begin{bmatrix}0\\1\end{bmatrix}\to \begin{bmatrix}0\\-1\end{bmatrix}$ |
| ---------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| ![[IMG_4808DFDC8AB6-1.jpeg\|250]]                                            | ![[IMG_FD5505AF0524-1.jpeg\|250]]                                             |

The standard matrix for this reflection is $\begin{bmatrix}1&0\\0&-1\end{bmatrix}$


### Reflection over the y-axis
| $e_{1}:\begin{bmatrix}1\\0\end{bmatrix}\to \begin{bmatrix}-1\\0\end{bmatrix}$ | $e_{2}:\begin{bmatrix}0\\1\end{bmatrix}\to \begin{bmatrix}0\\1\end{bmatrix}$ |
| ----------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| ![[IMG_0769.jpg\|250]]                                                        | ![[IMG_0770.jpg\|250]]                                                       |

The standard matrix for this reflection is $\begin{bmatrix}-1&0\\0&1\end{bmatrix}$


### Reflection over y=x
| $e_{1}:\begin{bmatrix}1\\0\end{bmatrix}\to \begin{bmatrix}0\\1\end{bmatrix}$ | $e_{2}:\begin{bmatrix}0\\1\end{bmatrix}\to \begin{bmatrix}1\\0\end{bmatrix}$ |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| ![[IMG_19040DEA0E08-1.jpeg\|250]]                                            | ![[IMG_45E285796F1E-1.jpeg\|250]]                                            |

The standard matrix for this reflection is $\begin{bmatrix}0&1\\1&0\end{bmatrix}$


### Reflection over a given line through origin

Think of the **green line** as the axis of reflection:
![[IMG_7BA661D6074C-1.jpeg|250]]

The **shortest straight line** from the end of $\vec{v}$ to the line is found through the [[5_Projections#Orthogonal Projections|projection]] of $\vec{v}$ onto the green line.
![[IMG_B0BA38289841-1.jpeg|400]]

Notice that $\text{perp}_{l}\vec{v}$ is exactly half the distance from $\vec{v}$ to $\vec{v}'$

![[IMG_A52208C65298-1.jpeg|300]]

Therefore, $\vec{v}'$ is the [[3_Length and Angles#Distance examples|vector connecting]] the ends of $\vec{v}$ and $2\text{perp}_{l}\vec{v}$
$\implies \vec{v}'=\vec{v}-2\text{perp}_{l}\vec{v}$

Using this algorithm:
- we create a standard matrix by plugging in $e_{1}$ and $e_{2}$
- reflect over a general line through origin $\begin{bmatrix}s\\t\end{bmatrix}$

| $e_{1}:\begin{bmatrix}1\\0\end{bmatrix}$                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | $e_{2}:\begin{bmatrix}0\\1\end{bmatrix}$                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![[IMG_22D77C7F08D3-1.jpeg\|250]]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | ![[IMG_2BC81466AD79-1.jpeg\|250]]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| $e_{1}'=e_{1}-2\text{perp}_{l}e_{1}$                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | $e_{2}'=e_{2}-2\text{perp}_{l}e_{2}$                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| $\text{perp}_{l}e_{1}=e_{1}-\text{proj}_{l}e_{1}$<br><br>$=e_{1}-\dfrac{e_{1}\cdot l}{\lVert l \rVert^{2}}l$<br><br>$=\begin{bmatrix}1\\0\end{bmatrix}-\dfrac{\begin{bmatrix}1\\0\end{bmatrix}\cdot \begin{bmatrix}s\\t\end{bmatrix}}{\lVert \begin{bmatrix}s\\t\end{bmatrix} \rVert^{2}}\begin{bmatrix}s\\t\end{bmatrix}$<br><br>$=\begin{bmatrix}1\\0\end{bmatrix}-\dfrac{s}{s^{2}+t^{2}}\begin{bmatrix}s\\t\end{bmatrix}$<br><br>$=\begin{bmatrix}1-\dfrac{s^{2}}{s^{2}+t^{2}}\\-\dfrac{st}{s^{2}+t^{2}}\end{bmatrix}$ | $\text{perp}_{l}e_{2}=e_{2}-\text{proj}_{l}e_{2}$<br><br>$=e_{2}-\dfrac{e_{2}\cdot l}{\lVert l \rVert^{2}}l$<br><br>$=\begin{bmatrix}0\\1\end{bmatrix}-\dfrac{\begin{bmatrix}0\\1\end{bmatrix}\cdot \begin{bmatrix}s\\t\end{bmatrix}}{\lVert \begin{bmatrix}s\\t\end{bmatrix} \rVert^{2}}\begin{bmatrix}s\\t\end{bmatrix}$<br><br>$=\begin{bmatrix}0\\1\end{bmatrix}-\dfrac{t}{s^{2}+t^{2}}\begin{bmatrix}s\\t\end{bmatrix}$<br><br>$=\begin{bmatrix}-\dfrac{st}{s^{2}+t^{2}}\\1-\dfrac{t^{2}}{s^{2}+t^{2}}\end{bmatrix}$ |
| $e_{1}'=\begin{bmatrix}1\\0\end{bmatrix}-2\begin{bmatrix}1-\dfrac{s^{2}}{s^{2}+t^{2}}\\-\dfrac{st}{s^{2}+t^{2}}\end{bmatrix}$<br><br>$=\begin{bmatrix}1\\0\end{bmatrix}-\begin{bmatrix}2-\dfrac{2s^{2}}{s^{2}+t^{2}}\\-\dfrac{2st}{s^{2}+t^{2}}\end{bmatrix}$<br><br>$=\begin{bmatrix}-1+\dfrac{2s^{2}}{s^{2}+t^{2}}\\\dfrac{2st}{s^{2}+t^{2}}\end{bmatrix}$<br><br>Factor out the common denominator<br>$=\dfrac{1}{s^{2}+t^{2}}\begin{bmatrix}s^{2}-t^{2}\\2st\end{bmatrix}$                                            | $e_{2}'=\begin{bmatrix}0\\1\end{bmatrix}-2\begin{bmatrix}-\dfrac{st}{s^{2}+t^{2}}\\1-\dfrac{t^{2}}{s^{2}+t^{2}}\end{bmatrix}$<br><br>$=\begin{bmatrix}0\\1\end{bmatrix}-\begin{bmatrix}-\dfrac{2st}{s^{2}+t^{2}}\\2-\dfrac{2t^{2}}{s^{2}+t^{2}}\end{bmatrix}$<br><br>$=\begin{bmatrix}\dfrac{2st}{s^{2}+t^{2}}\\-1+\dfrac{2t^{2}}{s^{2}+t^{2}}\end{bmatrix}$<br><br>Factor out the common denominator<br>$=\dfrac{1}{s^{2}+t^{2}}\begin{bmatrix}2st\\t^{2}-s^{2}\end{bmatrix}$                                            |
| $\therefore e_{1}:\begin{bmatrix}1\\0\end{bmatrix}\to\dfrac{1}{s^{2}+t^{2}}\begin{bmatrix}s^{2}-t^{2}\\2st\end{bmatrix}$                                                                                                                                                                                                                                                                                                                                                                                                  | $\therefore e_{2}:\begin{bmatrix}0\\1\end{bmatrix}\to\dfrac{1}{s^{2}+t^{2}}\begin{bmatrix}2st\\t^{2}-s^{2}\end{bmatrix}$                                                                                                                                                                                                                                                                                                                                                                                                  |

The standard matrix of this reflection is
$\dfrac{1}{s^{2}+t^{2}}\begin{bmatrix}s^{2}-t^{2}&2st\\2st&t^{2}-s^{2}\end{bmatrix}$

where:
- $\begin{bmatrix}s\\t\end{bmatrix}$ is the axis of reflection


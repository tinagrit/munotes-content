Lecture 8

## Tree Diagram

A visual tool to represent [[1_Conditional Probability#Conditional Probability|Conditional Probability]]. For example:

![[chart18.png|400]]

This diagram shows the pathing of $A$ and $B$ consequentially.

Terminologies:
![[chart19.png|440]]

- Each "circle" is a **node**, a starting point or a decision point
- Each "arrow" along with its related probability is a **branch**
- The **leaves** are the nodes without children, the final endpoints and unique outcomes

### Multiplying
Using the [[1_Conditional Probability#Multiplication rule|Multiplication rule]], the probability of each path is the **product** of each arrow in the path.

For example, finding the probability to rolling 2 $6$'s in a row on a 6-sided die:
![[chart20.png|400]]
To get the total probability of the path, we multiply the two arrow:
$$
\text{Pr}=\dfrac{1}{6}\times \dfrac{1}{6}=\dfrac{1}{36}
$$

### Adding
If there are two paths that lead to the same, using the [[3_Probability Rules#Union Bound|Union bound rule]], the probability is the **sum** of each path.

For example, blindly picking a ball out of a box with 2 greens and 2 reds. Finding the probability of picking one green and one red:

![[chart21.png|400]]

Here, getting a red then green, and a green then red, are identical. Therefore, there are two paths.

![[chart22.png|400]]

The yellow arrow: $\text{Pr}=\dfrac{2}{4}\times \dfrac{2}{3}=\dfrac{1}{3}$
The purple arrow: $\text{Pr}=\dfrac{2}{4}\times \dfrac{2}{3}=\dfrac{1}{3}$

Therefore, the probability of getting one green and one red is:
$$
\text{Pr}=\dfrac{1}{3}+ \dfrac{1}{3}=\dfrac{2}{3}
$$


---
## The Monty Hall Problem

Suppose there is a player on a game show with 3 doors, one of them is a car, and two are goats.

![[chart23.png|400]]

The host knows which door is the car. Once a player picks a door, the host opens a different door with a goat, then asks the player if they want to switch.

![[chart24.png|500]]

We can use the [[#Tree Diagram|Tree Diagram]] to map out each stage of these possibilities.

![[chart25.png|600]]

<span style="color: #E59EDD; background-color: #282A36">Where the car is</span> and <span style="color: #F6C6AD; background-color: #282A36">what the player chooses</span> are independent, since each of the 3 doors is likely to be chosen.

<span style="color: #83CBEB; background-color: #282A36">What the host reveals</span>, however, depends on both. 
- If the player's guess is <span style="color: white; background-color: #92D050">correct</span> (picks the car), there are 2 more goat doors, and the host picks either.
- If the player's guess is <span style="color: white; background-color: #C00000">incorrect</span> (picks the goat), there is only 1 more goat door, which the host will reveal.

The probability question is whether **the player should switch** after the goat being revealed.

These paths are cases where the player would **win by switching**:
![[chart26.png|400]]
Summing up the probability:
$$
\text{Pr}_{\text{switching}}=\left(\dfrac{1}{3}\times \dfrac{1}{3} \times 1\right) \times 6=\dfrac{2}{3}
$$

These paths are cases where the player would **win by not switching**:
![[chart27.png|400]]
Summing up the probability:
$$
\text{Pr}_{\text{staying}}=\left( \dfrac{1}{3}\times \dfrac{1}{3}\times \dfrac{1}{2} \right)\times 6 =\dfrac{1}{3}
$$

Therefore, a player has $\approx 66\%$ chances of winning by **switching the door** after a goat is revealed.


Lecture 1

## Statistics
The art of **learning from data**, used to evaluate observations and make decisions.

### History
Statistics, compared to mathematics, is relatively new.

At the start of the 19th century, science was focused on modelling **deterministic** systems to **discover formulas** and describe reality. 
- This idea is called a "*clockwork universe*"
- Example: Newton's laws of motion

This requires the inclusion of an **error function**, since accuracy cannot be 100%
- *human error*, *assumptions*, *imprecision in measurement*
- Instead of ignoring the small error value, modelling the error gives rise to **stochastic model** of reality (normal distribution, etc.)

### Types of statistics
1. **Descriptive statistics**: describe, organize, summarize, analyze data
2. **Inferential statistics**: interpretation, generalization, drawing conclusions, making decisions

### Population and data
Statistics is about obtaining information about **all individuals** (people, households, etc.). The set of all individuals is called the **population**. 

When the population is too large to study, a subgroup, **sample**, is studied. This sample should be **representative** of the population.
- Only representative if selected **at random**
- **Bias** introduced if not at random

![[chart01.png|400]]

For example,
> We are interested in the age distribution of people in Burnaby. If we record the ages of 20 people at SFU, and find the average age to be 30 years. Can we conclude that the average age of people in Burnaby to be 30?

**No**, the sample is biased.
We are only looking at people who go to SFU.

### Types of dataset
1. **Observational data**: collected without intervention or attempt to influence the observations, such as surveys
	- No causation conclusion statement (*Method A **tends to** give students higher grades than Method B*)

2. **Experimental data**: collected from an appropriately designed experiment.
	- Impose a treatment and study the effect
	- Experiment not always possible, ethical considerations (*Does smoking cause lung cancer?*)
	- Removes **lurking variables**, such as placebo effect
	- Causal conclusion (*Method A gives students higher grades than Method B*)


---
## Presenting Data
Collected data should be presented to reveal **important characteristics** of the data, including the location (centre), range, degree of concentration (spread), symmetry.

Tables and/or graphs can be used to **present data**, depending on the type of observation, and size of dataset.

### Frequency table
Present dataset with few distinct values
![[Screenshot 2026-05-14 at 11.43.33 AM.png|400]]

### Line graph and Bar graph
The distinct values are on the x-axis, while the frequency is on the y-axis. 
A line graph uses a line, and a bar graph uses a rectangle.

![[Screenshot 2026-05-14 at 11.44.00 AM.png|450]]

![[Screenshot 2026-05-14 at 11.44.20 AM.png|450]]

### Frequency polygon
A line graph with the frequencies connected to help visualize.

![[Screenshot 2026-05-14 at 11.44.42 AM.png|450]]

### Relative frequency
Proportion or percentage of frequency. The total should be 1, or 100%.

![[Screenshot 2026-05-14 at 11.45.05 AM.png|450]]

### Pie Chart
Shows the **relative frequency** when the data is not numerical. This is not preferred since humans are not good at comparing angles in a circle.

![[Screenshot 2026-05-14 at 11.46.47 AM.png|350]]


---
## Grouped data
If the dataset contains a **large number** of specific distinct values, we can group them into intervals.

When choosing class intervals:
- **Too few** classes, we lose relevant information
- **Too many** classes, frequencies are too low and it is difficult to identify patterns
- Often equal length, but unequal length can be used

The boundary is often $[a,b)_{}$, including the left but not including the right.

### Class frequency table

![[Screenshot 2026-05-14 at 11.49.20 AM.png|450]]

### Histogram
Displays the distribution of a grouped dataset. It is a **bar graph** with the bars **adjacent** to each other.

![[Screenshot 2026-05-14 at 11.59.27 AM.png|450]]

A **relative frequency histogram** will show the relative frequency on the y-axis, which will not change the shape.

### Stem-and-Leaf plot
Displays small to moderate-sized dataset. Each value is divided into a stem and a leaf.

For example, displaying:
$$
24,25,31,33,34,34,36,38,39,42,44,47,51,58,63
$$
We get:
$$
\begin{align}
2 &  \quad 4,5 \\
3 &  \quad 1,3,4,4,6,8,9 \\
4 &  \quad 2,4,7 \\
5 &  \quad 1,8 \\
6 &  \quad 3
\end{align}
$$

### Ogive
Pronounced *oh-jive* is a **cumulative** frequency plot. It plots the proportion of values $\leq$ to each value on the x-axis. The line must be **non-decreasing**.

![[Screenshot 2026-05-14 at 12.03.24 PM.png|450]]

This means that $\approx 22\%$ of lamps had lifetime $\leq 900$ hours.


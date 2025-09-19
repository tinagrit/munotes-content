## Basic counting of things
- basis of computing probabilities of discrete *(individual)* events
	"What is the probability of winning the lottery?"

### Examples

>"If you choose a sport car, you have the choice of six models. If you choose a van, you have a choice of four models. How many different choices do you have?"
- choosing one choice from a group of things
- [[#The Sum Rule]]
- 6 choices of car + 4 choices of van = 10 choices in total

>"As the buyer, you will need to choose from four different exterior colours (white, red, indigo blue, and ocean green) and three different interior colours (white, tan, and grey.) How many different colour combinations are possible?"
- 4 exterior choices ***matching*** with 3 interior choices
- making one choice and another one ***after*** that
- "successive tasks"
- [[#The Product Rule]]
- $4  *3 = 12$ in total

>"You may choose between a sports car (6 models) and a van (4 models) with the interior and exterior choices of problem two. How many different combinations are possible for you to choose from?"
- 10 choices of models ***matching*** with 12 choices of colours
- [[#The Product Rule]]
- $10 *12 = 120$ in total

---

## The Sum Rule

When two tasks ***CANNOT*** be performed simultaneously, performing either task can be done in any of $n_1+n_2$ ways.

>"The department will award a free computer to either a CS student or a CS professor. How many different choices are there, if there are 530 students and 15 professors?"
- only one person out of everyone gets the award
- $530 + 15 = 545$

>"A student can choose one computer project from one of three lists. The three lists contain 23, 15 and 19 possible choices. How many possible projects are there to choose from?"
- adding all options due to not being able to choose one from list 1 then one from list 2
- $23+15+19 = 57$

---

## The Product Rule

Procedure being broken down into two ***successive*** tasks, one after the other. If there are $n_1$ ways to do one task and $n_2$ ways to do the other task **AFTER** the first task, there are $n_1 * n_2$ ways to do the procedure.

If we have a procedure consisting of sequential tasks $T_1, T_2, ..., T_m$ that can be done in $n_1, n_2, ..., n_m$ ways, respectively, then there are $n_1  *n_2  *...*n_m$ ways to carry out the procedure

>"How many different license plates are there that contain exactly three English letters ?"
- choose a letter for the first letter, then choose a letter for the second letter, then choose a letter for the third letter
- numbers could be included if the question is asking "in general" instead of "English letters"
- Procedure
	- 26 character choices for the first letter
	- 26 character choices for the second letter *(duplicates allowed)*
	- 26 character choices for the third letter
- $26 * 26 * 26 = 17,576$ different combinations

>"The chairs of an auditorium are to be labeled with a letter and a positive integer not exceeding 100. For example, A23 would be one chair label. What is the largest number of chairs that can be labeled differently?"
- (letter) + (number)
- choose a letter, **THEN** a number (*successive task*s)
- Procedure
	- 26 character choices for the first letter
	- 100 integer choices for the number
- $26 * 100 = 2,600$ different combinations


---

## Inclusion-Exclusion examples

>"How many bit strings of length 8 either start with a 1 or end with 00?"
- **Task 1:** Construct a string of length 8 that starts with a 1
	- Procedure
		- 1 choice for the first bit (*it has to be 1*)
		- 2 choices for the bits 2-8 (*zero or one*)
	- Using [[#The Product Rule]]
	- $1*2^7=128$ different combinations for task 1
- **Task 2:** Construct a string of length 8 that ends with 00
	- Procedure
		- 2 choices for the bits 1-6
		- 1 choice for the bits 7-8 (*they have to be 0*)
	- Using [[#The Product Rule]]
	- $2^6*1^2=64$ different combinations for task 2
- Total combinations: sum rule will **NOT** work since there are bit strings that both start with 1 and end with 00. Therefore, task 1 and 2 can be done *at the same time*
- To use the sum rule, we must **subtract** the cases where task 1 and task 2 are done simultaneously
- "How many strings start with 1 ***AND*** end with 00?"
	- Procedure
		- 1 choice for the first bit (1)
		- 2 choices for the bits 2-6
		- 1 choice for the bits 7-8 (0)
	- Using [[#The Product Rule]]
	- $1*2^5*1=32$ strings that satisfy **both** task 1 and task 2
- Using [[#The Sum Rule]]
- There are $128+64-32=160$ ways to do either task

If two tasks can be done simultaneously, the sum rule cannot be used unless it is adjusted.

---


## Using Tree Diagrams

>"How many bit strings of length four do not have two consecutive 1s?"

Draw out possibilities after each task into a tree diagram. The counts of the last task will be the total combinations.

![[tree diagram.png]]

- There are 8 ways
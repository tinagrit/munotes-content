Sections 4.1-4.14

## Game theory
*Game theory* studies how **people make decisions** when their outcome depends on
- their **own** choices    
- the choices of **other people**

Used when people are **strategically interacting**. Before choosing an action, you have to think about what _**someone else might do**_.
  
A **game** usually contains
- players
- strategies    
- payoffs    
- rules / institutions

### Players
- The people / firms / countries making decisions
- Can have
    - conflicting interests    
    - common interests    
    - or a mixture of both    

> _Example_: Two competing coffee shops deciding whether to lower their prices.

### Strategies
- **Action or plan** a player can choose
- Each player usually has multiple possible strategies

> _Example_: A firm can keep its price high or lower its price

### Payoffs
- A payoff represents **how good an outcome is** for a player, can represent:
    - money
    - utility
    - profit
    - happiness
    - votes
    - any other benefit

> Players generally choose strategies that give them the _**highest payoff**_.


---
## Simultaneous games

- Make decisions **without knowing** what the other player chooses
- Doesn't mean they literally act at the same second

> _Example_: Two firms independently deciding whether to advertise.

### Payoff matrix
Suppose two firms, **A** and **B**, can either advertise or not advertise.

| A \ B               | Advertise         | Don't advertise   |
| ------------------- | ----------------- | ----------------- |
| **Advertise**       | $5 \backslash 5$  | $10 \backslash 2$ |
| **Don't advertise** | $2 \backslash 10$ | $8 \backslash 8$  |

- First number = payoff for **Firm A**
- Second number = payoff for **Firm B**

---
## Best response

- A best response is the strategy that gives a player the _**highest payoff given what the other player does**_

Using the advertising game:
- **If Firm B advertises**
	- Firm A gets **5** by advertising
	- Firm A gets **2** by not advertising
$\therefore$ A's best response is to **advertise**

- **If Firm B doesn't advertise**
	- Firm A gets **10** by advertising
	- Firm A gets **8** by not advertising
$\therefore$ A's best response is still to **advertise**


### Dominant strategy
- A dominant strategy is a player's best strategy _**regardless of what the other player chooses**_

In the advertising example,
- if B advertises → A wants to **advertise**
- if B doesn't advertise → A still wants to **advertise**

Therefore
- **advertise** is A's dominant strategy
- **advertise** is also B's dominant strategy


---
## Nash equilibrium
- A Nash equilibrium occurs when every player is playing their **best response** to the other players
- At a Nash equilibrium, _**no player wants to change their strategy**_

For the advertising game:

| A \ B               | Advertise | Don't advertise |
| ------------------- | --------- | --------------- |
| **Advertise**       | **5 \ 5** | 10 \ 2          |
| **Don't advertise** | 2 \ 10    | 8 \ 8           |

The Nash equilibrium is **Advertise, Advertise**

because
- given that B advertises, A does not want to change
- given that A advertises, B does not want to change

Both firms would actually prefer
**Don't advertise, Don't advertise → 8 \ 8**
but each firm individually has an incentive to advertise.

---
## Prisoner's dilemma
- A famous example where **individual self-interest** produces a **worse outcome** for everyone
- Each player has a dominant strategy
- The Nash equilibrium is _**not socially optimal**_

Two prisoners can either
- **stay silent**
- **confess**

|Prisoner A \ Prisoner B|Silent|Confess|
|---|---|---|
|**Silent**|-1 \ -1|-10 \ 0|
|**Confess**|0 \ -10|-5 \ -5|

Assume higher payoff = better.

For Prisoner A:
- If B stays silent
    - silent → -1
    - confess → 0
    - therefore **confess**
- If B confesses
    - silent → -10
    - confess → -5
    - therefore **confess**

$\therefore$ confess is A's **dominant strategy**

Same for B.

The Nash equilibrium is **Confess, Confess → -5 \ -5**

However, **Silent, Silent → -1 \ -1** would make _**both players better off**_.

> When everyone individually chooses what is best for themselves, they can collectively create a worse outcome.

This is a **social dilemma**.

---
## Social optimum
- The **social optimum** is the outcome that maximizes the _**total benefit**_ of everyone involved
- Does not have to equal the Nash equilibrium

In the prisoner's dilemma
- Nash equilibrium = **confess, confess**
- Social optimum = **silent, silent**

This creates a conflict between
- _individual incentives_
- _collective welfare_

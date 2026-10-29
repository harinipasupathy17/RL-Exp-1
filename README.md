# Representation-of-a-Real-World-Problem-as-a-Markov-Decision-Process


## Aim

To represent a Smart Parking System as a Markov Decision Process (MDP) by defining its states, actions, transition probabilities, rewards, and Python representation.

## Problem Statement
### Problem Description
A smart parking system helps drivers find a suitable parking space based on parking availability. The system observes the current parking condition and selects an action to reduce the time needed to park a vehicle. At each step, the system decides whether to park the vehicle, search for another parking space, or move to another parking area. The goal is to find a parking space quickly while minimizing waiting time and traffic congestion.


## MDP Components

A Markov Decision Process is represented as:

MDP = (S, A, P, R, gamma)

Where:

| Symbol | Meaning |
|---|---|
| S | Set of states |
| A | Set of actions |
| P | Transition probability function |
| R | Reward function |
|gamma | Discount factor |

---


## State Space

The state space represents the possible parking conditions of the Smart Parking System.

State space format:

```text
S = {
    0: "Available",
    1: "Limited",
    2: "Full"
}
```



---

## Sample State

A sample state is one specific example from the state space.

Limited (State 1): Only a few parking spaces are available in the parking area, so the system needs to search for an available space or move to another parking area.

---

## Action Space

The action space represents all possible actions available to the Smart Parking System.

Example format:

```text
A = {
    Action 1,
    Action 2,
    Action 3
}
```



## Sample Action
Park Vehicle

When a parking space is available, the system parks the vehicle in the available space. If the parking area is limited or full, the system searches for another space or moves to another parking area.

## Transition Probability
If the parking area is Available and the system chooses Park Vehicle, the parking condition changes to Limited with probability 0.8.

P(Limited | Available, Park Vehicle) = 0.8

If the parking area is Full and the system chooses Move Area, it reaches an Available parking area with probability 0.9.

P(Available | Full, Move Area) = 0.9

The transition probability explains how the parking condition changes from one state to another after an action is taken.

General form:

P(Next State | Current State, Action)


This means:

> Probability of reaching the next state after taking an action in the current state.

---

## Reward Function

```text
Successful Parking = +10
Finding a Parking Space Quickly = +5
Long Waiting / Searching = -2
Moving to Another Parking Area = -3
```
General form:


 R(s,a,s')

```
+10 – Vehicle successfully parked in an available parking space.
+5 – Parking space found quickly.
-2 – Time wasted searching for a parking space.
-3 – Moving to another parking area.
```



---

## Graphical Representation

<img width="1229" height="1280" alt="Smart Parking System MDP Graph" src="https://github.com/user-attachments/assets/9e70f3ad-c280-4367-a992-a2e8549abc6d" />

---

## Python Representation


```python
# MDP Representation using Python
# Smart Parking System

# States
# 0 = Available
# 1 = Limited
# 2 = Full

# Actions
# 0 = Park Vehicle
# 1 = Search Space
# 2 = Move Area

P = {
    0: {
        0: [(0.8, 1, 10, False),
            (0.2, 0, 5, False)],
        1: [(1.0, 0, -2, False)]
    },

    1: {
        1: [(0.7, 0, 5, False),
            (0.3, 2, -2, False)],
        2: [(1.0, 0, -3, False)]
    },

    2: {
        2: [(0.9, 0, -3, False),
            (0.1, 2, -2, False)]
    }
}

print("Smart Parking System MDP\n")

for state in P:
    print(f"{state}: ")
    print("  {")
    for action in P[state]:
        print(f"    {action}: {P[state][action]}")
    print("  }")
    print()

print("Name: Harini P")
print("Register Number: 212224230082")

```
---
## Output


<img width="497" height="355" alt="image" src="https://github.com/user-attachments/assets/569212d6-f463-4577-9f24-005fdae128e6" />


---

## Result

Thus, the Smart Parking System was successfully represented as a Markov Decision Process (MDP) using three states, three actions, transition probabilities, rewards, and a discount factor.


---

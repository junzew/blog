---
layout: post
title:  "Temporal Logic"
categories: verification
---

## Linear Temporal Logic (LTL)
* Linear time model
* Infinite sequences of states
* Operators:
    * $Fp$ (sometime p; eventually p; $\lozenge$) Variable p must become true in some future state
    * $Gp$ (always p; henceforce p; $\square$ ) At all future moments p is true
    * $Xp$ (nexttime p; $\bigcirc$) Variable p must be true in the next state
    * $p\; U\; q$ (p until q) Variable p must remain true up until the state where variable q becomes true, at which point p becomes unconstrained
        * Strong until vs. Weak until
* Combinations:
    * Infinitely Often $GFp$
        * Example: car will get gas in the future, but even after that the car will eventually need to get gas again
    * Eventually Forever $FGp$
        * From some point on in the future, p always holds

* Example:

    The traffic light will be green until it turns red at which point it will be red forever
    $(g\; U\; r) \wedge (r \rightarrow Gr)$
    
* Büchi automaton

## Computation Tree Logic (CTL)
* Introduced by Emerson & Clarke
* Branching time model, computation trees
* Quantified properties over paths
* Operators: $(E,A) \times (X, F, G, U)$
    * 8 operator pairs: $EX, EF, EG, EU, AX, AF, AG, AU$

* Example: 

    For all computations, if the traffic light is current yellow, for all paths the next state must be red 
    $AG(y \rightarrow AX r)$


### CTL*
* Full branching-time logic, more expressive than CTL
* Extends CTL by allowing basic temporal operators where the path quantifier ($A$ or $E$) is followed by an arbitrary linear-time formula allowing Boolean
combinations and nestings, over $F, G, X$, and $U$
* Kripke Structures


## Application 
### Verification and Model Checking
* Create guarantees about a system and formally verify it for properties
* Safety: system will never enter a state with a certain condition
    * mutual exclusion $AG(\neg crit_1 \vee \neg crit_2)$
* Maintenance: certain condition will always hold

### Puzzle solver
Create specification with a formula, then use model checker to solve the negation of the formula

## Tools
* NuSMV
* PDDL

## Links
[Model Checking Lectures](https://www.youtube.com/playlist?list=PLnbFC0ntxiqdpoWwMKCVh6BRwBePHaqQx)

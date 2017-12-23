## Problem 1. [24 points]
Translate the following sentences from English to predicate logic. The domain that you are
working over is X, the set of people. You may use the functions S(x), meaning that “x has
been a student of 6.042,” A(x), meaning that “x has gotten an ‘A’ in 6.042,” T(x), meaning
that “x is a TA of 6.042,” and E(x, y), meaning that “x and y are the same person.”


__(a) [6 pts].__ There are people who have taken 6.042 and have gotten A’s in 6.042

__(b) [6 pts].__ All people who are 6.042 TA’s and have taken 6.042 got A’s in 6.042

__(c) [6 pts].__ There are no people who are 6.042 TA’s who did not get A’s in 6.042.

__(d) [6 pts].__ There are at least three people who are TA’s in 6.042 and have not taken 6.042

#### Solution (a):
```
There are people who have taken 6.042 and have gotten A’s in 6.042

- There are people is ∃x ∈ X or ∃x,y ∈ X
- who have taken 6.042 is S(x) or S(x)∧S(y)
- and have gotten A’s in 6.042 is ∧A(x) or ∧A(x)∧A(y)

Result 1 (One Person). ∃x ∈ X : S(x)∧A(x) 
Result 2 (At Least 2 Persons). ∃x,y ∈ X : S(x)∧S(y)∧A(x)∧A(y)∧¬E(x,y) 
```

#### Solution (b):
```
All people who are 6.042 TA’s and have taken 6.042 got A’s in 6.042

- All people is ∀x ∈ X
- who are 6.042 TA’s is T(x)
- and have taken 6.042 is ∧S(x)
- got A’s in 6.042 is ⇒ A(x)

Result: ∀x ∈ X : T(x)∧S(x) ⇒ A(x) 
```

#### Solution (c):
```
There are no people who are 6.042 TA’s who did not get A’s in 6.042. 

- There are no people is ¬∀x ∈ X
- who are 6.042 TA’s is T(x)
- who did not get A’s in 6.042 is ¬A(x)

Result: ¬∃x ∈ X : T(x)∧(¬A(x)) 
```

#### Solution (d)
```
There are at least three people who are TA’s in 6.042 and have not taken 6.042

- There are at least three people is ∃x,y,z ∈ X : (¬E(x,y)¬E(x,z)¬E(y,z))
- who are TA’s in 6.042 is ∧T(x)∧T(y)∧T(z)
- and have not taken 6.042 is ∧¬S(x)∧¬S(y)∧¬S(z)

Result: ∃x,y,z ∈ X : (¬E(x,y)¬E(x,z)¬E(y,z))∧T(x)∧¬S(x)∧T(y)∧¬S(y)∧T(z)∧¬S(z) 
```

## Problem 2. [24 points]
Use a truth table to prove or disprove the following statements: 

__(a) [12pts].__ ¬(P ∨ (Q ∧ R)) = (¬P) ∧ (¬Q ∨¬R)

__(b) [12pts].__ ¬(P ∧ (Q ∨ R)) = ¬P ∨ (¬Q ∨¬R)

#### Solution (a)
```
                           LEFT                               RIGHT
P | Q | R | (Q ∧ R) | ¬(P ∨ (Q ∧ R)) | (¬P) | (¬Q ∨¬R) | (¬P) ∧ (¬Q ∨¬R) |
--|---|---|---------|----------------|------|----------|-----------------|
T | T | T |    T    |       F        |   F  |    F     |        F        |
T | T | F |    F    |       F        |   F  |    T     |        F        |
T | F | T |    F    |       F        |   F  |    T     |        F        |
T | F | F |    F    |       F        |   F  |    T     |        F        |
F | T | T |    T    |       F        |   T  |    F     |        F        |
F | T | F |    F    |       T        |   T  |    T     |        T        |
F | F | T |    F    |       T        |   T  |    T     |        T        |
F | F | F |    F    |       T        |   T  |    T     |        T        |

Conclusion: ¬(P ∨ (Q ∧ R)) and (¬P) ∧ (¬Q ∨¬R) is equivalent
```

#### Solution (b)
```
                           LEFT                            RIGHT
P | Q | R | (Q ∨ R) | ¬(P ∧ (Q ∨ R)) | (¬Q ∨¬R) | ¬P | ¬P ∨ (¬Q ∨¬R) |
--|---|---|---------|----------------|----------|----|---------------|
T | T | T |    T    |        F       |     F    |  F |       F       |
T | T | F |    T    |        F       |     T    |  F |       T       |
T | F | T |    T    |        F       |     T    |  F |       T       |
T | F | F |    F    |        T       |     T    |  F |       T       |
F | T | T |    T    |        T       |     F    |  T |       T       |
F | T | F |    T    |        T       |     T    |  T |       T       |
F | F | T |    T    |        T       |     T    |  T |       T       |
F | F | F |    F    |        T       |     T    |  T |       T       |

Conclusion: ¬(P ∧ (Q ∨ R)) = ¬P ∨ (¬Q ∨¬R) are no equivalent
```
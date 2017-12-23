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

-There are people is ∃x ∈ X or ∃x,y ∈ X
-who have taken 6.042 is S(x) or S(x)∧S(y)
-and have gotten A’s in 6.042 is ∧A(x) or ∧A(x)∧A(y)

Solution 1 (One Person). ∃x ∈ X : S(x)∧A(x)
Solution 2 (At Least 2 Persons). ∃x,y ∈ X : S(x)∧S(y)∧A(x)∧A(y)∧¬E(x,y)
```
## Problem 1. [24 points]
Translate the following sentences from English to predicate logic. The domain that you are
working over is X, the set of people. You may use the functions S(x), meaning that “x has
been a student of 6.042,” A(x), meaning that “x has gotten an ‘A’ in 6.042,” T(x), meaning
that “x is a TA of 6.042,” and E(x, y), meaning that “x and y are the same person.”


__(a) [6 pts].__ There are people who have taken 6.042 and have gotten A’s in 6.042<br/>
__(b) [6 pts].__ All people who are 6.042 TA’s and have taken 6.042 got A’s in 6.042<br/>
__(c) [6 pts].__ There are no people who are 6.042 TA’s who did not get A’s in 6.042.<br/>
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

__(a) [12pts].__ ¬(P ∨ (Q ∧ R)) = (¬P) ∧ (¬Q ∨¬R)<br/>
__(b) [12pts].__ ¬(P ∧ (Q ∨ R)) = ¬P ∨ (¬Q ∨¬R)

#### Solution (a)
```
                           LEFT                               RIGHT
 P | Q | R | (Q ∧ R) | ¬(P ∨ (Q ∧ R)) | (¬P) | (¬Q ∨¬R) | (¬P) ∧ (¬Q ∨¬R) 
---|---|---|---------|----------------|------|----------|-----------------
 T | T | T |    T    |       F        |   F  |    F     |        F        
 T | T | F |    F    |       F        |   F  |    T     |        F        
 T | F | T |    F    |       F        |   F  |    T     |        F        
 T | F | F |    F    |       F        |   F  |    T     |        F        
 F | T | T |    T    |       F        |   T  |    F     |        F        
 F | T | F |    F    |       T        |   T  |    T     |        T        
 F | F | T |    F    |       T        |   T  |    T     |        T        
 F | F | F |    F    |       T        |   T  |    T     |        T        

Conclusion: ¬(P ∨ (Q ∧ R)) and (¬P) ∧ (¬Q ∨¬R) is equivalent
```

#### Solution (b)
```
                           LEFT                            RIGHT
 P | Q | R | (Q ∨ R) | ¬(P ∧ (Q ∨ R)) | (¬Q ∨¬R) | ¬P | ¬P ∨ (¬Q ∨¬R) 
---|---|---|---------|----------------|----------|----|---------------
 T | T | T |    T    |        F       |     F    |  F |       F       
 T | T | F |    T    |        F       |     T    |  F |       T       
 T | F | T |    T    |        F       |     T    |  F |       T       
 T | F | F |    F    |        T       |     T    |  F |       T       
 F | T | T |    T    |        T       |     F    |  T |       T       
 F | T | F |    T    |        T       |     T    |  T |       T       
 F | F | T |    T    |        T       |     T    |  T |       T       
 F | F | F |    F    |        T       |     T    |  T |       T       

Conclusion: ¬(P ∧ (Q ∨ R)) = ¬P ∨ (¬Q ∨¬R) are no equivalent
```

## Problem 3. [24 points]
The binary logical connectives ∧ (and), ∨ (or), and (implies) appear often in not only ⇒computer programs, but also everyday speech. In computer chip designs, however, it is considerably easier to construct these out of another operation, nand, which is simpler to represent in a circuit. 

Here is the truth table for nand: 
```
 P | Q | P nand Q 
---|---|----------
 T | T |    F    
 T | F |    T
 F | T |    T
 F | F |    T
 ```

 __(a) [12 pts].__ For each of the following expressions, ﬁnd an equivalent expression using only nand and ¬(not), as well as grouping parentheses to specify the order in which the operations apply. You may use A, B, and the operators any number of times.

* __(i)__ A ∧ B <br/>
* __(ii)__ A ∨ B <br/>
* __(iii)__ A ⇒ B

__(b) [4 pts].__ It is actually possible to express each of the above using only nand, without needing to use ¬. Find an equivalent expression for (¬A) using only nand and grouping ¬paren theses. 

__(c) [8 pts].__ The constants true and false themselves may be expressed using only nand. Construct an expression using an arbitrary statement A and nand that evaluates to true regardless of whether A is true or false. Construct a second expression that always evaluates to false. Do not use the constants true and false themselves in your statements.

#### Solution (a)
```
  (i): A ∧ B = ¬(A nand B)
 (ii): A ∨ B = ¬¬(A ∨ B) = ¬(¬(A) ∧ ¬(B)) = (¬¬(A) ∨ ¬¬(B))
(iii): A ⇒ B = ¬(A ∧ ¬B) = (¬A ∨ B)
```

#### Solution (b)
```
(¬A) = (A nand A) = ((A nand A) and (A nand A))
```

#### Solution (c)
```
True construction: (A nand (A nand A))
False construction: ((A nand (A nand A)) nand (A nand (A nand A)))
```

## Problem 4. [10 points]
You have 12 coins and a balance scale, one of which is fake. All the real coins weigh the same, but the fake coin weighs less than the rest. All the coins visually appear the same, and the diﬀerence in weight is imperceptible to your senses. In at most 3 weighings, give a strategy that detects the fake coin. (Note: the scale in this problem is a scale with two dishes, which tips toward the side that is heavier. For clariﬁcation, do an image search for “balance scale”). 

#### Variant 1
```
All coins
(Weight=1) (Weight=1) (Weight=1) (Weight=1)
(Weight=1) (Weight=1) (Weight=1) (Weight=1)
(Weight=1) (Weight=1) (Weight=1) (Weight=1/2)

Let measuring first two sets.
(Weight=1) (Weight=1) (Weight=1) (Weight=1) = 4
(Weight=1) (Weight=1) (Weight=1) (Weight=1) = 4

Then we conclude that small coin is in last batch of coins,
therefore split it two by two and again on the scale.
(Weight=1) (Weight=1) = 2
(Weight=1) (Weight=1/2) = 1.5

Again the above trick.
(Weight=1) = 1
(Weight=1/2) = 0.5 <- here is the fake coin
```

#### Variant 2
```
All coins
(Weight=1) (Weight=1) (Weight=1) (Weight=1)
(Weight=1) (Weight=1) (Weight=1) (Weight=1)
(Weight=1) (Weight=1) (Weight=1) (Weight=1/2)

Let measuring first and last sets.
(Weight=1) (Weight=1) (Weight=1) (Weight=1) = 4
(Weight=1) (Weight=1) (Weight=1) (Weight=1/2) = 3.5

Then we conclude that small coin is in second batch of coins,
therefore split it two by two and again on the scale.
(Weight=1) (Weight=1) = 2
(Weight=1) (Weight=1/2) = 1.5

Again the above trick.
(Weight=1) = 1
(Weight=1/2) = 0.5 <- here is the fake coin
```

## Problem 5. [6 points]
Prove the following statement by proving its contrapositive: if r is irrational, then r¹/⁵ is irrational. (Be sure to state the contrapositive explicitly.) 

#### Solution
```
Contra: if r is rational then r¹/⁵ is rational.

r¹/⁵ = (a / b) ⇒ 
    r = (a⁵ / b⁵) ⇒
        r is rational ⇒ 
            if r is irrational, then r¹/⁵ is irrational.
```


## Problem 6. [12 points]
Suppose that w2 + x2 + y2 = z2, where w, x, y, and z always denote positive integers. (Hint: It may be helpful to represent even integers as 2i and odd integers as 2j + 1, where i and j are integers) 
Prove the proposition: z is even if and only if w, x, and y are even. Do this by considering all the cases of w,x,y being odd or even.

#### Solution
```
z is even if and only if w, x, and y are even. Do this by considering all the cases of w,x,y being odd or even.

Case 1: w,x,y = all even ⇒
    4w² + 4x² + 4y² = 4(w² + x² + y²) = z² is even
Case 2: w+1,x+1,y+1 = all odd ⇒ 
    4w² + 4x² + 4y² = 4(w² + x² + y²) = z² is odd
Case 3: x,y,y+1 = one odd ⇒
    4w² + 4x² + 4y² = 4(w² + x² + y²) = z² is odd
Case 4: x,y+1,y+1 = two odd ⇒ 
    4w² + 4x² + 4y² = 4(w² + x² + y²) = z² is odd

 w even | x even | y even | z even
--------|--------|--------|--------
 True   | True   | True   | True
 True   | True   | False  | False
 True   | False  | True   | False
 True   | False  | False  | False
 False  | True   | True   | False
 False  | True   | False  | False
 False  | False  | True   | False
 False  | False  | False  | False
```
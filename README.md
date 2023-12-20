# Turing Machine - No double 0's for the 1's

## Created a Turing Machine using YAML language to decide the language of 0's and 1's where the 0's are not equal to double the one's


### Template by  [Daniel Chahine](https://github.com/DanielChahine0)
<hr>

This Turing machine decides the language L(M)={0<sup>n</sup>1<sup>m</sup> | n ≠ 2m}

The Machine could be viewd using [THIS LINK](https://turingmachine.io/?import-gist=5dd4e91a321677a6ac9b6fbf105ed929)

## The machine is split into 3 parts:
> # 0 Reader
This part cross off the first 2 zeros in the tape. This allows us to know how many double zeros we have since we care about the number of 0's compared to the 1's.  

```
 q1:
    X: R
    Y: R
    1: {R: accept}
    0: {write: X, R: q2}
    ' ': {R: reject}
q2:
    0: {write: X, R: q3}
    1: {R: accept}
    ' ': {R: accept}
    X: {R: accept}
    Y: {R: accept}
 q3:
    0: R
    Y: R
    1: {write: Y, L: q4}
    ' ': {R: accept}
    X: R
```

<br>

> # 1 Reader
This part is right after the 0 reader. This allows us to cross off a single 1 after crossing off double 0's. After doing so it returns to the beginning to allows this method to be recursively called.

```  
q4:
    Y: L
    0: L
    X: L
    ' ': {R: q1}

```

<br>

> # Accept & Reject
Because this TM only rejects when the number of 0's is double the number of 1's we can just loop through the tape after crossing everything. If we reach an end we reject, if there's any 0's or 1's left we accept. For easier and simpler use, the transition are directed from the readers to the empty reject and accept states

```
reject:
    # Empty State

accept:
    # Empty State    
```

<br>
<hr>
<hr>

This is not supposed to be the **perfect solution** or the most efficient one, this is just **my way** of doing this challenge, feel free to improve my Turing Machine and play with its parameters.


```
Daniel Chahine
```
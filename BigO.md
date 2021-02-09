# Big O Notation Proof
For any polynomial time complexity

f(n) = a<sub>d</sub>n<sup>d</sup> + a<sub>d-1</sub>n<sup>d-1</sup> + ... + a<sub>0</sub>
<br>
Let c = |a<sub>d</sub>n<sup>d</sup>| + |a<sub>d-1</sub>n<sup>d-1</sup>| + ... + |a<sub>0</sub>|

Estimate d<sup>n-i</sup> to d<sup>n</sup> (Highest polynomial degree)

then f(n) = O(cn<sup>d</sup>)

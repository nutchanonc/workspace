# Big O Notation Proof
### For any polynomial time complexity

f(n) = a<sub>d</sub>n<sup>d</sup> + a<sub>d-1</sub>n<sup>d-1</sup> + ... + a<sub>0</sub>
<br>
Let c = |a<sub>d</sub>n<sup>d</sup>| + |a<sub>d-1</sub>n<sup>d-1</sup>| + ... + |a<sub>0</sub>|

Estimate d<sup>n-i</sup> to d<sup>n</sup> (Highest polynomial degree)

then f(n) = O(cn<sup>d</sup>)

### Prove that f(n) = O(g(n)), h(n) = O(g(n)) then f(n) + h(n) = (g(n)) 

f(n) <= c<sub>1</sub>g(n) while n >= n<sub>1</sub> and f(n) <= c<sub>2</sub>g(n) while n >= n<sub>2</sub><br>
  f(n) + h(n) <= c<sub>1</sub>g(n)+ c<sub>2</sub>g(n)  while  n >= max(n<sub>1</sub>,n<sub>2</sub>)

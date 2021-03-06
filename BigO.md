# Big O Notation Proof
### For any polynomial time complexity

f(n) = a<sub>d</sub>n<sup>d</sup> + a<sub>d-1</sub>n<sup>d-1</sup> + ... + a<sub>0</sub>
<br>
Let c = |a<sub>d</sub>n<sup>d</sup>| + |a<sub>d-1</sub>n<sup>d-1</sup>| + ... + |a<sub>0</sub>|

Estimate d<sup>n-i</sup> to d<sup>n</sup> (Highest polynomial degree)

then f(n) = O(cn<sup>d</sup>)

### Prove that f(n) = O(g(n)), h(n) = O(g(n)) then f(n) + h(n) = (g(n)) 

- f(n) <= c<sub>1</sub>g(n) while n >= n<sub>1</sub> and f(n) <= c<sub>2</sub>g(n) while n >= n<sub>2</sub><br>
- f(n) + h(n) <= c<sub>1</sub>g(n)+ c<sub>2</sub>g(n)  while  n >= max(n<sub>1</sub>,n<sub>2</sub>)
- f(n) + h(n) <= (c<sub>1</sub> + c<sub>2</sub>)g(n)
- give C = c<sub>1</sub> + c<sub>2</sub> and n<sub>0</sub> = max(n<sub>1</sub>,n<sub>2</sub>)
- f(n) + h(n) <= Cg(n) while n >= n<sub>0</sub>
- f(n) + h(n) = O(g(n))

### Transitivity
- give f(n) = O(g(n)) and g(n) = O(h(n)) then f(n) = O(h(n))


### Selection Sort
> input: n, Array A[1,2,3,4,...,n]
<br>

**Pseudo code**
```python
for i=1 to to n-1:      O(n-1)
  min = A[i]            O(1)
  minIndex = i          ^
  for j=i+1 to n:       O(n-i)
    if A[i] < min:        O(1)
      min = A[j]            O(1)
      minIndex = j          ^
  swap A[i] and A[j]    O(1)
```
Simple thinking : ( O(1) + O(n) + O(1) ) x (n-1) = O(n<sup>2</sup>) 


### Find Max
> input: A , n (size of Array)
```python
m = n
while m != 1:
  for i=1,2,3,...,m/2:
    B[i] = max(A[2i-1],A[2i])
  for i=1,2,3,...,m/2:
    A[i] = B[i]
  m = m/2
```
Rough calculating: O(n) x ( O(n) + O(n) + O(1)) = O(n<sup>2</sup>)
Presice calculating: 
> c(n) + c(n/2) + c(n+4) + c(n+8) + ... + c<br>
c n [1 + 1/2 + 1/4 + ... + 1/n]  (Geometric series => always smaller than 2)<br>
So: 2cn = O(n)    // Better !

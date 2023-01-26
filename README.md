# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
```
import numpy as np
def QR_Decomposition(A):
    n, m = A.shape # get the shape of A
    Q = np.empty((n, n)) # initialize matrix Q
    u = np.empty((n, n)) # initialize matrix u
    u[:, 0] = A[:, 0]
    Q[:, 0] = u[:, 0] / np.linalg.norm(u[:, 0])
    for i in range(1, n):
        u[:, i] = A[:, i]
        for j in range(i):
            u[:, i] -= (A[:, i] @ Q[:, j]) * Q[:, j] # get each u vector
        Q[:, i] = u[:, i] / np.linalg.norm(u[:, i]) # compute each e vector
    R = np.zeros((n, m))
    for i in range(n):
        for j in range(i, m):
            R[i, j] = A[:, j] @ Q[:, i]
    print(Q)
    print(R)
a = np.array(eval(input()))
QR_Decomposition(a)






```

## Output
```
![QR dec1](https://user-images.githubusercontent.com/121165938/214769750-c85fa43f-6541-4c33-a568-1c5719e842b3.png)
![QR dec2](https://user-images.githubusercontent.com/121165938/214769782-f7758783-5fcf-481f-a63c-4fcdf6a4b961.png)


```

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.

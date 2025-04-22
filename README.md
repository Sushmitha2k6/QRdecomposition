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


''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: SUSHMITHA S
RegisterNumber: 212224230282
'''
import numpy as np
def QR_Decomposition(A):
    n, m = A.shape
    Q = np.empty((n,m))
    u = np.empty((n,m))
    u[:, 0] = A[:, 0]
    Q[:, 0] = u[:, 0]/np.linalg.norm(u[:, 0])
    for i in range(1, m):
         u[:, i] = A[:, i]
         for j in range(i):
            u[:, i]-=(A[:, i]@ Q[:,j]* Q[:, j])
            Q[:, i] = u[:, i]/np.linalg.norm(u[:, i])
    R = Q.T @ A
    Q=np.where(np.isclose(Q,0), 0, Q)
    R=np.where(np.isclose(R,0), 0, R)
    print("The Q Matrix is")
    print(" " + np.array2string(np.round(Q, 8),separator=' '))
    
    print("The R Matrix is")
    print(" " + np.array2string(np.round(R, 8),separator=' '))
a=np.array(eval(input()))
QR_Decomposition(a)




```

## Output
```
![image](https://github.com/user-attachments/assets/20f60424-26e2-4ac7-a582-90e5371820da)



```

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.

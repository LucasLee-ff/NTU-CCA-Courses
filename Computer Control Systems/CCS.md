# 1. State Space Model (Continuous)

## 1.1 State Space Representation

$$
\begin{cases}
\overset{.}{X}(t) = AX(t) + BU(t)\\
Y(t) = CX(t) + DU(t)
\end{cases}
$$

## 1.2 Transfer Function

$$
TF = {Y(s)\over U(s)} = (C{[sI -A]}^{-1}B + D) = (C{adj[sI-A]B\over det[sI-A]}) + D
$$

## 1.3 Solution of X(t)

$$
X(t) = \Phi(t)X(0) + \gamma(t)
$$

$$
\begin{cases}
\gamma(t) = L^{-1}[[sI - A]^{-1}BU(s)]]\\
\Phi(t) = L^{-1}[[sI - A]^{-1}]
\end{cases}
$$

# 2. State Space Model (Discrete)

## 2.1 State Space Representation

$$
\begin{cases}
X(k+1) = AX(k) + BU(k)\\
Y(k) = CX(k) + DU(k)
\end{cases}
$$

## 2.2 Transfer Function

$$
TF = {Y(z)\over U(z)} = (C{[zI -A]}^{-1}B + D) = (C{adj[zI-A]B\over det[zI-A]}) + D
$$

## 2.3 Continuous -> Discrete

​    Given $\Phi(t)$, sampling period  $T$ ,

$$
X(k+1) = A_dX(k) + B_dU(k) = \Phi(T)X(k) + \Theta(T)U(k)
$$

$$
\begin{cases}\Phi(T) = A_d = L^{-1}[[sI - A]^{-1}]_{t=T}\\ 
\Theta(T) = B_d = \int_0^T\Phi(\tau)d\tau B\end{cases}
$$

$X(k) = X(t)_{t=kT} \Rightarrow$ Discrete-time system depend on the sampling period $T$. 

# 3. Poles and Zeros

## 3.1 Poles

1. Continuous: $det[sI-A]=0$  
2. Discrete: $det[zI-A]=0$  

## 3.2 Discrete Time Zeros:

$$
det\left[
\begin{matrix}
 zI-A & -B\\
 C & D
\end{matrix}
\right]=0  
$$

# 4. Solution of X(k)

​    Given $X(0)$ and $U(i)_{i=0,1,...,k-1}$, we can get $X(k)$ by **recursion**

$$
\begin{cases}
X(1)=AX(0)+BU(0)\\
X(2)=AX(0)+BU(0)\\
\cdots\\
X(k+1)=AX(k)+BU(k)
\end{cases}  
$$

$$
X(k)=A^kX(0)+\sum_{i=0}^{k-1}A^{(k-i-1)}BU(i)
$$

# 5. Similarity Transformation

​    Given a system $A, B, C, D$, and **linear transformation** $P$, $X(k) = PW(k) \rightarrow W(k) = P^{-1}X(k)$ , $W(k)$ is the **new state vector** with the state space model:

$$
\begin{cases}
W(k+1) = A_wW(k) + B_wU(k)\\
Y(k) = C_wW(k) + D_wU(k)
\end{cases}
$$

where,  

$$
\begin{cases}
A_w = P^{-1}AP\\
B_w = P^{-1}B\\
C_w = CP\\
D_w = D
\end{cases}
$$

$$
det[\lambda I - A_w] = det[\lambda I - A]
$$

# 6. Canonical Form

​    Given a system $A, B, C, D$ , $det[zI - A]=z^n + a_{n-1}z^{n-1} + ... + a_1z + a_0$

## 6.1 Controllable Canonical Form (CCF)

$$
W_c=\left[
\begin{matrix}
     B & AB & A^2B & \cdots & A^{n-1}B
\end{matrix}
\right]
$$

$$
\overset{\sim}{W}_c=\left[
\begin{matrix}
 B_c & A_cB_c & A_c^2B_c & \cdots & A_c^{n-1}B_c
\end{matrix}
\right]
$$

where,

$$
A_c=\left[
\begin{matrix}
 0 & 1 & 0 & 0 & \cdots & 0\\
 0 & 0 & 1 & 0 & \cdots & 0\\
 0 & 0 & 0 & 1 & \cdots & 0\\
 \vdots & \vdots & \vdots & \vdots & \ddots & \vdots\\
 0 & 0 & 0 & 0 & \cdots & 1\\
 -a_0 & -a_1 & -a_2 & -a_3 & \cdots & -a_{n-1}\\
\end{matrix}
\right]
$$

$$
B_c=\left[
\begin{matrix}
0\\
0\\
\vdots\\
0\\
1
\end{matrix}
\right]
$$

the transformation matrix $P$ to obtain the CCF is:

$$
P = W_c\overset{\sim}{W}_c^{-1}
$$

## 6.2 Observable Canonical Form (OCF)

$$
W_o=\left[
\begin{matrix}
C
\\
CA
\\
\vdots
\\
CA^{n-1}
\end{matrix}
\right]
$$

$$
\overset{\sim}{W}_o=\left[
\begin{matrix}
C_o
\\
C_oA_o
\\
\vdots
\\
C_oA^{n-1}_o
\end{matrix}
\right]
$$

where,

$$
A_o=\left[
\begin{matrix}
 0 & 0 & \cdots & 0 & -a_0\\
 1 & 0 & \cdots & 0 & -a_1\\
 0 & 1 & \cdots & 0 & -a_2\\
 \vdots & \vdots & \ddots & \vdots & \vdots\\
 0 & 0 & \cdots & 1 & -a_{n-1}\\
\end{matrix}
\right]
$$

$$
C_o=\left[
\begin{matrix}
 0 & 0 & \cdots & 0 & 1
\end{matrix}
\right]
$$

the transformation matrix $Q$ to obtain the OCF is:

$$
Q = W_o^{-1}\overset{\sim}{W}_o
$$

## 6.3 Canonical Form from Transfer Function

​    If the $TF$ $G(z)$ is in the following form:

$$
G(z) = {b_{n-1}z^{n-1} + \cdots + b_1z + b_0 \over z^n + \cdots + a_1z + a_0}
$$

$$
C_c = 
\left[
\begin{matrix}
b_0 & b_1 & \cdots & b_{n-2} & b_{n-1}
\end{matrix}
\right], \space
A_c, \space B_c\space from \space 6.1,\space
$$

OCF:

$$
B_o = 
\left[
\begin{matrix}
b_0 & b_1 & \cdots & b_{n-2} & b_{n-1}
\end{matrix}
\right],\space
A_o, \space C_o\space from \space 6.2,\space
$$

Since:

$$
TF = G(z) = {Y(z)\over U(z)} = C{[zI -A]}^{-1}B + D
$$

$D$ can be found directly in the $TF$ , or it is the remainder of the long division.

# 7. Controller Design

​    The state feedback controller and the observer can be designed separately.

## 7.1 State Feedback Controller

​    Assume that state vector $X(k)$ is available, design a Feedback controller $K$.

## 7.2 Observer

​    The real value of $X(k)$ may hard to be measured, an $Observer$ takes the system input and $U(k)$ and system output $Y(k)$ as input and give the estimation of state vector, denoted as $\overset{\sim}{X}(k)$.

# 8. Controllability

​    **Controllable** means a system can move from an initial state $X(0)$ to $X(k)$ with a series of input $U$.

​    Equation in 4. can also be denoted as:

$$
X(k) = A^kX(0) + W_cU
$$

$$
U = W_c^{-1}[X(k) - A^kX(0)]
$$

where:

$$
W_c=\left[
\begin{matrix}
     B & AB & A^2B & \cdots & A^{n-1}B
\end{matrix}
\right]
$$

$$
U=\left[
\begin{matrix}
     u(k-1) & u(k-2) & \cdots & u(0)
\end{matrix}
\right]^T
$$

If:

$$
rank(W_c) = n \Leftrightarrow \left|W_c\right| \neq 0
$$

then $W_c^{-1}$ exists, system $A,B$ is **controllable**.

# 9. Observability

​    **Observable** means a system's initial state $X(0)$ can be determined based on the knowledge of $Y$ and $U$.

​    Given a system:

$$
\begin{cases}
X(k+1) = AX(k)\\
Y(k) = CX(k)
\end{cases}
$$

since:

$$
\begin{cases}
Y(0) = CX(0)\\
Y(1) = CX(1) = CAX(0)\\
\cdots \\
Y(k-1) = CA^{k-1}X(0)
\end{cases}
$$

$$
Y = 
\left[
\begin{matrix}
y(0)\\
y(1)\\
\vdots\\
y(k-1)
\end{matrix}
\right] =
\left[
\begin{matrix}
C\\
CA\\
\vdots\\
CA^{k-1}
\end{matrix}
\right]
X(0)
= W_oX(0)
$$

then:

$$
X(0) = W_o^{-1}
\left[
\begin{matrix}
y(0)\\
y(1)\\
\vdots\\
y(k-1)
\end{matrix}
\right]
$$

if:

$$
rank(W_o) = n \Leftrightarrow \left|W_o\right| \neq 0
$$

then $W_o^{-1}$ exists, system $A,C$ is **observable**.

# 10. Controllability and Observability

​    **Controllability and observability depends on what are considered as input and output.**

## 10.1 Relations between Controllability, Observability and Transfer Function

1. $TF$ has pole-zero cancellation $\Rightarrow$ either uncontrollable, unobservable, or both.

2. $TF$ has no pole-zero cancellation $\Rightarrow$ can always represented as a controllable and observable system.

## 10.2 Loss of Controllability/Observability Due to Sampling

​    From 2.3, the discrete system matrices $A_d,\space B_d$ are related to the sampling period $T$. Therefore, $W_c$ and $W_o$ will be affected **due to the change of $T$**. So do controllability and observability.

# 11. State Feedback Design

    When reference input $r(k)=0$, the plant input $U(k)$:

$$
\begin{cases}
U(k) = -KX(k)\\
K = 
\left[
\begin{matrix}
k_1 & k_2 & \cdots & k_n
\end{matrix}
\right ]
\end{cases}
$$

the close-loop system:

$$
X(k+1) = [A - BK]X(k)
$$

$$
\alpha(z) = det[zI - A +BK]
$$

if the desired poles are $p_i = p_1, p_2, \cdots, p_n$,

$$
\alpha_c(z) = (z-p_1)(z-p_2)\cdots(z-p_n) = z^n +\beta_1z^{n-1} + \cdots + \beta_{n-1}z + \beta_n
$$

solution of $K$ can be obtained by solving the equation $\alpha(z) \equiv \alpha_c(z)$.

## 11.1 Zeros in State Feedback Control

    State feedback control **does not affect** the positions of zeros.



# 12.Ackermann's Formula

    Given the desired poles, the characteristic polynomial is:

$$
\alpha_c(z) = (z-p_1)(z-p_2)\cdots(z-p_n) = z^n +\beta_1z^{n-1} + \cdots + \beta_{n-1}z + \beta_n
$$

Ackermann's formula for the controller:

$$
K =
\left[
\begin{matrix}
0 & \cdots & 0 & 1
\end{matrix}
\right]
W_c^{-1}\alpha_c(A)
$$

$$
\alpha_c(A) = A^n +\beta_1A^{n-1} + \cdots + \beta_{n-1}A + \beta_nI
$$

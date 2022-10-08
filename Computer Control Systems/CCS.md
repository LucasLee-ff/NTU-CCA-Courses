# 1. State Space Model (Continuous)

## 1.1 State Space Representation

$$
\overset{.}{X}(t) = AX(t) + BU(t)
$$

$$
Y(t) = CX(t) + DU(t)
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
\gamma(t) = L^{-1}
\left\{[[sI - A]^{-1}BU(s)]
\right\}\\
\Phi(t) = L^{-1}\left\{[sI - A]^{-1}\right\}
\end{cases}
$$

# 2. State Space Model (Discrete)

## 2.1 State Space Representation

$$
X(k+1) = AX(k) + BU(k)
$$

$$
Y(k) = CX(k) + DU(k)
$$

## 2.2 Transfer Function

$$
TF = {Y(z)\over U(z)} = (C{[zI -A]}^{-1}B + D) = (C{adj[zI-A]B\over det[zI-A]}) + D  
$$

## 2.3 Continuous -> Discrete

given $\Phi(t)$, sampling period  $T$ 

$$
X(k+1) = \Phi(T)X(k) + \Theta(T)U(k)
$$

$$
\begin{cases}\Phi(t) = L^{-1}
\left\{
[sI - A]^{-1}
\right\}_{t=T}\\ 
\Theta(T) = \int_0^T\Phi(\tau)d\tau B\end{cases}  
$$

# 3. Poles and Zeros

## 3.1 Poles

Continuous: $det[sI-A]=0$  
Discrete: $det[zI-A]=0$  

## 3.2 Discrete Time Zeros:

$$
det\left[
\begin{matrix}
 zI-A & -B\\
 C & D
\end{matrix}
\right]=0  
$$

# 4. Solving the State by Recursion

given $X(0)$ and $U(i)_{i=0,1,...,k-1}$    

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

If $X(k) = PW(k) \rightarrow W(k) = P^{-1}X(k)$   

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

for a system $A, B, C, D$ , $det[zI - A]=z^n + a_{n-1}z^{n-1} + ... + a_1z + a_0$

## 6.1 Controllable Canonical Form (CCF)

$$
W_c=\left[
\begin{matrix}
     B & AB & A^2B & ... & A^{n-1}B
\end{matrix}
\right]
$$

$$
\overset{\sim}{W}_c=\left[
\begin{matrix}
 B_c & A_cB_c & A_c^2B_c & ... & A_c^{n-1}B_c
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
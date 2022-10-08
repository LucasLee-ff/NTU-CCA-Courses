# 线性规划
### **1. Initial feasible solution (LectureNote 1 p23)**
1) 无松弛变量 (slack variable) 的等式加入人工变量 (artificial variable).  
2) slack, artificial variable 等于等式右边常数，其他变量设为0.
### **2. LP Standard form (LectureNote 1 p32)**
### **3. Basic solution (LectureNote1 p20)**
  
# 单纯形法
### **1. 单纯形法步骤 (LectureNote 2 p3)**
### **2. 存在人工变量 (C中有M) 的单纯形法 (LectureNote 2 p20)**

# 对偶
### **1. 对偶问题的定义 (LectureNote 2 p34)**
### **2. 通过对偶问题求解原问题  (LectureNote 2 p37)**
### **3. 通过 primal 和 dual 的可行解判定是否最优 (LectureNote 2 p43, 44)**  

# 敏感性分析
### **1. 计算 $A^*$, $C^{*T}$, $S$, $y^T$ (LectureNote 2 p48, 49)**
### **2. 常数项 $B$ 改变 (LectureNote 2 p55)**
计算 $SB_c$ > 0
### **3. 最优解中为0的变量 (nonbasic variable) 的系数改变**
1) 仅目标函数系数 $C^*$ 改变 (LectureNote 2 p61)  
2) $A^*$ 和 $C^*$ 均改变 (LectureNote 2 p63)
### **4. 最优解中不为0的变量 (basic variable) 的系数改变 (LectureNote 2 p64)**

# 运输问题
### **1. 总需求不等于总供应的解决方法 (LectureNote 3 p11)**
创建虚拟 source/demand，对应数值为差值
### **2. 寻找初始可行解 (LectureNote 3 p18)**
### **3. 检查是否为最优解 (LectureNote 3 p24)**
### **4. 初始可行解不是最优，找环路 (LectureNote 3 p28)**

# 分配问题
### **1. 匈牙利法 (LectureNote 3 p41)**
1) 每行减去行最小值，在得到的结果上每列减去列最小值  
2) 检查是否存在 n 个两两不在同一行同一列的 0，若存在，达到optimum，否则跳到下一步  
3) 用最少直线覆盖所有 0，找到没被直线覆盖的数中的最小值；所有未被覆盖的数减去该最小值，所有两直线相交处的数加上该最小值  
4) 回到第 2) 步 
### **2. 某人无法胜任某工作 (LectureNote 3 p44)**
将对应的代价 $c_{ij}$ 设为一个非常大的正数 $M$
### **3. 人数与工作数不等 (LectureNote 3 p51)**
设置dummy job，所有人对其cost都为0

# 非线性规划
### **1.非线性规划标准形式 (LectureNote 4 p3)**
1) objective function $f(X)$  
2) equlity constraint $h(X)$ = $h^{'}(X) - \alpha$  
3) inequlity constraint $g(X)$ = $g^{'}(X) - \beta$  
### **2.单变量优化**
#### **(1) Direct search method (LectureNote 4 p15)**
#### **(2) Fibonacci search method (LectureNote 4 p19)**
#### **(3) Golden-section search method (LectureNote 4 p28)**
#### **(4) Newton's method (LectureNote 4 p36)**
$x_{n+1}$ = $x_n$ - $f^{'}(x_n)/f^{''}(x_n)$
### **3. 多变量优化 (LectureNote 4 p39)**
#### **(1) 最优判别 optimality criteria (LectureNote 4 p42)**
梯度为0，Hessian matrix 正定 -> minimum
梯度为0，Hessian matrix 负定 -> maximum
#### **(2) Newton's method (LectureNote 4 p52)**
$X_{n+1}$ = $X_n$ - $[\nabla^2f(X_n)]^{-1} \nabla f(X_n)$
### **4. 包含相等条件的多变量优化 (LectureNote 4 p58)**
$min:f(X)$  
$s.t.$ $h_i(X)=0$
### **5. 包含不等条件的多变量优化 (LectureNote 4 p76)**
$min:f(X)$  
$s.t.$ $g_j(X) \le 0$
### **6. 包含相等与不等条件的多变量优化 (LectureNote 4 p83)**
$min:f(X)$  
$s.t.$ $h_i(X)=0$, $g_j(X) \le 0$
### **7. 凹凸函数定义 (LectureNote 4 p89)**
Hessian matrix 正定/半正定 -> convex  
Hessian matrix 负定/半负定 -> concave
### **8. K-T sufficient theorem (LectureNote 4 p92)**
若 $f(X)$ 为凸函数，不等条件 $g_j(X)$ 均为凸函数，相等条件 $h_i(X)$ 为线性，若 $(X^*,\lambda^*,\mu^*)$ 满足K-T条件，$X^*$ 为最优解
### **9. 敏感性分析 (LectureNote 4 p96)**
$min:f(X)$  
$s.t.$ $h_i(X)=\alpha_i$, $g_j(X) \le \beta_j$  
若 $\alpha_i^{'}=\alpha_i+\Delta\alpha_i$, $\beta_i^{'}=\beta_i+\Delta\beta_i$   
$\Delta f(X^*) \approx - \Sigma_i \lambda^*_i \Delta \alpha_i - \Sigma_j \mu^*_j \Delta \beta_j$  

# Levene检验的数学原理与手工计算示例

## 1. 检验原理
Levene检验通过比较各组数据与组中心位置偏离程度的平均值来检验方差齐性，构造的统计量如下：
## 基本概念
**Levene检验** (Levene's test) 是一种用于检验多组数据方差齐性（homogeneity of variances）的非参数方法。它是ANOVA分析的重要前提检验，替代了传统的Bartlett检验（对正态性要求严格）。

### 核心特点：
- 原假设(H₀)：所有组的方差相等
- 备择假设(H₁)：至少有两组方差不相等
- 默认使用**中位数**作为集中趋势度量（对非正态数据稳健）
- 结果解读：p值 < α(通常0.05)时拒绝原假设
### 核心公式

<img width="362" height="95" alt="image" src="https://github.com/user-attachments/assets/6a56fb3b-a1b8-49c0-84aa-858c6e81b170" />


其中：
- $k$：组别数量
- $n_i$：第$i$组的样本量
- $N$：总样本量（$N = \sum n_i$）
- $Z_{ij} = |Y_{ij} - \tilde{Y}_i|$（$\tilde{Y}_i$为第$i$组的中位数）
- $\bar{Z}_i$：第$i$组$Z_{ij}$的平均值
- $\bar{Z}$：所有$Z_{ij}$的全局平均值

## 2. 手工计算示例

### 实验数据
检验以下三组数据的方差齐性（α=0.05）：

| 组别 | 样本值 |
|------|--------|
| A    | 3, 5, 7, 5, 4 |
| B    | 6, 8, 10, 7, 9 |
| C    | 12, 15, 11, 13, 14 |

### 计算步骤

**Step 1：计算各组中位数**
- 组A中位数 $\tilde{Y}_1 = 5$
- 组B中位数 $\tilde{Y}_2 = 8$  
- 组C中位数 $\tilde{Y}_3 = 13$

**Step 2：计算绝对离差 $Z_{ij}$**

<img width="787" height="308" alt="image" src="https://github.com/user-attachments/assets/742d3528-ab75-4b7d-804d-98ebd229cba1" />
<img width="391" height="317" alt="image" src="https://github.com/user-attachments/assets/c778c2bd-d009-48c4-9e5c-972a37e0f74d" />


**Step 3：计算各组$Z_{ij}$均值**
$\bar{Z}_1 = (2+0+2+0+1)/5 = 1.0$
$\bar{Z}_2 = (2+0+2+1+1)/5 = 1.2$
$\bar{Z}_3 = (1+2+2+0+1)/5 = 1.2$
- 全局均值 $\bar{Z} = (1.0+1.2+1.2)/3 ≈ 1.133$

**Step 4：计算分子部分**
$$\sum n_i(\bar{Z}_i-\bar{Z})^2 = 5(1.0-1.133)^2 + 5(1.2-1.133)^2 + 5(1.2-1.133)^2 ≈ 0.133$$

**Step 5：计算分母部分**
<img width="644" height="63" alt="image" src="https://github.com/user-attachments/assets/8567a294-2055-4a14-a104-8754c92e0c54" />


**Step 6：计算统计量**
$$W = \frac{15-3}{3-1} \times \frac{0.133}{6.0} ≈ 0.133$$

**Step 7：查F分布表**
比较 $W$ 与 $F_{0.05(2,12)} = 3.885$  
∵ 0.133 < 3.885 ∴ 不拒绝原假设

### 结论
在0.05显著性水平下，三组数据方差无显著差异（W=0.133, p>0.05）

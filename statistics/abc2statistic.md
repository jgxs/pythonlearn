# basic #  

for ***n*** items set
$$ { x_1, x_2, x_3, \ldots , x_n } $$  

**mean**:
$$ \mu=x_{mean} = \frac {\sum_i^n x_i} {n}  $$

**variance***:
$$    \sigma^2=x_{variance} = \frac {\sum_i^n (x_i-x_{mean})^2}{n}  $$

**standard variance**:
$$ \sigma = \sqrt{\sigma^2} = \sqrt{\frac {\sum_i^n (x_i-x_{mean})^2}{n} } $$

Supposing $x_i$ represents the observed value, while the predicted value of $x_i$ is $y_i$, then we can use the terms below to evaluate the prediction.

$${y_1, y_2,\ldots, y_n }$$

**error**:
$$ \delta_i = err_i = |y_i - x_i| $$

**mean square error**:
$$X_{MSE} = \frac {\sum_i^n \delta_i^2 } {n}$$

**root mean square error**:
$$X_{RMSE} = \sqrt{X_{MSE}} = \sqrt{\frac {\sum_i^n \delta_i^2}{n}}  $$

These three items can represent precision of the prediction.

**RMSD** stands for ***Root Mean Square Deviation***.  

The word "deviation" in the definition of RMSD refers to this:
When two structures are compared, a RMS value is measured for each atom and for instance, if you want to compare two structures named Protein 1 and Protein 2: RMSD = Protein 1's atom RMS - Protein 2's atom RMS.

给定一个分子结构的两种状态，$\delta_i$就是第i个原子的位置在这两种状态下的差值（偏移），对结构中所有的粒子的偏移量求平方和再平均，开方，就是RMSD。

***RMSF*** stands for ***Root Mean Square Fluctuation***.  

$$ X_{RMSF} = \sqrt{\frac{\displaystyle\sum_{t_j=1}^T(x_i(t_i)-\mu_{i})^2}{T}} $$  
RMSF计算的是一个粒子在时间T内，其位置的偏移量之平方和随时间的平均后再开方。RMSF的计算可以写成积分的形式，时域上(0,T)区间的积分  
RMSD表示的是分子结构变化的程度，而RMSF值表示的是分子中各个原子运动的自由程度  

Covariance 协方差是一个反映两个随机变量相关程度的指标，如果一个变量跟随着另一个变量同时变大或者变小，那么这两个变量的协方差就是正值，反之相反，公式如下：  
$$ Cov_{x,y}=\frac{\displaystyle\sum_{i=1}^n{(x_i-\mu_x)(y_i-\mu_y)}}{n-1} $$

但是协方差有一个缺点：它的值会随着变量量纲的变化而变化（covariance is not scale invariant），所以，这才提出了相关系数(correlation coefficient)的概念：  
$$ r = Corr_{x,y} = \frac{Cov_{x,y}}{\sigma_x \cdot \sigma_y} = \frac {\displaystyle\sum_{i=1}^n(x_i-\mu_x)\cdot(y_i-\mu_y)}{\displaystyle\sqrt{\displaystyle \sum_{i=1}^n(x_i-\mu_x)^2}\cdot\sqrt{\displaystyle \sum_{i=1}^n(y_i-\mu_y)^2}}$$

相关系数是用于描述两个变量线性相关程度的:  如果r>0，呈正相关；如果r=0，不相关；如果r<0，呈负相关。  

如果我们将$\{x_i-\mu_x\}$和$\{y_i-\mu_y\}$看成两个$n$维向量的话，那$r$刚好表示的是这两个向量夹角的余弦值，这也就解释了为什么r的值域是[-1, 1]。

相关系数对变量的平移和缩放（线性变换）保持不变（Correlation is invariant to scaling and shift，不知道中文该如何准确表达，😅）。比如Corr(X,Y)=Corr(aX+b,Y)恒成立  

下面来说决定系数，R方一般用在回归模型用用于评估预测值和实际值的符合程度，R方的定义如下：  
$$R^2 = 1-FVU = 1- \frac{RSS}{TSS} = 1 - \frac{\displaystyle \sum_i^n{(f_i-y_i)^2}}{\displaystyle \sum_i^n{(y_i-\mu_y)^2}}$$  

式中$y_i$是实际值，$f_i$是预测值，$\mu_y$是实际值的平均值。  
***FVU***被称为***fraction of variance unexplained***  
***RSS***叫做***Residual sum of squares***，  
***TSS***叫做***Total sum of squares***  
根据$\mathrm{R^2}$的定义，可以看到$\mathrm{R^2}$是有可能小于0的，所以$\mathrm{R^2}$不是$\mathrm{r}$的平方。
一般地，$\mathrm{R^2}$越接近1，表示回归分析中自变量对因变量的解释越好。

对于$\mathrm{R^2}$可以通俗地理解为使用均值作为误差基准，看预测误差是否大于或者小于均值基准误差。

此外，我们做这样一个变形：可以看到变成了1减去均方根误差和方差的比值（有利于编程实现）
$$R^2 = 1 - \frac{\sum\limits_i(y_i - f_i)^2 / n}{\sum\limits_i(y_i - \hat{y})^2 / n} = 1 - \frac{\mathrm{RMSE}}{\mathrm{Var}}$$

对于Explained sum of squares
$$\mathrm{ESS} = \sum\limits_i(f_i - \hat{y})^2$$

$$R^2 = 1 - \frac{\mathrm{RSS}}{\mathrm{TSS}} = \frac{\mathrm{ESS}}{\mathrm{TSS}} = \frac{\sum\limits_i(f_i - \hat{y})^2}{\sum\limits_i(y_i - \hat{y})^2}$$  

# basic #
for ***n*** items set
$$ { x_1, x_2, x_3, ... , x_n } $$    

**mean**:
$$ \mu=x_{mean} = \frac {\sum_i^n x_i} {n}  $$

**variance***:
$$    \sigma^2=x_{variance} = \frac {\sum_i^n (x_i-x_{mean})^2}{n}  $$

**standard variance**:
$$ \sigma = \sqrt{\sigma^2} = \sqrt{\frac {\sum_i^n (x_i-x_{mean})^2}{n} } $$

Supposing $x_i$ represents the observed value, while the predicted value of $x_i$ is $y_i$, then we can use the terms below to evaluate the prediction.

$${y_1, y_2, ... , y_n }$$

**error**:
$$ err_i = |y_i - x_i| $$

**mean square error**:
$$X_{MSE} = \frac {\sum_i^n err_i^2 } {n}$$

**root mean square error**:
$$X_{RMSE} = \sqrt{X_{MSE}} = \sqrt{\frac {\sum_i^n err_i^2 } {n}}  $$

These three items can represent precision of the prediction.

**RMSD** stands for ***Root Mean Square Deviation***.   

The word "deviation" in the definition of RMSD refers to this:
When two structures are compared, a RMS value is measured for each atom and for instance, if you want to compare two structures named Protein 1 and Protein 2: RMSD = Protein 1's atom RMS - Protein 2's atom RMS.
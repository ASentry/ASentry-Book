# 似然函数

### 似然函数(likelihood function)

> ***Likelihood*** is used to describe the plausibility of a value for the parameter, given some data.  —from wikipedia

其数学形式为：

假设X是观测结果序列，它的概率分布fx依赖于参数θ，则似然函数表示为
$$
L(\theta\mid x) = f_\theta(x)=P_\theta(X=x)
$$

### 离散型概率分布(Discrete probability distributions)

假设X是离散随机变量,其概率质量函数p依赖于参数θ,则有
$$
L(\theta\mid x) = p_\theta(x)=P_\theta(X=x)
$$

### 连续型概率分布(Continuous probability distributions)

假设X是连续概率分布的随机变量,其密度函数f依赖于参数θ ,则有
$$
L(\theta\mid x) = f_\theta(x)
$$

### 最大似然估计(Maximum Likelihood Estimation,MLE)

假设每个观测结果x是独立同分布的，通过似然函数L(θ|x)，求使观测结果X发生的概率最大的参数θ，即argmaxf(X;θ)

### 对数似然估计(log likelihood)

由于对数函数具有单调递增的特点，对数函数和似然函数具有同一个最大值点。取对数是为了方便计算极大似然估计，MLE中直接求导比较困难，通常先取对数再求导，找到极值点。

### 负对数似然估计(negative log-likelihood)

$$
-logP(y\mid x)
$$


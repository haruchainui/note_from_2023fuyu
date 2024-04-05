## 基本概念

![image-20240330014014140](Diffusion数学原理1.assets/image-20240330014014140.png)

## VAE vs Diffusion model

![image-20240330014056122](Diffusion数学原理1.assets/image-20240330014056122.png)

区别在于VAE中的encoder需要训练，add noise 的过程是固定的，并不是NN

## algorithm

![image-20240330014424441](Diffusion数学原理1.assets/image-20240330014424441.png)

### training

![](./Diffusion%E6%95%B0%E5%AD%A6%E5%8E%9F%E7%90%861.assets/image-20240405151644370.png)

![image-20240330015827926](Diffusion数学原理1.assets/image-20240330015827926.png)

![](Diffusion数学原理1.assets/image-20240330164032210.png)

t越大，$\alpha$越小，意味着原图所占的比例越小（更多噪音）

t是$\epsilon_{\theta}$的输入

![image-20240330170131735](Diffusion数学原理1.assets/image-20240330170131735.png)

![image-20240330170155295](Diffusion数学原理1.assets/image-20240330170155295.png)

### Inference

![image-20240330170819624](Diffusion数学原理1.assets/image-20240330170819624.png)



## 影像生成模型本质上共同的目标

![](Diffusion数学原理1.assets/image-20240330171407196.png)

从一个简单的，可预测的distribution，通过NN使之取值范围尽量接近真正的distribution

### Maximum Likelihood Estimation

![image-20240330171918294](Diffusion数学原理1.assets/image-20240330171918294.png)

$\theta^*$：我们想要找到的参数向量，能够使$x^i$出现在$P_{\theta}$中的似然概率最大

![](Diffusion数学原理1.assets/image-20240330174124157.png)

**在第二行中，这一步可以理解为**：

在训练集中的数据中sample所有 $x^i$，其在 $P_{\theta}$中的出现概率最大

$\approx$ 在真实数据 $P_{data}$中sample数据$x$，$x$在$P_{\theta}$中的出现概率最大

总而言之，以抽样数据推断整体

maximum likelihood estimation=minimize kl divergence



![image-20240330180810041](Diffusion数学原理1.assets/image-20240330180810041.png)

![image-20240405165321554](./Diffusion%E6%95%B0%E5%AD%A6%E5%8E%9F%E7%90%861.assets/image-20240405165321554.png)

### probability density function 与divergence

![image-20240405165827782](./Diffusion%E6%95%B0%E5%AD%A6%E5%8E%9F%E7%90%861.assets/image-20240405165827782.png)

$x$出现于$P$中的几率

正比于$G(z)$和$x$的divergence的负数

## VAE：Lower bound of $logP(x)$

![](./Diffusion%E6%95%B0%E5%AD%A6%E5%8E%9F%E7%90%861.assets/image-20240405170623512.png)

## DDPM:Compute $P_{\theta}(x)$

![image-20240405171021636](./Diffusion%E6%95%B0%E5%AD%A6%E5%8E%9F%E7%90%861.assets/image-20240405171021636.png)

这里为什么在假设$G(x_t)$的时候把他假设成一个高斯分布的mean？为什么不考虑他是更复杂的分布？为什么不考虑variance

以往的经验来讲考虑variance并不会让model结果更好，更复杂的分布也是一样。

![image-20240405171839155](./Diffusion%E6%95%B0%E5%AD%A6%E5%8E%9F%E7%90%861.assets/image-20240405171839155.png)

![](./Diffusion%E6%95%B0%E5%AD%A6%E5%8E%9F%E7%90%861.assets/image-20240405171918758.png)

## 基本概念

![image-20240330014014140](Diffusion数学原理1.assets/image-20240330014014140.png)

## VAE vs Diffusion model

![image-20240330014056122](Diffusion数学原理1.assets/image-20240330014056122.png)

区别在于VAE中的encoder需要训练，add noise 的过程是固定的，并不是NN

## algorithm

![image-20240330014424441](Diffusion数学原理1.assets/image-20240330014424441.png)

### training

![](Diffusion数学原理1.assets/image-20240330165936331.png)

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

![](Diffusion数学原理1.assets/image-20240330174124157.png)

maximum likelihood estimation=minimize kl divergence

![image-20240330180810041](Diffusion数学原理1.assets/image-20240330180810041.png)

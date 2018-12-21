---
layout: post
mathjax: true
author: Long
title:  " Lotka–Volterra equations"
---

## Prey-Predator equations

对于一个捕食者-猎物系统（Prey-Predator system)，其可以由一对一阶自治方程：

$$\frac{dx}{dt} = \alpha x - \beta xy$$

$$\frac{dy}{dt} = \delta xy - \gamma y$$

其中$x$为猎物数量，$y$为捕食者数量，来描述。上述方程组即为Prey-Predator system的Lotka–Volterra equations。

对于猎物，前一项代表着自然增长（自然生长和自然死亡之差），后一项表示对于猎物种群中每一个个体受到每个捕食者的捕食压力为$\beta$，他受到所有捕食者的竞争压力为$\beta y$,整个种群收到的捕食压力的总和即为$\beta xy$。
对于捕食者，每个猎物对每个捕食者提供的捕食成功率和转化率之积为$\delta$,
同理整个捕食者种群由于猎物种获得的繁殖为$\delta xy$，而后一项则为捕食者群体的自然死亡。
**注意，上述方程未考虑任何竞争，包括种内竞争。**

## Competition equations

对于一个竞争系统，其也有相应的Lotka–Volterra equations。

### 单物种竞争

对于单一物种的种群，其个体在竞争中具有相同的能力不具有差异，那么其Lotka–Volterra equations为：

$$\frac{dx}{dt} = rx(1 - \frac{x}{k})$$

为了更为形象的理解上述单物种竞争方程，并使其易于同捕食者-猎物相比较。我将其改写为：

$$\frac{dx}{dt} = rx - \frac{r}{k} x \times x$$

前一项描述的是自然增长，而后一项则表示对于种群中任意一个个体，他受到所有个体的竞争压力$\frac{r}{k}x$，整个种群收到的竞争压力的总和即为$\frac{r}{k}x\times x$。

### 多物种竞争

对于多物种竞争，不同物种之间在竞争中具有不同的生长率，环境容纳量和竞争优势，其方程为：

$$\frac{dx_i}{dt} = r_i x_i(1 - \frac{\sum_j \alpha_{ij} x_j}{K_i})$$

对上式进行相同的改写：

$$\frac{dx_i}{dt} = r_i x_i - \frac{r_i x_i \sum_j\alpha_{ij} x_j}{K_i}$$

对于多物种竞争，$\alpha_{ij}$可以被认为是物种$i$对$j$的竞争优势，显然，$\alpha_{ii} = 1$。而却对于多物种方程，我们可以更显著但看出第二项的含义。

## 两类方程的联合及对捕食能力差异是否能够完全解释捕食者竞争的讨论

### 方程的联合

由于对单物种竞争方程的解释，单物种内竞争是存在的，我们在此处可以只对只存在一对捕食者-猎物方程进行扩充。对于猎物，这一扩充方式是显然的：
$$\frac{dx}{dt} = \alpha x - \beta xy - \lambda x^2$$
最后一项$\lambda$为物种的竞争强度。
但是，对于捕食者的竞争，是否有必要增加项及如何增加项，这是有疑问的，为此我必须先进行讨论。

### 捕食能力差异是否能够完全解释捕食者竞争的讨论

由于此处我们仅存在单个捕食者种群，其捕食能力的差异不存在差异，但是单物种内仍然存在竞争，故而在考虑竞争的情况下，对于捕食者，对于任意猎物给定的情况下，其必然存在一个上限，然而对于捕食者方程：
$$\frac{dy}{dt} = \delta xy - \gamma y = (\delta x - \gamma)y$$
其增长率是固定的其完全由猎物的数量决定，当猎物数量满足$\delta x - \gamma > 0$时，其将不断的增长。倘若我们认为维持猎物数量恒定且满足上述条件，那么我们将得到一个指数增长的捕食者种群，这显然是与事实相悖的。

扩展到多个捕食者种群的情况下，仍然保持猎物种群恒定且对于任意的捕食者均满足上述条件，那么我们得到多个指数增长捕食种群，但是其相对多度会表现出差异，最终最优物种会占据捕食者种群中的绝大多数。而在实际的种群动态中，由于捕食者的增加会导致猎物数量的降低，从而使得劣势物种会更早开始出现下降，故而依然可以表现竞争。

### 回到方程的联合

由于上述讨论，对于只存在一对捕食者猎物的模型的方程联合变得显然：

$$\frac{dx}{dt} = \alpha x - \beta xy - \lambda x^2$$

$$\frac{dy}{dt} = \delta xy - \gamma y- \kappa y^2$$

对于存在多对捕食者猎物的模型，存在两种方式：

方式一：

$$\frac{dx_i}{dt} = \alpha_i x_i -x_i \sum_j \beta_{ij} y_j - x_i \sum_j\lambda_{ij} x_j$$

$$\frac{dy_i}{dt} = y_i \sum_j \delta_{ij} x_j  - \gamma_i y_i - y_i \sum_j \kappa_{ij} y_j$$

方式二：

$$\frac{dx_i}{dt} = \alpha_i x_i - x_i \sum_j \beta_{ij} y_j - x_i \sum_j\lambda_{ij} x_j$$

$$\frac{dy_i}{dt} = y_i \sum_j \delta_{ij} x_j -\gamma_i y_i - \kappa_i y_i^2$$

即是否额外考虑不同捕食者种群之间的竞争，此处待进一步讨论。

### 从另一个角度进行修改

考虑到猎物的自然增长率实际上是由其对上一营养级的捕食（对于植物则是阳光的吸收）并转化减去死亡率简化的结果，故可以考虑，直接替换竞争方程中$r_i$为$(\sum_j \delta_{ij} x_j - \gamma_i)$得到捕食者竞争方程：

$$\frac{dx_i}{dt} = (\sum_k \delta_{ik} x_j - \gamma_i) y_i(1 - \frac{\sum_j \alpha_{ij} y_j}{K_i})$$

展开，并简化得到：

$$\frac{dy_i}{dt} = y_i \sum_j \delta_{ij} x_j - \gamma_i y_i + \gamma_i y_i\sum_j \kappa_{ij} y_j - y_i \sum_k \delta_{ik} x_k\sum_j \kappa_{ij} y_j$$

对于一对的捕食者猎物模型，其简化为：

$$\frac{dy}{dt} = \delta xy - \gamma y+ \gamma\kappa y^2 - \delta\kappa xy^2 = \delta xy - \gamma y - (\delta x - \gamma)\kappa y^2$$

若将$(\delta x - \gamma)$视为恒定,并将其吸收入$\kappa$，则得到之前的方程。

此处可以看出前文忽视了猎物种群变化对捕食者竞争的影响，因此上述方程可能是最能够准确的描述捕食者竞争的方程。

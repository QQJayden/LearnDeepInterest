# 图像风格迁移

---

> 知乎： [04 图像风格迁移](https://zhuanlan.zhihu.com/p/44165451)

## 原理

图像风格迁移是将一幅内容图的内容和一幅或多幅风格图的风格融合在一起，从而生成一些有意思的图片

所生成的风格图内容上应该尽可能接近内容图，风格上尽可能接近风格图

因此需要定义内容损失函数和风格损失函数

### 损失函数

+ 内容损失函数：

以VGG19为例，介绍内容损失函数

![1552123139346](/home/jayden/github/LearnDeepInterest/图像风格迁移/1552123139346.png)

![1552051613602](https://github.com/QQJayden/LearnDeepInterest/raw/master/home/jayden/.config/Typora/typora-user-images/1552051613602.png)


$$
L_{content}(\vec{p},\vec{x},l)=\frac12\sum_{i,j}(F_{ij}^l-P_{ij}^l)^2
$$

+ 风格损失函数：

风格难以说清，这里使用卷积层各个特征图之间的互相关作为风格

以conv1_1为例，共包含64个特征图，每个特征图都是对上一层输出的一种理解；64个人之间的理解差异可用特征图的互相关表示；不同风格会导致差异化互相关结果

![1552052416636](/home/jayden/.config/Typora/typora-user-images/1552052416636.png)

+ 总损失

![1552052439565](/home/jayden/.config/Typora/typora-user-images/1552052439565.png)
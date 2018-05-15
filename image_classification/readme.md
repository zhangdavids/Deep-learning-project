

1.数据的预处理

归一化处理 one-hot-encoder

可以利用 sklearn　中的 Preprocessing　中的 LabelBinarizer 函数

也可以使用numpy的eye函数


2.卷积层 最大池化层 扁平化层 全连接层 输出层


本项目的难点在于模型的参数选择。具体参数包括：


+ 卷积层滤波器的　size　以及 stride： 

    经过反复测试，滤波器 选择　4*4，stride 选择 1 的效果较好 

+ 最大池化的 size　以及 stride: 

    池化的 size 选择　8*8， stride 选择１的效果较好 

+ 全连接层的输出 size： 

    输出层为 384 个输出的效果较好 

+ keep-probability: 

    经过测试，keep-probability 宜小一点，可以更好的防止 overfitting。
    
    但是太小的 keep-probability 也会导致运算速度慢，以及模型预测不准的问题。 

+ 各个层级的 weight　的初始化问题： 

    我在搭建模型初期，遇到一个很大的问题就是，初始化参数设置不合理，导致收敛太慢。
    
    一开始注意到收敛太慢的问题时，我采用的方法是增大 optimizer 的 learning-rate ，
    
    
通过查询资料，发现应该在初始化变量时，调整正态分布的标准差，将默认的标准差“1”修改为 “0.1” 或 “0.01”。



>  2019/11/6



## Review：

- ### 人工神经元
  - 一组输入，线性加权叠加后，通过非线性的变换，输出

- ### 权重可调节

- ### 多层神经网络

  - 单层神经网络：线性分类
  - 多层：可以进行复杂分类

- ### 层间联系关系

  - 连接主义观点：人工神经网络由大量的神经元以及他们的有向连接构成，能够实现复杂的智能功能
  - 前馈（分类）、反馈（预测）、记忆网络（算法）、图网络

- ### 工作原理

  - def（训练数据集、样本、标签）
  - 监督学习：训练+推断
  - 训练：
    - 目标函数
    - 过程：调整权重
    - 固化：固定权重，形成统一的模型参数网络，即训练的结果
  - 推断：
    - 即实际应用此模型推测新数据的标签

- ### 模型参数

  - 网络的层数、结构
  - 每层的权重
  - 输入与输出端
  - 使用$netron$查看

- ### SGD随机梯度下降法

  - 关键是选择一个随机样本

- ### 小批量训练

  - mini-batch
  - 一个mini-batch为一次迭代
  - 整个数据集为一个时代



## 卷积网络

- 是一种==前馈==网络，连接关系不如Dense多

  ### 卷积

  - 是一种张量运算，由==卷积核==遍历所有像素，途中对应格求积，积求和。即 卷积核移动一格，卷积层得到一个格，三维张量是同理的

    ![Day9.1.png](https://i.loli.net/2019/11/06/4z5YWCLmjQ6eKsn.png)

    ![Day9.2.png](https://i.loli.net/2019/11/06/Wpfok7GsTIAVlCr.png)

### 卷积网络的发展

- $LeNet-5$：手写字体识别
- $AlexNet$：图像分类
  - 一次卷积多次池化最终使用Dense
  - Dropout避免过学习
- 新的网络结构不断提出

### 应用

- 深度卷积网络-人脸识别
  - 多隐藏层进行逐层的模型自底向上建构：特征学习，特征工程

- R-CNN：对象检测（Region-based Convolutional Neural Network)



## 语音识别

- 波形图
- 频域图
- 时频谱图（保留了上二者的信息：STFFT变换）

### 语音识别的本质：

- 经典方法：STFFT变换将语音按时间分成小段向量序列，转为音素，转为字母，转为词汇。
- 引入DL技术
- 改为纯深度学习模型：识别准确率甚至降低了，终于实用化

### 纯深度学习技术：端到端，一个神经网络搞定

- 三个部分：特征提取（时频谱图）、声学模型、语言模型
- Google CLDNN：结合了卷积网、LSTM（ 长短期记忆网络 ）和DNN



## AudioNet项目

- 使用$Keras$：基于$Tensorflow$而高级
  - Sequential：序列化。。？
- Google-CLDNN

- FFMPEG：音频处理库，用于转码为.wav
- SOX（$SOund\  eXchange$） 数据增强，增多样本：通过增高降低音调，提高减慢语速生成同样有价值的数据。==注意在两个进程分别进行数据增强服务和训练==
- 实现
- 上传web
- 用于Android端
- 注意：
  - SOX for Linux : `SOX_PATH = ...`
  - for Android : 替换`.pb`文件



## 循环神经网络

- 引入了记忆的概念：

  - 一个神经元此次输出的结果受其上一状态的影响

  ![Day9.3.png](https://i.loli.net/2019/11/06/MKwQj5PUzEYuvRo.png)

- 不同类型：

  - 双向RNN：之前的预测也可以由现在的状态修正
  - 深度双向RNN

- LSTM：长短期记忆网络

  - 为解决大量无用记忆不能快速访问有效记忆的问题，引入门，只允许有意义的记忆通过

  1. 决定什么信息要丢掉：忘记门
  2. 决定什么信息要加入细胞状态
  3. 更新细胞信息以及输出

  - 变体：
    - GRU：把忘记门和输入门合成一个门，简化LSTM



## 神经图灵机DNC

- 记忆网络
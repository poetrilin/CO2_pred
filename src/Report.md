# 实验报告
## 问题介绍与理解
[比赛官网](https://www.kaggle.com/competitions/playground-series-s3e20).

## 数据分析

### 可视化分析
通过对数据集进行可视化分析，我们得到了以下一些关键观察：

1. 没有明显的周期性，虽然有常见的时间特征，但是我们通过多次采样发现

### 数据预处理
在数据预处理阶段，我们采取了以下步骤：

- 缺失值处理： 用每个地方的平均值填充缺失值
- 数据标准化： 使用scaler将数据标准化,i.e. 将特征转换为均值为0，方差为1的正态分布
- 标签编码: 使用LabelEncoder将标签转换为数字,进行ordinal encoding,后续也进行了相应的one-hot encoding,测试影响不大

### 特征处理

- 特征选择: 由于数据集中存在大量的特征,我们采用相关分析的方法,选择与标签相关性较高的特征,并将其余特征过滤掉.
- PCA : 主成分分析(Principal Component Analysis) 模型,由于数据集中存在大量的特征,我们使用PCA对特征进行降维处理,以减少模型训练的时间和提高模型的准确率.
- 日期正余弦编码: 由于数据集中存在日期特征,我们对日期进行正余弦编码,在保证周期性的同时,增强了模型的泛化能力.


### 模型选择与实现
为了解决问题，我们尝试了四种不同的模型：

- 决策树： 原理是通过对数据的学习，建立一系列的规则(根据熵进行二分)，从而对数据进行分类的过程

- 随机森林: 集成多个决策树模型来完成学习任务

- XGBoost: 一种梯度提升算法，通过对损失函数进行优化，从而得到一个更好的模型,也是一种集成学习算法

- SVR： 支持向量回归(Support Vector Regression) 模型,通过对数据进行映射,将数据映射到高维空间。这是在上课后得到启发补充的一个模型测试。

结果分析与总结
在对四种模型进行训练和测试后，我们得到了以下结果：

```shell 
model1(DecisionTree), rmse =100.17612298650134
model2(Random Forest), rmse =72.65666466920476
model3(XGBoost), rmse =80.73130345467878
model4(SVR), rmse =  86.50532672217197
```

version 1 : PCA(主成分分析)

```shell
model1(DecisionTree), rmse =113.97760241373803
model2(Random Forest), rmse =84.91892483122726
model3(XGBoost), rmse =90.1006751045587
model4(SVR), rmse =  96.326
```
综合分析表明,随机森林模型的效果最好,其次是XGBoost模型, 决策树模型效果较差.

分工:

- 刘兆宸 : 进行了探索性数据分析,对数据的周期性，分布偏度等特征进行了可视化并进行了简单的数据预处理,特征处理,选择了几个常见的模型与测试。
- 龚劲铭
- 金文丁
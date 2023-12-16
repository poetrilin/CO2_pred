# Predict_CO2_Emissions_PS_S03E20

## Description

Competition: https://www.kaggle.com/competitions/playground-series-s3e20


## Log

version 0 :

使用粗糙的数据处理方法:

- 直接去掉缺失值的行
- 种类特征(过滤取种类<10的)直接转换为数字

效果:
```shell 
model1(DecisionTree), rmse =100.17612298650134
model2(Random Forest), rmse =72.65666466920476
model3(XGBoost), rmse =80.73130345467878
```

version 1 : PCA(主成分分析)

```shell
model1(DecisionTree), rmse =113.97760241373803
model2(Random Forest), rmse =84.91892483122726
model3(XGBoost), rmse =90.1006751045587
```
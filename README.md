# 2018中国高校计算机大赛——Rank4 
快手活跃用户预测——lctry队解决方案

简要介绍

赛题：

“快手”新注册用户脱敏和采样后的数据30天，预测未来7天活跃的用户

解决方案：滑窗法

特别特征：因为注册必登陆，行为能体现用户的某种本质，所以对注册当天提取了特征，注册本身是一种异常，所以去除注册当天记录后再提取特征

主要使用lgb模型，xgb、catboost提升微小。另外使用了三个NN模型（keras+tensorflow）。
前两个NN结构相似，都是把mlp,lstm,cnn集合在一个网络中。

lgb线下0.8905~0.891，三个NN线下都可以0.891+

第一个NN训练方式非常对新手友好，

第二个NN训练比较正常。

第三个NN为GBDT特征（使用xgb提取）+deepFM，主要是对网上的开源代码做了点修改，以个人理解实现。

（NN新手，希望有老手提提意见）

滑窗法对近期用户预测不准：

另外对26-30的用户使用单天滑窗，单独提取特征，使用5个lgb模型进行单独预测

完整的见Github: https://github.com/chantcalf/2018-Rank4-

科赛链接: https://www.kesci.com/home/project/5b7a15a231902f000f54dfd2

原始代码过长且比较混乱，可能引起不适，有兴趣可参考

lgb: https://www.kesci.com/home/project/5b51b92cfc7e900010325a35

NN0: https://www.kesci.com/home/project/5b63098fa711e60010abce78

NN1：https://www.kesci.com/home/project/5b5bc23ba711e600109abffd

NN2：https://www.kesci.com/home/project/5b6bd9ed9889570010cc1cdd


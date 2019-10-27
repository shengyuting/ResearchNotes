# YOLO Series
## 1.YOLO Loss
![yolo_loss](E:\work\record\yolo_loss.png)

* v1和v2 loss中的$\lambda_{coord}$和$\lambda_{noobj}$参数
  调整loss之间的平衡。 v3去掉了该参数，可能模型已经变得更加稳定，不需要这样的微调

* 参数$\Pi_{ij}^{obj} $ 
  某个grid cell的bounding box是否负责预测某个对象。如果不负责那我们就不应该训练该bounding box的条件类别概率和坐标参数，即不应该根据条件概率和中心坐标输出误差调整相应的权重。使用该参数调整对loss的贡献。

* $\hat{C}_{i}$
  训练中，$\hat{C}_{i}$的取值是由grid cell的bounding box有没有负责预测某个对象决定的。

* S
v2和v3去掉了传统的全连接层，使得网络不再限制输入图片的尺寸。根据输入图片的大小和降采样因子便可求的S值。

## 2.存在的问题

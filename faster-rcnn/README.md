## 一、环境搭建
本代码所需环境详见requirements.txt文件，版本不同可能会报错。

## 二、训练步骤
### a.文件下载
下载VOC2007数据集并放在VOCdevkit文件夹中，命名为VOC2007。

### b.处理数据集
确认voc_annotation.py里面的annotation_mode=2后运行voc_annotation.py，生成根目录下的2007_train.txt和2007_val.txt。

### c.模型训练
1.在train.py中设定训练的初始模型（第一次训练直接用‘’），epoch，batch_size，optimizer等训练属性，并确保根目录下的frcnn.py中"model_path"为'logs/last_epoch_weights.pth'，然后运行train.py。

2.如果训练过程中意外中断，可在logs中找到中断前5的倍数的最大epoch储存的model，将train.py中model_path修改为对应相对路径，Init_Epoch修改为该模型对应epoch，即可继续训练。

3.训练过程中可开启tensorboard实时查看train/val loss和每五个epoch评估的mAP和MIoU曲线。

### d.图片处理
1.生成第一阶段top 100 proposal boxes:
将nets/frcnn.py中94行注释，95，96行取消注释，并将根目录下frcnn.py文件中的"model_path"为你想使用模型的相对路径，将图片存放在proposal_img文件夹中，运行根目录下的proposal_box.py，输入图片路径即可预测。生成的有proposal box的图片将储存在proposal_img文件夹中，后缀‘proposal_box’。例如‘airport_proposal_box.png’。

2.生成检测结果（类别标签，得分，boundingbox）：
将根目录下frcnn.py文件中的"model_path"为你想使用模型的相对路径，将图片存放在img文件夹中，运行根目录下的predict.py，输入图片路径即可预测。生成的有预测结果的图片将储存在img文件夹中，后缀‘predict’。例如‘cat_predict.png’。


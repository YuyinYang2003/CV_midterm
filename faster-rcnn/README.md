##环境搭建
本代码所需环境详见requirements.txt文件，版本不同可能会报错。

##训练步骤
###a.文件下载
下载VOC2007数据集并放在VOCdevkit文件夹中，命名为VOC2007。

###b.处理数据集
确认voc_annotation.py里面的annotation_mode=2后运行voc_annotation.py，生成根目录下的2007_train.txt和2007_val.txt。

###c.模型训练
在

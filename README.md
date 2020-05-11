# Pytorch场景迁移学习驾驶场景分类
源代码:[https://github.com/Dalaska/scene_clf](https://github.com/Dalaska/scene_clf)

## 1.安装 pytorch 
直接用官网上的方法能装上但下载很慢。通过换源安装发现torchvision找不到。还有一个方法是下载.whl然后用pip install安装。
```
pip install .\torch-1.4.0+cu92-cp37-cp37m-win_amd64.whl .\torchvision-0.5.0+cu92-cp37-cp37m-win_amd64.whl
```
## 2. 迁移学习
pytorch官网上有一个迁移学习教程。可以参考里面的代码:
[ https://pytorch.org/tutorials/beginner/transfer_learning_tutorial.html]( https://pytorch.org/tutorials/beginner/transfer_learning_tutorial.html)
迁移学习保留cnn网络底层feature，只修改最上层。这样做可以大幅减小训练所需算力及数据。所以实用性很强。
下面用实车采集的驾驶场景数据做一个驾驶场景分类器。

### 2.1. 准备数据
采集的原始数据为视频。需要将视频抽帧得到图片。opencv里有'cv2.VideoCapture'命令可以完成这个功能。
写了一个'get_img_from_video.py' 脚本实现这个功能。
按照试例的形式把图片放入文件夹。文件夹分训练集(train)验证集(val)。每个数据集内根据不同的类分为城市(city)，高速(highway)，闸道口（ramp)。
由于同一段视频抽取的图片比较类似，为了验证泛化能力，训练集和验证集用不同的视频抽取的图片。

![example](https://files-cdn.cnblogs.com/files/dalaska/ramp.bmp)

### 2.2 修改模型
实例里pretrain模型用的是resnet18。运行下面这句会直接从网上下载。如果下载失败的话，直接按显示的连载在网上下载然后把文件放在显示的文件夹里就行了。
```
model_ft = models.resnet18(pretrained=True)
```

### 2.3运行程序
模型训练loss
![epoch](https://files-cdn.cnblogs.com/files/dalaska/epoch.bmp)

模型分类效果
![predict](https://files-cdn.cnblogs.com/files/dalaska/predict.bmp)

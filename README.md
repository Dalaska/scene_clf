# Yolo车辆检测+LaneNet车道检测

通过 加载 object_detector, lane_detector, 
可视化，bbox， lane， obj_list输出到csv

## 用法
运行process_frame


## Yolo车辆检测
yolo通过opencv 实现
下载yolov3 pretrained weight在 https://pjreddie.com/darknet/yolo/ 
weight有400M, 不和代码一起托管了。
把‘yolov3.weights’放在weight文件夹下

## LaneNet 车道线检测
参照这个例子写的：https://github.com/MaybeShewill-CV/lanenet-lane-detection
同样weight 也单独 lanenet_label\model\tusimple_lanenet_vgg

## 车与车道线关系
车辆靠近底部3/4处中心的。
把中心的带入直线方程，
判断在车道线

## 测试检测结果
udacity公开数据集。 
label是以csv村的，有图片编号，计算iou检测结果







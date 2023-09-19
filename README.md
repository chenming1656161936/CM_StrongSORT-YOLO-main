# CM_StrongSORT-YOLO-main
 使用tensorrt对YOLOv5检测进行加速，再用StrongSORT作为跟踪器进行跟踪，其中添加count和draw功能  
 环境安装pip install -r requirements.txt  
 cd yolov5  
 再pip install -r requirements.txt  
 需要去YOLOv5官网当中下载你需要的权重，放在yolov5文件夹中  
 然后python export.py --weights yolov5*.pt --include engine --imgsz 640 640 --device 0  
 会生成tensorrt使用的相应权重yolov5*.engine  
 然后cd ..  
 运行track_v5.py  
 python track_v5.py --yolo-weights yolov5/yolov5*.engine --strong-sort-weights weights/osnet_x0_25_msmt17.pt --source *.MP4 --show-vid --save-txt --save-vid --count --draw  
 其中--yolo-weights是检测器YOLOv5使用的权重  
 --strong-sort-weights是StrongSORT中外观特征提取CNN的权重  
 --source为你需要检测跟踪的视频  
 --show-vid显示运行结果  
 --save-txt保留相应结果文件，其中包括视频帧、类别等
 -save-vid保存结果视频  
 --count开启计数功能，count：记录跟踪每个类别出现的次数
 --draw绘画出目标运动轨迹，原理就是选取框的中心点进行绘画

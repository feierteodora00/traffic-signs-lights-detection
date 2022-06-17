# traffic-signs-lights-detection
Investigating the performance of YOLOv4 detection model for the detection of traffic signs and lights, and finding the parameters that most impact the results

## Information about the files

Configurations: 
1. Original parameters, network input size 416*416
2. Optimal anchors for the dataset, input size 416*416
3. Reduced network input size 320*320
4. YOLOv4-tiny, network input size 416*416
5. Tuned network (augmentation parameters, learning rate, burn in, original achors), network input size 416*416 

V1, V2, V3, V4 and V5 contain the configurations files and results (upon testing) for each of the specified configuration. 
weights_v1, weights_v2, weights_v3, weights_v4 and weights_v5 contain the weights used for testing of each configuration (at different points). 

*csv_files* folder provides files to be used for data visualization

## Setup instructions 

Order of the notebooks:
1. convert_GTSDB.ipynb
2. convert_MakeML.ipynb
3. augment_dataset.ipynb
4. train_test_split.ipynb
5. yolov4-model.ipynb

Setting up the environment (using Google Colab):
1. Clone the Darknet repository 
```
!git clone https://github.com/AlexeyAB/darknet
```
2. Enable GPU and CuDNN in the Makefile
```
!sed -i 's/OPENCV=0/OPENCV=1/' Makefile
!sed -i 's/GPU=0/GPU=1/' Makefile
!sed -i 's/CUDNN=0/CUDNN=1/' Makefile
!sed -i 's/CUDNN_HALF=0/CUDNN_HALF=1/' Makefile
!sed -i 's/LIBSO=0/LIBSO=1/' Makefile
```
3. Compile the Makefile 
```
!make
```
4. Download the pretrained weights 
```
!wget https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v3_optimal/yolov4.conv.137
```
5. Create/edit and place the required files:
    - .data file in the *data* folder
    - .names file in the *data* folder
    - train.txt and test.txt in the *data* folder
    - .cfg files in the *cfg* folder
6. Upload the images to Google Drive, in the *data/images* folder
Provided images are taken from copyright free websites and manually annotated using labelImg tool [(https://pypi.org/project/labelImg/1.4.0/)]
The rest of images are taken from the German Traffic Sign Detection Benchmark [(https://benchmark.ini.rub.de/gtsdb_dataset.html)], reclassified and processed in notebook 1, and Road Signs Dataset [(https://makeml.app/datasets/road-signs)], reclassified and processed in notebook 2

Additional instructions can be found in each of the provided notebooks
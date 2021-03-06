# CNN_Person_Reidentification
Re-identify pedestrians with CNN.

## Introduction
### Dataset
#### RIDLT 
A dataset created for person re-identification task, including 274 identities, 38934 bounding boxes, created by the lab of Professor [Hua Yang](http://icne.sjtu.edu.cn/info/1059/1073.htm) of Shanghai Jiao Tong University.
#### Image_Clipper 
A tool helps to clip bounding boxes from original images from video cameras. The code of the tool is [here](https://github.com/riceroll/image_clipper).
### Training
Train the model with a CNN modified from Caffenet, whose task is classification. The sizes of fc6 and fc7 are modified into 1024 in order to avoid overfitting. The size of fc8 is modified into 151, which is the number of identities in the training set.
### Feature Extraction
Abandong fc8 and extract the vector of fc7 as the feature of an image. Save the features of query sequence and library sequence into a .mat file.
### Evaluation
Adopt XQDA as metric learning method. Use CMC curve to show the performance. The code of evaluation is [here](https://github.com/riceroll/Evaluation_Person_Reidentification).

## Requirements

- Python-2.7
- Caffe(for python) 
- Numpy
- Pylab

## Quick Start
### Download Data
Since the test set and training set are too large, so I uploaded them to MEGA.
Get the deploy file, models and test set(4.51GB) by typing this command in the root directory:
```bash
sh download_model_proto_test.sh
```

Get the training set(11.65GB) by typing this command in the root directory (This step can be skipped if you just want to do the test):
```bash
sh download_train.sh
```

### Training
Train:
```bash
python finetuning_RIDLT.py
```
You have to change the directory of caffe or caffe-master in the code.

### Evaluating
```bash
python evaluation_RIDLT.py
```
You have to change the directory of caffe or caffe-master in the code.


## References

- [BVLC/caffe](https://github.com/BVLC/caffe)

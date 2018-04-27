# Implementation of [Camelyon'16](https://camelyon16.grand-challenge.org/) grand challenge

This repository contains the source code for deep learning based cancer detection system, developed to identify metastatic breast cancer from digital Whole Slide Images (WSI). Using dataset of the Camelyon’16 grand challenge, developed system obtained an area under the receiver operating curve (ROC) of 92.57%, which is superior than results obtained by [the winning method of Camelyon’16 grand challenge](https://camelyon16.grand-challenge.org/results/), developed by Harvard & MIT research laboratories.

#### See [presentation](presentation.pdf) and [report](report.pdf) for detailed information about developed system, various implementations and environmental setup.

## Requirements
  - [python 3.5.x or above](https://www.python.org/downloads/)
  - [Tensorflow 0.12.1 or above (GPU version)](https://github.com/tensorflow/tensorflow)
  - [OpenSlide](http://openslide.org/download/)
  - [sk-learn](http://scikit-learn.org/stable/)
  - [sk-image](http://scikit-image.org/docs/dev/api/skimage.html)
  - [open-cv v3.0](http://docs.opencv.org/3.1.0/d5/de5/tutorial_py_setup_in_windows.html)
  - [numPy](https://github.com/numpy/numpy), [sciPy](https://github.com/scipy/scipy)

## Modules
  - [ops](camelyon16/ops)
    - contains sub-modules for performing common operations 常见操作的子模块 
      - reading WSIs ([wsi_ops.py](camelyon16/ops/wsi_ops.py))
      - 读取 WSIs ([wsi_ops.py](camelyon16/ops/wsi_ops.py))
      - extracting patches from WSIs ([wsi_ops.py](camelyon16/ops/wsi_ops.py))
      - 提取补丁对于WSIs的情况 ([wsi_ops.py](camelyon16/ops/wsi_ops.py))
      - file ops (copy, move, delete, rename, and search patches) ([file_ops.py](camelyon16/ops/file_ops.py))
      - 文件操作(复制、移动、删除、重命名和搜索补丁) ([file_ops.py](camelyon16/ops/file_ops.py))
  - [preprocess](camelyon16/preprocess)
    - contains sub-modules for data pre-processing 包含数据预处理的子模块。
      - find Region of Interest (ROI) for WSIs ([wsi_ops.py](camelyon16/ops/wsi_ops.py))
      - 为WSIs找到感兴趣区域(ROI)。 ([wsi_ops.py](camelyon16/ops/wsi_ops.py))
      - extract training patches from WSIs ([extract_patches.py](camelyon16/preprocess/extract_patches.py))
      - 从WSIs中提取训练补丁。([extract_patches.py](camelyon16/preprocess/extract_patches.py))
      - build TF-Records for training patches ([build_tf_records.py](camelyon16/preprocess/build_tf_records.py))
      - 为训练补丁建立tf记录。([build_tf_records.py](camelyon16/preprocess/build_tf_records.py))
  - [postprocess](camelyon16/postprocess)
    - contains sub-modules related to post-processing 包含与后处理相关的子模块。
      - extract patches for heatmaps ([extract_patches_heatmap.py](camelyon16/postprocess/extract_patches_heatmap.py))
      - 提取的补丁的热图 ([extract_patches_heatmap.py](camelyon16/postprocess/extract_patches_heatmap.py))
      - building TF-Records for heatmaps ([build_tf_records_heatmap.py](camelyon16/postprocess/build_tf_records_heatmap.py))
      - 建筑TF-Records热图 ([build_tf_records_heatmap.py](camelyon16/postprocess/build_tf_records_heatmap.py))
      - building heatmaps ([build_heatmap.py](camelyon16/postprocess/build_heatmap.py))
      - 建筑的热图 ([build_heatmap.py](camelyon16/postprocess/build_heatmap.py))
      - extract features from heatmaps ([extract_feature_heatmap.py](camelyon16/postprocess/extract_feature_heatmap.py))
      - 提取特征的热图 ([extract_feature_heatmap.py](camelyon16/postprocess/extract_feature_heatmap.py))
      - feature classifiers (SVM, Random Forest) ([wsi_classification_modular.py](camelyon16/postproce/wsi_classification_modular.py))
      - 功能分类器 ([wsi_classification_modular.py](camelyon16/postproce/wsi_classification_modular.py))
  - [inception](camelyon16/inception)
    - contains implementation of inception-v3 deep network 包含incepa -v3深度网络的实现.
      - defining inception-v3 architecture ([inception_model.py](camelyon16/inception/slim/inception_model.py))
      - 定义inception-v3架构 ([inception_model.py](camelyon16/inception/slim/inception_model.py))
      - training inception-v3 ([inception_train.py](camelyon16/inception/inception_train.py))
      - 培训inception-v3 ([inception_train.py](camelyon16/inception/inception_train.py))
      - evaluating inception-v3 ([inception_eval.py](camelyon16/inception/inception_eval.py))
      - 评估inception-v3 ([inception_eval.py](camelyon16/inception/inception_eval.py))
      - implementation of TF-Slim ([slim](camelyon16/inception/slim))
      - 实现TF-Slim ([slim](camelyon16/inception/slim))

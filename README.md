# GIDR
This repository contains the source code for our paper " *Global-integrated and Drift-rectified Imprinting for Few-Shot Remote Sensing Object Detection* " by Bowei Yan, Gong Cheng, Chunbo Lang, and Junwei Han.

**abstract:** *Few-Shot Object Detection (FSOD) in remote sensing images is a marginally explored but highly challenging task that focuses on identifying unseen classes of objects with a limited number of annotations. Current FSOD approaches often fail to accurately localize the foreground and misalign targets with various orientations, resulting in poor detection performance. For this purpose, we develop a fresh and powerful meta-learning framework based on the idea of imprinting, which leverages tailored support information to model the region correlation between the query and support objects in the different stage. Specifically, a global-integrated scheme is first proposed to guide the generation of high-quality proposals through increasing the activation of foreground features and integrating support global information. Considering the orientation discrepancy of objects in query and support sets, we further introduce a drift-rectified technique to achieve adaptive alignment by implicitly capturing the positional correspondence between the two sets. In stark contrast to conventional FSOD approaches, our method can effectively extract key clues and establish directional relationships between objects from different training sets, leading to better generalization capability. Extensive experiments on two standard benchmarks (DIOR and NWPU VHR-10.V2) manifest the effectiveness, and our proposed method exhibits superior performance to other competitors with similar motivation.*

---
![Image text](https://github.com/Ybowei/GIDR/blob/main/picture/method.jpg)
---


## 📑 Table of Contents

* Global-integrated and Drift-rectified Imprinting for Few-Shot Remote Sensing Object Detection
  * Table of Contents
  * Installation
  * Code Structure
  * Data Preparation
  * Model training and evaluation on DIOR and NWPU VHR-10.v2
    * Base training
    * Model Fine-tuning
    * Evaluation
  * Model Zoo


## 🧩 Installation

Our code is based on [MMFewShot](https://github.com/open-mmlab/mmfewshot/tree/main) and please refer to [install.md](https://github.com/open-mmlab/mmfewshot/blob/main/docs/en/install.md) for installation of MMFewShot framwork. 
Please note that we used detectron 0.1.0 in this project. Higher versions of detectron might report errors.


## 🏰 Code Structure

* **configs:** Configuration files
* **checkpoints:** Checkpoint
* **Weights:** Pretraing models
* **Data:** Datasets for base training and finetuning
* **mmfewshot:** Model framework
* **Tools:** analysis and visualize tools

## 💾 Data Preparation

* Our model is evaluated on two FSOD benchmarks DIOR and NWPU-VHR following the previous work [Attention-RPN](https://github.com/fanq15/FewX).
* Please prepare the original [DIOR](https://pan.baidu.com/s/1iLKT0JQoKXEJTGNxt5lSMg#list/path=%2F) and NWPU [VHR-10.v2](https://pan.baidu.com/s/1hqwzXeG?_at_=1728709381194#list/path=%2F) datasets and also the few-shot datasets in the folder ./data/dior and ./data/nwpu_vhr respectively.
* please refer to [Data Preparation](https://github.com/Ybowei/UNP/blob/main/data/preparation/README.md) for more detail.

## 📖 Model training and evaluation on the both DIOR and NWPU VHR-10.v2

* We have two steps for model training, first meta-base-training the model over base classes, and then meta-fine-tuning the model over novel classes.
* The training script for base training is
  ```Python
  sh script/dist_train_base.sh

 * After model base training, we perform 3/5/10/20-shot fine-tuning over novel classes, and the training script is
   ```Python
   sh script/dist_train_finetuning.sh

 * We evaluate our model on the four splits in DIOR and two splits in VHR-10.v2. The evaluate script is
   ```Python
   sh script/dist_test_voc.sh

 ## 📚 Model Zoo
* We provided both the base-trained models and novel-finetuning models for the both two benchmarks. The model links are [Baidu Drive]().

 ## 👏 Acknowledgement
* This repo is developed based on [Attention-RPN](https://github.com/fanq15/FewX), [TFA](https://github.com/ucbdrive/few-shot-object-detection), and [mmfewshot](https://github.com/open-mmlab/mmfewshot/tree/main). Thanks for their wonderful codebases.

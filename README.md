## Introduction
This repo contains the official PyTorch implementation of the paper: Exemplar-Free Incremental Deepfake Detection.


<span id='environment'/>

### 1. Quick Start

<span id='install_environment'/>

#### 1.1 Environment Installation

Clone the repository locally:

```
git clone https://github.com/woody-panda/ForgeryGPT.git 
```
Install the required packages:

```
pip install -r requirements.txt
```

<span id='download_imagebind_model'/>

#### 1.2 Prepare ImageBind Checkpoint:

You can download the pre-trained ImageBind model using [this link](https://dl.fbaipublicfiles.com/imagebind/imagebind_huge.pth). After downloading, put the downloaded file (imagebind_huge.pth) in [[./pretrained_ckpt/imagebind_ckpt/]](./pretrained_ckpt/imagebind_ckpt/) directory. 

<span id='download_vicuna_model'/>

#### 2.3 Prepare Vicuna Checkpoint:

To prepare the pre-trained Vicuna model, please follow the instructions provided [[here]](./pretrained_ckpt#1-prepare-vicuna-checkpoint).

<span id='download_anomalygpt'/>

#### 2.4 Prepare Delta Weights of AnomalyGPT:

We use the pre-trained parameters from [PandaGPT](https://github.com/yxuansu/PandaGPT) to initialize our model. You can get the weights of PandaGPT trained with different strategies in the table below. In our experiments and online demo, we use the Vicuna-7B and `openllmplayground/pandagpt_7b_max_len_1024` due to the limitation of computation resource. Better results are expected if switching to Vicuna-13B.

| **Base Language Model** | **Maximum Sequence Length** |            **Huggingface Delta Weights Address**             |
| :---------------------: | :-------------------------: | :----------------------------------------------------------: |
|  Vicuna-7B (version 0)  |             512             | [openllmplayground/pandagpt_7b_max_len_512](https://huggingface.co/openllmplayground/pandagpt_7b_max_len_512) |
|  Vicuna-7B (version 0)  |            1024             | [openllmplayground/pandagpt_7b_max_len_1024](https://huggingface.co/openllmplayground/pandagpt_7b_max_len_1024) |
| Vicuna-13B (version 0)  |             256             | [openllmplayground/pandagpt_13b_max_len_256](https://huggingface.co/openllmplayground/pandagpt_13b_max_len_256) |
| Vicuna-13B (version 0)  |             400             | [openllmplayground/pandagpt_13b_max_len_400](https://huggingface.co/openllmplayground/pandagpt_13b_max_len_400) |

Please put the downloaded 7B/13B delta weights file (pytorch_model.pt) in the [./pretrained_ckpt/pandagpt_ckpt/7b/](./pretrained_ckpt/pandagpt_ckpt/7b/) or [./pretrained_ckpt/pandagpt_ckpt/13b/](./pretrained_ckpt/pandagpt_ckpt/13b/) directory. 


<span id='data_preparation'/>

#### 2.1 Data Preparation:

You can download MVTec-AD dataset from [[this link]](https://www.mvtec.com/company/research/datasets/mvtec-ad/downloads) and VisA from [[this link]](https://github.com/amazon-science/spot-diff). You can also download pre-training data of PandaGPT from [[here]](https://huggingface.co/datasets/openllmplayground/pandagpt_visual_instruction_dataset/tree/main). After downloading, put the data in the [[./data]](./data/) directory.

The directory of [[./data]](./data/) should look like:

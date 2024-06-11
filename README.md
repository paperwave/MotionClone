# MotionClone
This repository is the official implementation of [MotionClone](https://arxiv.org/abs/2406.05338). It is a training-free framework that enables motion cloning from a reference video to control text-to-video generation.
<details><summary>Click for the full abstract of MotionClone</summary>

> We propose MotionClone, a training-free framework that enables motion cloning from a reference video to control text-to-video generation. We employ temporal attention in video inversion to represent the motions in the reference video and introduce primary temporal-attention guidance to mitigate the influence of noisy or very subtle motions within the attention weights. Furthermore, to assist the generation model in synthesizing reasonable spatial relationships and enhance its prompt-following capability, we propose a location-aware semantic guidance mechanism that leverages the coarse location of the foreground from the reference video and original classifier-free guidance features to guide the video generation.
</details>

**[MotionClone: Training-Free Motion Cloning for Controllable Video Generation](https://arxiv.org/abs/2406.05338)** 
</br>
[Pengyang Ling*](https://github.com/LPengYang/),
[Jiazi Bu*](https://github.com/Bujiazi/),
[Pan Zhang<sup>†</sup>](https://panzhang0212.github.io/),
[Xiaoyi Dong](https://scholar.google.com/citations?user=FscToE0AAAAJ&hl=en/),
[Yuhang Zang](https://yuhangzang.github.io/),
[Tong Wu](https://wutong16.github.io/),
[Huaian Chen](https://scholar.google.com.hk/citations?hl=zh-CN&user=D6ol9XkAAAAJ),
[Jiaqi Wang](https://myownskyw7.github.io/),
[Yi Jin<sup>†</sup>](https://scholar.google.ca/citations?hl=en&user=mAJ1dCYAAAAJ)
(*Equal Contribution)(<sup>†</sup>Corresponding Author)

<!-- [Arxiv Report](https://arxiv.org/abs/2307.04725) | [Project Page](https://animatediff.github.io/) -->
[![arXiv](https://img.shields.io/badge/arXiv-2406.05338-b31b1b.svg)](https://arxiv.org/abs/2406.05338)
[![Project Page](https://img.shields.io/badge/Project-Website-green)](https://bujiazi.github.io/motionclone.github.io/)
<!-- [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/app-center/openxlab_app.svg)](https://bujiazi.github.io/motionclone.github.io/) -->
<!-- [![Hugging Face Spaces](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Spaces-yellow)](https://bujiazi.github.io/motionclone.github.io/) -->

![teaser](__assets__/teaser.gif)

## 🚀 Method Overview
<div align="center">
    <img src='__assets__/framework.jpg'/>
</div>

As illustrated in the framework above, MotionClone comprises two core components in its guidance stage: **Primary Temporal-Attention Guidance** and **Location-Aware Semantic Guidance**, which operate synergistically to provide comprehensive motion and semantic guidance for controllable video generation.

## 🔧 Preparations
### Setup repository and conda environment

```
git clone https://github.com/Bujiazi/MotionClone.git
cd MotionClone

conda env create -f environment.yaml
conda activate motionclone
```

### Download Stable Diffusion V1.5

```
git lfs install
git clone https://huggingface.co/runwayml/stable-diffusion-v1-5 models/StableDiffusion/
```

### Prepare Community Models

Manually download the community `.safetensors` models from [RealisticVision V5.1](https://civitai.com/models/4201?modelVersionId=130072) and save them to `models/DreamBooth_LoRA`. 

### Prepare AnimateDiff Motion Modules

Manually download the AnimateDiff modules from [AnimateDiff](https://github.com/guoyww/AnimateDiff), we recommend [`v3_adapter_sd_v15.ckpt`](https://huggingface.co/guoyww/animatediff/blob/main/v3_sd15_adapter.ckpt) and [`v3_sd15_mm.ckpt.ckpt`](https://huggingface.co/guoyww/animatediff/blob/main/v3_sd15_sparsectrl_scribble.ckpt). Save the modules to `models/Motion_Module`.

## 🎈 Quick Start

### Perform DDIM Inversion
```
python invert.py --config configs/example.yaml
```
### Perform Motion Cloning
```
python sample.py --config configs/example.yaml
```
## 🏗️ Todo
- [ ] Release Gradio demo
- [ ] Release the MotionClone code (We plan to release the code in about **two weeks**!)
- [x] Release paper

## 📎 Citation 

```
@misc{ling2024motionclone,
      title={MotionClone: Training-Free Motion Cloning for Controllable Video Generation}, 
      author={Pengyang Ling and Jiazi Bu and Pan Zhang and Xiaoyi Dong and Yuhang Zang and Tong Wu and Huaian Chen and Jiaqi Wang and Yi Jin},
      year={2024},
      eprint={2406.05338},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```

## 📣 Disclaimer

This is official code of MotionClone.
All the copyrights of the demo images and audio are from community users. 
Feel free to contact us if you would like remove them.

## 💞 Acknowledgements
The code is built upon the below repositories, we thank all the contributors for open-sourcing.
* [AnimateDiff](https://github.com/guoyww/AnimateDiff)
* [FreeControl](https://github.com/genforce/freecontrol)

# Image Forensics OSN

An official implementation code for paper "Robust Image Forgery Detection against Transmission over Online Social Networks"

## Table of Contents

- [Background](#background)
- [Dependency](#dependency)
- [Usage](#usage)
- [Citation](#citation)
- [Acknowledgments](#acknowledgments)


## Background

The increasing abuse of image editing software causes the authenticity of digital images questionable. Meanwhile, the widespread availability of online social networks (OSNs) makes them the dominant channels for transmitting forged images to report fake news, propagate rumors, etc. Unfortunately, various lossy operations, e.g., compression and resizing, adopted by OSNs impose great challenges for implementing robust image forgery detection, as shown in the below figure.

<p align='center'>  
  <img src='https://github.com/HighwayWu/ImageForensicsOSN/blob/main/imgs/demo.jpg' width='550'/>
</p>
<p align='center'>  
  <em>The detection results of DFCN (TIFS 2021) and ours by using an original forgery and the forgery transmitted through OSN. The right woman in the forgery is spliced (forged).</em>
</p>

To fight against the OSN-shared forgeries, in this work, a novel robust training scheme is proposed. Firstly, we design a baseline detector, which won top ranking in a recent certificate forgery detection competition. Then we conduct a thorough analysis of the noise introduced by OSNs, and decouple it into two parts, i.e., *predictable noise* and *unseen noise*, which are modelled separately. The former simulates the noise introduced by the disclosed (known) operations of OSNs, while the latter is designed to not only complete the previous one, but also take into account the defects of the detector itself. We finally incorporate the modelled noise into a robust training framework, significantly improving the robustness of the image forgery detector.

<p align='center'>
  <img src='https://github.com/HighwayWu/ImageForensicsOSN/blob/main/imgs/framework.jpg' width='770'/>
</p>
<p align='center'>  
  <em>The overview of our proposed training scheme and corresponding testing phase.</em>
</p>

<p align='center'>
  <img src='https://github.com/HighwayWu/ImageForensicsOSN/blob/main/imgs/cmp.jpg' width='770'/>
</p>
<p align='center'>  
  <em>A qualitative comparison for the detection of OSN-transmitted forgeries. For each row, the images from left to right are forgery (input), ground-truth, detection result (output) generated by MT-Net (CVPR 2019), NoiPri (TIFS 2020), ForSim (TIFS 2020), DFCN (TIFS 2021) and ours, respectively. The forgeries in each group from top to bottom are the cases without OSN transmission, and with Facebook, Whatsapp, Weibo and Wechat transmissions, respectively.</em>
</p>

Furthermore, we build a public forgeries dataset based on four existing datasets, through uploading and downloading over the platforms of Facebook, Whatsapp, Weibo, and Wechat, respectively.

## Dependency

- torch 1.6.0
- tensorflow 1.8.0

## Usage

For testing:
```bash
python test.py
```
Then the model will detect the images in the `data/input/` and save the results in the `data/output/` directory.

**Note 1: The pretrained weights can be downloaded from:
[Google Drive](https://drive.google.com/file/d/1scOAVxvqYSfRi4s7s0crk2Ieqn5Cm6r6/view?usp=sharing) or 
[Baidu Yun (Code: n2ai)](https://pan.baidu.com/s/17W14E3pQLyPia14Kq8QeQg)**

**Note 2: The collected OSN-transmitted dataset can be downloaded from:
[Google Drive](https://drive.google.com/file/d/1uMNZdhX3bYAZNcVGlkCvrnj5lSLW1ld5/view?usp=sharing) or 
[Baidu Yun (Code: nfsc)](https://pan.baidu.com/s/12DQhLT9AQe3G1my6C4ZJug)**

## Citation

If you use this code/dataset for your research, please consider citing our paper:
```
@article{imageforensicsOSN,
  title={Robust Image Forgery Detection against Transmission over Online Social Networks},
  author={Haiwei Wu and Jiantao Zhou and Jinyu Tian and Jun Liu and Yu Qiao},
}
```
And the references of the original dataset:
```
@article{DSO,
  title={Exposing digital image forgeries by illumination color classification},
  author={T. Carvalho and C. Riess and E. Angelopoulou and H. Pedrini and A. Rezende Rocha},
  journal={IEEE Trans. Inf. Forensics and Security},
  volume={8},
  number={7},
  pages={1182--1194},
  year={2013},
  publisher={IEEE}
}

@inproceedings{Columbia,
  title={Detecting image splicing using geometry invariants and camera characteristics consistency},
  author={Y. Hsu and S. Chang},
  booktitle={IEEE Inter. Conf. Multim. Expo},
  pages={549--552},
  year={2006},
  organization={IEEE}
}

@misc{NIST,
  title = {Nist nimble 2016 datasets},
  howpublished = {\url{https://www.nist.gov/itl/iad/mig/nimble-challenge-2017-evaluation/}},
}

@inproceedings{CASIA,
  title={Casia image tampering detection evaluation database},
  author={J. Dong and W. Wang and T. Tan},
  booktitle={IEEE China Summit Inter. Conf. Signal Info. Proc.},
  pages={422--426},
  year={2013},
  organization={IEEE}
}
```

## Acknowledgments
- Part of the network codes are based on the [SCSE-U-Net](https://github.com/maloyan/Roscosmos)
- The [Tianchi Competition](https://tianchi.aliyun.com/competition/entrance/531812/introduction)

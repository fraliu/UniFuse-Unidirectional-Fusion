

# UniFuse (RAL+ICRA2021)

Office source code of paper **UniFuse: Unidirectional Fusion for 360$^\circ$ Panorama Depth Estimation**, [arXiv](https://arxiv.org/abs/2102.03550), [Demo](https://youtu.be/9vm9OMksvrc)



# Preparation

#### Installation

Environments


* python 3.6
* Pytorch >= 1.0.0
* CUDA >= 9.0


Install requirements

```bash
pip install -r requirements.txt
```

#### Datasets 

Please download the preferred datasets,  i.e., [Matterport3D](https://niessner.github.io/Matterport/), [Stanford2D3D](http://3dsemantics.stanford.edu/), [3D60](https://vcl3d.github.io/3D60/) and [PanoSUNCG](https://fuenwang.ml/project/360-depth/). For Matterport3D, please preprocess it following [M3D-README.md](UniFuse/Matterport3D/README.md).



# Training 

#### UniFuse on Matterport3D

```
python train.py --data_path $DATA_PATH \
-dataset matterport3d \
--model_name Matterport3D_UniFuse \
--batch_size 6 \
--num_epochs 100 \
--height 512 \
--width 1024 \
--imagenet_pretrained \
--net UniFuse 
```

#### Equirectangular baseline on Matterport3D

```
python train.py --data_path $DATA_PATH \
-dataset matterport3d \
--model_name Matterport3D_Equi \
--batch_size 6 \
--num_epochs 100 \
--height 512 \
--width 1024 \
--imagenet_pretrained \
--net Equi 
```

It is similar for other datasets. 


# Evaluation  

#### Pre-trained models

The pre-trained models of UniFuse for 4 datasets are available, [Matterport3D](https://drive.google.com/drive/folders/1Dx7QR4ypujgLbyOo1zu4vIYXbqf95ToE?usp=sharing), [Stanford2D3D](https://drive.google.com/drive/folders/1q3LP9tyWi18yJwmhdjVn7dGUOsU3AH9G?usp=sharing), [3D60](https://drive.google.com/drive/folders/1B79FX_LoJ6GrcqyP1PIh2jqsiYs30V6P?usp=sharing) and [PanoSUNCG](https://drive.google.com/drive/folders/1trwQ7orixAjxWVK8rFLAtaaAqIjRB6va?usp=sharing).

#### Test on a pre-trained model

```
python evaluate.py  --data_path $DATA_PATH --dataset matterport3d --load_weights_folder $MODEL_PATH 
```



## Citation

Please cite our paper if you find our work useful in your research.

```
@article{jiang2021unifuse,
      title={UniFuse: Unidirectional Fusion for 360$^{\circ}$ Panorama Depth Estimation}, 
      author={Hualie Jiang and Zhe Sheng and Siyu Zhu and Zilong Dong and Rui Huang},
	  journal={IEEE Robotics and Automation Letters},
	  year={2021},
	  publisher={IEEE}
}
```


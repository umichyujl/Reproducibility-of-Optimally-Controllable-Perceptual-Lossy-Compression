# Reproducibility of Optimally Controllable Perceptual Lossy Compression
This is the final project for EECS 553, Fall 2022. Reproduced from https://github.com/ZeyuYan/Controllable-Perceptual-Compression, made some modifications. Run everything on Google Colab.

# RGB experiments
## Directory introduction
1. **src**: all the utility functions are stored in here like loss, dataset, and some helper functions.
2. **main function**: contains all kinds of version of training files. As we trained many models with different hyperparameters, a few changes are made in each .py but most of it are the same. If you want to use the train.py, pay attention to the details.
3. **experiments**: contains the weights files for ($E_d$ and $G_d$) for different models and the training info. [link](https://drive.google.com/drive/folders/130b0mzRc1Vy1M8HTzJkl6fcbxkRImcCA?usp=share_link)
4. **data**: contains all the training dataset, testing dataset, and results images. [link](https://drive.google.com/drive/folders/13jtWoLJ3o2YSTddJ1JXVMpvhL83Z2XNu?usp=share_link)
5. **ckpt**: contains the weights files for $G_p$ for different models [link](https://drive.google.com/drive/folders/1-07_sWjMcXq_OOo2pODy3G-Sl7RQlEIz?usp=share_link)
6. **default_config.py**: hyperparameter settings
7. **compress2.py**: to generate compressed image.
9. **demo.ipynb**: basic training and testing process.

## training code
### Framework A
`python train_A.py --model_type compression_gan --name stage_A --regime low ` 

### Framework B
#### stage 1
`python train_A.py  --name stage_A --regime low ` 

#### stage 2
`python train2.py --model_type compression_gan --regime low --warmstart -ckpt ./model/MMSE_model.pt`
- ckpt: states the weight path for $E_d$ and $G_d$ 

## Testing code
`python3 compress2.py 
--metrics --reconstruct 
--ckpt_path "/weight/path/for/Ed/and/Gd" 
--decoder "/weight/path/for/Gp" `

# MNIST experiments
## Directory Tutorial
**train.py**: training dataset. \
**test.py**: testing dataset and plotting figures with different $\alpha$. \
**train_beta.py**: using for tuning $\beta$. \
**data**: MNIST, Fashion-MNIST and EMNIST are pre-loaded dataset in Pytorch.

1. Please download all the .py and .ipynb files.
2. Open the **MNIST_code.ipynb** on Google Colab.
3. The GPU is needed. Please change the runtime type to GPU first.
4. To train different dataset, please change the dataset loaded by `train_loader` in **train.py** or **train_beta.py**.
5. Remember to change the file paths of generators into the right one before running **test.py**.




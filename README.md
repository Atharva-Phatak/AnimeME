# **AnimeGAN Pytorch**


[![Hugging Face Spaces](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Spaces-brightgreen)](https://huggingface.co/spaces/Atharva-Phatak/AnimeGAN)  ![License](https://img.shields.io/github/license/Atharva-Phatak/AnimeGAN?color=blue&label=Apache)
***

Pytorch implementation of AnimeGAN for fast photo animation.
* *AnimeGAN: a novel lightweight GAN for photo animation* - [Semantic scholar](https://www.semanticscholar.org/paper/AnimeGAN%3A-A-Novel-Lightweight-GAN-for-Photo-Chen-Liu/10a9c5d183e7e7df51db8bfa366bc862262b37d7#citing-papers)


* **[Official online demo](https://huggingface.co/spaces/Atharva-Phatak/AnimeGAN) is integrated to [Huggingface Spaces](https://huggingface.co/spaces) with [Gradio](https://github.com/gradio-app/gradio)**.
***

## **Documentation**

### **1. Install required dependencies**

* Create virtual environment in python.
* Install dependencies using the following command
```bash
pip install -r requirements.txt
```

### **2. Prepare dataset**

* Download the dataset from [AnimeGANV2 repo](https://github.com/TachibanaYoshino/AnimeGANv2)
* Extract the dataset to the desired folder. Run the below command if there are no smooth images in your style folder i.e Hayao, Paprika, etc

```bash
python data_process --data_dir <Path to the stored location of dataset> --dataset <The name of the style data i.e Hayao/Paprika/Shenkai> --image-size 256
```


### **3. Train animeGAN**

* To train the animeGAN from command line, you can run `train_model.py` as the following:
* You can play around the parameters in params.yaml file avaiable in ```Params``` folder.

```bash
python train_model.py
```

### **3. Transform images**

To convert images in a folder or single image, run `inference_image.py`, for example:

> --src and --dest can be a path to file : "./images/fake.png" or something like this.

```bash
python infer.py --checkpoint_path <path to saved checkpoint> --source_path <path to src image> --dest_path <path to where image should be saved>
```

## Anime transformation results


| Input | Output(Hayao style) |
|--|--|
|![c1](./outputs/arch.jpg)|![g1](./outputs/fake-arch.png)|
|![c1](./outputs/clay-banks-org.jpg)|![g1](./outputs/city-banks-anime.png)|
|![c1](./outputs/kimono-street-org.jpg)|![g1](./outputs/kimono-street.png)|
|![c1](./outputs/Japan.jpg)|![g1](./outputs/nigh-street-fake.png)|
|![c1](./outputs/cityscape.jpg)|![g1](./outputs/cityscape-fake.png)|
|![c1](./outputs/india.jpg)|![g1](./outputs/india-fake.png)|

## Training Curves
Below is how my loss looked like for overall training. All the tracking is done using ML-Flow.

![training](./outputs/training-curves.png)

**Note : Batch size will has significant effect on training and results. Atleasts that's what I observed.**

## Things to remember
* You can train this on any dataset but images should be high resolution especially the style images.
* Read the paper to understand the implementation and process.
* It is very important to track your experiments, I used [mlflow](https://mlflow.org/) to track my experiment and parameters.


## Work in Progress
- [ ] Custom anime dataset
- [ ] TensorRT/Onnx models.

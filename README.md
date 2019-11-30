# Generative Adversarial Network for Medical Imaging
# MI-GAN

##Data
Copy your data into the two sub-directories DRIVE and STARE inside the directory Data.
To save space, we have removed any image data from many of the sub-directories however, we have kept the empty directory there so that you may still be able to use the same path for a sub-directory. This is to help you to retain the hierarchy of the folders.

##Credits

**Contribution from Talha Iqbal and Hazrat Ali**

_The following code is associated to the paper_

Talha Iqbal and Hazrat Ali, Generative Adversarial Network for Medical Images (MI-GAN), Journal of Medical System, November 2018, 42:231. Doi: 10.1007/s10916-018-1072-9

Avaiable at: [https://link.springer.com/article/10.1007/s10916-018-1072-9]

PDF arxiv link: [https://arxiv.org/abs/1810.00551]


#How to use this code.

## Package Dependency
- tensorflow 1.16.0
- python 3.5.3
- numpy 1.14.2
- matplotlib 2.0.2
- pillow 5.0.0
- scikit-image 0.13.0
- scikit-learn 0.19.0
- scipy 0.19.0

## Download Data
Original data file strucure was modified for convenience by [Jaemin Son](https://www.vuno.co/team).  
Download data from [here](https://bitbucket.org/woalsdnd/v-gan/src/04e60e8baee6d03721b0d6b0990255bfa115dab6?at=master) and copy data file in the same directory with codes file as following Directory Hierarchy.  

## Directory Hierarchy
```
.
+-- codes
¦   +-- dataset.py
¦   +-- evaluation.py
¦   +-- main.py
¦   +-- model.py
¦   +-- solver.py
¦   +-- TensorFlow_utils.py
¦   +-- utils.py
+-- data
¦   +-- DRIVE
¦   +-- STARE
+-- evaluation (get after running evaluation.py)
¦   +-- DRIVE
¦   +-- STARE
+-- results
¦   +-- DRIVE
¦   +-- STARE
```
**codes:** source codes  
**data:** original data. File hierarchy is modified for convenience.  
**evaluation:** quantitative and qualitative evaluation. (*get after running evaluation.py*)  
**results:** results of other methods. These image files are retrieved from [here](http://www.vision.ee.ethz.ch/~cvlsegmentation/driu/downloads.html).  

## Training
Move to **codes** folder and run main.py  
```
python main.py --train_interval=<int> --ratio_gan2seg=<int> --gpu_index=<int> --discriminator=[pixel|patch1|patch2|image] --batch_size=<int> --dataset=[DRIVE|STARE] --is_test=False
```  
- models will be saved in './codes/{}/model\_{}\_{}\_{}'.format(dataset, disriminator, train_interval, batch_size)' folder, e.g., './codes/STARE/model_image_100_1' folder.  
- smapled images will be saved in './codes/{}/sample_\_{}\_{}\_{}'.format(dataset, disriminator, train_interval, batch_size)', e.g., './codes/STARE/sample_image_100_1' folder.  

### Arguments
**train_interval:** training interval between discriminator and generator, default: 1    
**ratio_gan2seg:** ratio of gan loss to seg loss, default: 10  
**gpu_index:** gpu index, default: 0  
**discriminator:** type of discriminator [pixel|patch1|patch2|image], default: image  
**batch_size:** batch size, default: 1  
**dataset:** dataset name [DRIVE|STARE], default: STARE  
**is_test:** set mode, default: False  

**learning_rate:** initial learning rate for Adam, default: 2e-4  
**beta1:** momentum term of Adam, default: 0.5  
**iters:** number of iterations, default: 50000  
**print_freq:** print loss information frequency, default: 100  
**eval_freq:** evaluation frequency on validation data, default: 500  
**sample_freq:** sample generated image frequency, default: 200  

**checkpoint_dir:** models are saved here, default: './checkpoints'  
**sample_dir:** sampled images are saved here, default: './sample'  
**test_dir:** test images are saved here, default: './test'  

## Test
```
python main.py --is_test=True --discriminator=[pixel|patch1|patch2|image] --batch_size=<int> --dataset=[DRIVE|STARE]
```
- Outputs of inferece are generated in 'seg_result_{}\_{}\_{}'.format(discriminator, train_interval, batch_size) folder, e.g., './codes/STARE/seg_result_image_100_1' folder.  
- Make sure model already trained with defined dataset, discriminator, training interval, and batch size.

## Evaluation
**Note:** Copy predicted vessel images to the ./results/\[DRIVE|STARE\]/V-GAN folder  
```
python evaluation.py
```
Results are generated in **evaluation** folder. Hierarchy of the folder is  
```
.
+-- DRIVE
¦   +-- comparison
¦   +-- measures
¦   +-- vessels
+-- STARE
    +-- comparison
    +-- measures
    +-- vessels
```

**comparison:** difference maps between V-GAN and gold standard  
**measures:** AUC_ROC and AUC_PR curves  
**vessels:** vessels superimposed on segmented masks  
*Area Under the Curve* (AUC), *Precision and Recall* (PR), *Receiver Operating Characteristic* (ROC)  



##Support
We would be offer any possible support as long as it does not have conflict with our own work committements. 

##Disclaimer
In no event shall we be liable to any party for direct, indirect, special, incidental or consequential damages, including lost profis, arising out of the use of this software code and its documentation.





# Generative Adversarial Network for Medical Imaging
# MI-GAN

_The code is associated to the following paper_

Talha Iqbal and Hazrat Ali, Generative Adversarial Network for Medical Images (MI-GAN), Journal of Medical System, November 2018, 42:231. Doi: 10.1007/s10916-018-1072-9

Avaiable at: [https://link.springer.com/article/10.1007/s10916-018-1072-9]

PDF arxiv link: [https://arxiv.org/abs/1810.00551]
## Credits

**Contribution from Talha Iqbal and Hazrat Ali**

## Data

Copy your data into the two sub-directories DRIVE and STARE inside the directory Data.
To save space, we have removed any image data from many of the sub-directories however, we have kept the empty directory there so that you may still be able to use the same path for a sub-directory. This is to help you to retain the hierarchy of the folders.




---

# How to use this code.

## Package Dependency
- tensorflow 1.16.0
- python 3.5.3
- numpy 1.14.2
- matplotlib 2.0.2
- pillow 5.0.0
- scikit-image 0.13.0
- scikit-learn 0.19.0
- scipy 0.19.0


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

## Support

We would be offer any possible support as long as it does not have conflict with our own work commitments. 

## Disclaimer

In no event shall we be liable to any party for direct, indirect, special, incidental or consequential damages, including lost profis, arising out of the use of this software code and its documentation.





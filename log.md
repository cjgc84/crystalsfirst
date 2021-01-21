## Introduction:

Propulsion Academy DS_2020_09 Final Project:
Detection of protein crystals in images from crystallization screening using
deep learning.


## Requirements:


## Recommended modules:


## Configuration:


## Maintainers:
Linda Wymann  
Claudio Cunha  


## LOG:
#######################  26/10/2020 ###################  

26.10.2020 

- Set up GCP

- Created Google Drive folder

- tried to undestand the available sample images metadata
	- size: 1280 x 960
	- channels: 3 (RGB)  
	- 

   
- discussed image manipulation (to be determined)
	- padding: none  (to be confirmed)
	- segmentation: TBD
	- augmentation: TBD
	- labels: TBD  
	- created temporary folders with "crystal", "clear" samples for experimenting with models  
	-

   
- Discussed possible model strategies (to be determined)
	- One-shot learning
	- grad-CAM
	- Transfer Learning: VGG, ResNet, Inception, EfficientNet, etc
	- Classification: Random Forest, Regression
	- Test/Train split for such amount of data (800GB)  
	-

  
- ran grad-CAM with different models (no training applied besides pre-trained models)
	- VGG 16		(bad)
	- ResNet50		(best)
	- EfficientNetB7	(good)
	- InceptionV3		(bad)	
	- weights = imagenet  
	-

  
- Collected questions for Serghei
	- Difference between crystilized proteins and precipitated proteins?
	- Classification. Binary or multi-class? 
	- How to label images? 
	- Why are there blurry pictures? Are they useful? Do humans use them?	
	- Back-end solution integration with front-end. Any specific deliverables for project team?
	- Further communication with Crystals First? Point of contact? Frequency?
	- GCP enviroment (GCP vs. Colab)  
	-

  
- created overall project plan
	- rough draft plan created. Will log plan after first meeting with Crystals First. 


#######################  27.10.2020  #######################  

- Data augmentation:  
	- Implemented

- Image resizing layer:
	- Implemented

- TransferLearning: 
- Training on ResNet50 and adding customized bottom layers 
	- Dropout: TBD
	- Flatten: TBD
	- Dense: implemented

- Test different output functions: TBD

- Opening last conv layer to backprop own weights
	- Implemented

- Meeting with Moritz Ruf from CrystalsFirst
	- multi-class task
	- possible labels: clear, crystal, clear precipitation, homogenous precip., inhomogenous precip., amorphous precip., "other"
	- time evolution to crystal is important
	- images ending with th will be ignored

#######################  28.10.2020  #######################

-General: 
	- download synching method gdrive / local drive to do a backup and easier to push to git
	- meeting with Moritz Ruf on labelling data (he labeled a batch for us since it took too long)
	- uploading labelled images (8 classes) to gdrive

	
-Model
	- function to unzip images from .tar files in gdrive to memory
	- upgrading model with dropout layer
	- changing class names according to the labels provided by Moritz
	- balancing classes using a sklearn's calculate class weights
	


#######################  29.10.2020  #######################

- Labeling, lots and lots of manual image labeling..... 		



#######################  30.10.2020  #######################

- Meeting with Crystals First
	- Cross-checking our labeling with Crystals First 
	- Discussion on model output and metrics


- TransferLearning: 
- Training on ResNet50 and adding customized bottom layers 
	- Dropout: implemented
	- Flatten: implemented
	- Dense: implemented

- How to do train/val/test split with directories.
	- Tried to create Test dataset from directory: Not successful yet

#######################  02.11.2020  #######################

- Worked on train / test / validation split from directory
- Tried to get efficient net and resnet working for a binary classification
- This did not work so we switched to multi classification (7 calsses). 
- This works slightly better or at least provides results we can work with. 
- Separated workbook to work on different models in parallel.
- ResNet seems to do a better job with the current settings. 

-> Goals for tmrw: Opening up more layer to train the weights on our images
-> Being able to pass an entire folder through prediction
-> claryfing deliverable once again. How does the model need to be implemented exactly? 

#######################  03.11.2020  #######################

- tried different model settings on efficient net and resnet
- tested inception V3 and got good "accuracy" metrics but poor predictions
- implement prediction 
- implemented F1 score as a metric instead of sparse categorical 
- meeting with Moritz Ruf, talked about implementation of the product
- got access to MRI project data and had a look at that
- incorporated blurry images

#######################  05.11.2020  #######################

- created VGG19 Model, openued up last block and then entire model for training
- only predicted one class (crystals) on all models
-> call with Nitin and Albin: Looked at preprocessing and loss function
- tweaked dense layer and class_mode and went for categorical cross entropy
- on ResNet Model: Created Confusion Matrix for predictions on Test_img by 
creating data frames from json and the predictions. 

#######################  06.11.2020  #######################

- Hyperparameter Tuning for ResNet, Efficient Net, Inception and VGG
- Tensorboard for all of them 
- Looking into RandomForest and talked to Nitin about that

#######################  08.11.2020  #######################

- Results from Hyperparameter Tuning are not convincing
- Further individual tuning, some models give ok results but nothing 
close to what we desired.
- Created larger data set and tested it on VGG, still no good results.


#######################  09.11.2020  #######################

- recreated new multi-class and binary image folder
- recreated test folder
- created json file that combined the labels for binary and multi-class
- ran resnet and inception on new data, still can't detect crystals. 
- talked to Moritz & Badru about new VM, set up meeting at 10:15 for Tuesday
- Email to DJ explaining our case and asking for advice


#######################  10.11.2020  #######################

- Talk with Moritz and Albin to set up VM
- waiting for more crystal images (different size)
- Grad-CAM on ResNet -> same result as base resnet since it's looking at the same layer
-> should ask DJ on how to choose the proper layer when applying GradCAM to a transfer learning model
- creating data frame to collect probabilities from all four models
- feeding random forest with these probabilites, getting good results
- trying to set up Colab Notebook using the new VM instance Moritz created, not successful. 

#######################  11.11.2020  #######################

- random forest -> train / test splitting new
- adapted images folder with new crystal images
- ran all models on new image data and looked at predictions
- tried connecting the VM to colab, not working at all


#######################  12.11.2020  #######################

- tried running one of the notebooks on jupyterlab instance on google cloud platform
- ran / improved VGG and inception


#######################  13.11.2020  #######################

- talked to Badru about the models and granted access to gdrive
- improved models based on Badru's usggestion and got some decent results
- ran GradCam on VGG and Inception and looked at the images which were missed
- ran a test folder on VGG -> no crystals were predicted

#######################  16.11.2020  #######################

- decided on Inception Model for final production
- cleaned up the notebook and project folder
- created readme.md file 
- confirmed the use of a VM from CrystalsFirst



#######################  18.11.2020  #######################

- first round of presentation
- finalized presentation
- talked to Moritz about presentation content and VM issues
- worked on connecting storage_4 with the VM for createjson
- then tried the same for prediction notebook


#######################  19.11.2020  #######################

- continued working on transferring notebooks to jupyterlab VM
	- loading images
	- loading pre-trained model 
	- creating a data frame as output

- started creating user manuals and enhanced the markdowns on the 
final notebooks




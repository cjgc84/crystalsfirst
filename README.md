<a href="https://propulsion.academy/"><img src="https://static.swissdevjobs.ch/pictures/propulsion-academy-logo.png" title="Propulsion Academy" alt="Learn how to become a Data Scientist with Propulsion Academy"></a>


# Detection of protein crystals in images from crystalization screening using deep learning

Crystallization of proteins is an essential step for determination of their molecular structure. The data is critical for design of new therapeutics and drugs.To identify conditions, where proteins crystalize thousands of conditions are screened in miniaturized settings using well plates. The monitoring is often conducted visually by a scientist,who evaluates the results on pre-defined days. This results in visual inspection of eg. 1200 images for one simple screen. The desired result of such screens are crystalized proteins in the well, but most of the wells(images) are empty. This activity is highly time-consuming and a reliable automation of thisprocess is desired. [Crystals First](https://crystalsfirst.com) will provide a large set of images.    


## Authors

[Claudio Cunha](https://www.linkedin.com/in/claudiojgcunha/)    
[Linda P. Wymann](https://www.linkedin.com/in/linda-p-wymann/)    


## Supervisors

[Albin Plathottathil](https://www.linkedin.com/in/albin-plathottathil/)    
[Badru Stanicki](https://www.linkedin.com/in/badrustanicki/)    
[Nitin Kumar](https://www.linkedin.com/in/drnitinkumar/)    


## Purpose 

Reliable classification/differentiation of images with or without protein crystals that will be passed on for manual evaluation by a crystallographer. The crystallographer could focus only on the images predicted as "crystals", thus saving labor time not looking at images predicted as "no crystal".    


## Data 

The images used for training and testing, the storage and the VM on google cloud were provided by Crystals First GmbH.

[Example images of crystals and non crystals](https://gitlab.propulsion-home.ch/datascience/bootcamp/final-projects/ds-2020-09/crystalsfirst/-/blob/master/03_presentation/Image_Crystals_example.PNG)


## Requirements

The "environment.yml" file contains all the necessary python packages.


## How to work with this repo

### [Part 1. Processing training data](https://gitlab.propulsion-home.ch/datascience/bootcamp/final-projects/ds-2020-09/crystalsfirst/-/tree/master/04_production/Training)

Run "Createjson.ipynb" notebook to process training data.     
This notebook creates a .JSON file needed during model training.     
The .JSON file will contain the true lables of each image in the trainig data set.    


### [Part 2. Training the model](https://gitlab.propulsion-home.ch/datascience/bootcamp/final-projects/ds-2020-09/crystalsfirst/-/tree/master/04_production/Training)

The following notebook depend on the created .JSON.    
Run "InceptionV3_Training.ipynb".     
Will use images stored at the "training_data" folder to train the model.    
Will use images stored at the "test" folder to test and evaluate model.    
Finally, will save a copy of the pre-trained model.    


### [Part 3. Predict](https://gitlab.propulsion-home.ch/datascience/bootcamp/final-projects/ds-2020-09/crystalsfirst/-/tree/master/04_production/Prediction)

Run "InceptionV3_Predicting.ipynb"    
Will load saved pre-trained model.     
Will request user input of destination folder with images to be predicted.     
After predictions, will return dataframe with image path, name, prediction and prediction confidence level.    


## Repo Structure

[01_notebooks](https://gitlab.propulsion-home.ch/datascience/bootcamp/final-projects/ds-2020-09/crystalsfirst/-/tree/master/01_notebooks): Contains a final version of the InceptionV3 notebooks which can be run in a colab environment. 
In the subfolder "research" you can find the ohter trail notebooks which were used during the project but
were not considered for the final version.  
  
[02_source](https://gitlab.propulsion-home.ch/datascience/bootcamp/final-projects/ds-2020-09/crystalsfirst/-/tree/master/02_source): Contains a single file called "image_labels.json" which is the result of the notebook "Createjson.ipynb"
and is required to run the prediction part of the notebooks.  
 
[03_presentation](https://gitlab.propulsion-home.ch/datascience/bootcamp/final-projects/ds-2020-09/crystalsfirst/-/tree/master/03_presentation): Contains the final presentation and a short presentation we gave Moritz Ruf in the second week of the
project.  

[04_production](https://gitlab.propulsion-home.ch/datascience/bootcamp/final-projects/ds-2020-09/crystalsfirst/-/tree/master/04_production): Contains the "production-ready" notebooks of Inception V3 which run on the VM of crystalsfirst. It also contains
a user manual for this set of notebooks. The code is adapted from the colab version to make it work on the VM instance provided by
crystalsfirst.  
 



 
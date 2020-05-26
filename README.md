# Machine Learning & DevOps Integration

# Task Given by Mr. Vimal Daga Sir Under MLOPs Training

# Task Overview :

This task has the following series of things to be done :

  * 1. Create container image that’s has Python3 and Keras or Sklearn  installed  using dockerfile 
  * 2. When we launch this image, it should automatically starts train the model in the container.
  * 3. Create a job chain of job1, job2, job3, job4 and job5 using build pipeline plugin in Jenkins 
  * 4.  Job1 : Pull  the Github repo automatically when some developers push repo to Github.
  * 5.  Job2 : By looking at the code or program file, Jenkins should automatically start the respective machine learning software installed interpreter install image container to deploy code  and start training( eg. If code uses CNN, then Jenkins should start the container that has already installed all the softwares required for the cnn processing).
  * 6. Job3 : Train your model and predict accuracy or metrics.
  * 7. Job4 : if metrics accuracy is less than 80%  , then tweak the machine learning model architecture.
  * 8. Job5: Retrain the model or notify that the best model is being created
  * 9. Create One extra job job6 for monitor : If container where app is running. fails due to any reason then this job should automatically start the container again from where the last trained model left

# Technologies Integrated :
Here we have integrated :
* Machine Learning Model
* Jenkins
* Git, Github
* Docker

# Project Description :

Machine Learning model training takes a lot of time and resources in the form of RAM and CPU. Also Data Scientists need to tweak the **model architectue and hyper parameter** several time and **retrain models for better accuracy**.This manual process can take lots of time, so we can use **Jenkins** to **automatically train model and if the desired accuracy is not achieved then Jenkins will tweak the model and retrain it.**  

## Machine Learning Model :
I have used two simple ways to **tweak the ML Model and manage the Hyper parameters**, which are - 

* command line input -

Depending upon the command line input given from the **Jenkins Job** the machine learning code will change the **architecture of model**
 by adding more **Dense layers or Convolve-Pooling layers** depending upon the Developer's ML code. 

* random library -

I have used random library to select different combinations of **hyper parameters** between given range while Jenkins Job retrain the model for better accuracy.

 Link to the ML model: https://github.com/disha1822/MLOPs-Task-ML-Part-

## DevOps Integration :

#### Job1(Pull Github Code) :

Whenever Developer pushes new ML model code in Github it copies it.

![a](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job1_1.png?raw=true)
![b](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job1_2.png?raw=true)
![c](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job1_3.png?raw=true)

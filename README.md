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

It is a simple job to copy Developer codeusing Poll SCM Trigger.We can use Github Webhook Triggers to decrease the computation.
Whenever Developer pushes new ML model code in Github it copies it.

![a](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job1_1.png?raw=true)
![b](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job1_2.png?raw=true)
![c](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job1_3.png?raw=true)

#### Job2(Launch Appropriate Environment) :

This will launch a Docker container with appropriate environment depending upon the ML model and also the code pre installed in the container.

![d](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job2_1.png?raw=true)
![e](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job2_2.png?raw=true)

When the container launched successfully with respective environment and model code installed in it, it will trigger Job3.

#### Job3(Train model) :

* It will train the ML model and retrieve the accuracy.
* **If accuracy is less than 80% job will be successful and it will trigger Job4 for retraining model.**
* **If accuracy is greater than 80% then it will mark biuld as failed.**
* If build fails the **Post Build Action** will run a python file for **sending mail to developer saying best model created and will not further trigger Job4 as we donot need to retrain in thisn case.**
* For the above Post Build Action we need to install **PostBuildScript Plugin**.

![f](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job3_1.png?raw=true)
![g](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job3_2.png?raw=true)
![h](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job3_3.png?raw=true)

#### Job4(Retrain model) :

* I have retrained the model for 5 times and retrieved accuracy each time.
* while training I have passed a command line input. If it is 1 then model will change its architecture by adding more Dense or Convolve layers.
* **If accuracy is greater than 80%, retraining stops** and it triggers Job5.

![i](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job4_1.png?raw=true)
![j](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job4_2.png?raw=true)

#### Job5(Sending Notification) :

It will simply run a python file to send email notification to the developer saying the best model is created.

![k](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job5_1.png?raw=true)
![l](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job5_2.png?raw=true)

#### Job6(Monitors Container) :

If container where app is running, fails due to any reason then this job will automatically start the container again from where the last trained model left.

![m](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job6_1.png?raw=true)
![n](https://github.com/disha1822/ML-DevOps-Integration/blob/master/job6_2.png?raw=true)

## Pipeline Looks Like :

![o](https://github.com/disha1822/ML-DevOps-Integration/blob/master/pipeline.png?raw=true)


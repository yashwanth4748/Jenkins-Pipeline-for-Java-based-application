# Jenkins-Pipeline-for-Java-based-application
![image](https://github.com/yashwanth4748/Jenkins-Pipeline-for-Java-based-application/assets/123750192/e7c4fdf2-866c-4a51-86c9-7b818d11ea21)

<h3 align="left">Languages and Tools:</h3>
Git,Jenkins,Maven,SonarQube,Docker,ArgoCD,Kubernetes


**Continuous Integration**<br>
First, we will create a webhook in Github where our source code is present<br>
The webhook is triggered whenever there is any commit or push occurs<br>
The jenkins will be notified using this webhook with the new update<br>
Then the jenkins which was installed on our EC2 instance will start the building the pipeline<br>
Here we not need to install the MAVEN, we can use docker agents in this project which comes with inbuilt maven<br>
The mavent then starts to build the code starting from unit testing of code<br>
Then from the unit testing stage, If it is successful then it moves to static code Analysis<br>
If it fails, then the email or slack notifications will be sent.<br>
Here we use, SonarQube for static code Aalysis, if it fails then the above step repeats<br>
Building the pipeline moves further with succesfful static code Analysis and continued by docker Agent<br>
Here we install the Docker Plugin in the jenkins, which is  useful to use the docker agents<br>
Then our docker image will be created and updated in the Docker Container Registry(docker Hub, ECR).<br>

**Continuous Delivery**<br>
We use Agro Image updater which continuously monitors the Docker Container Registry fand updates the images into Git<br>
In this project instead of Agro Image updater, I used shell script commands to do this process<br>
Once there is a change in the Git, the AgroCd Updates it to CI pipeline.<br>
Here the AgroCD always maintain the state between the Git and the kubernetes Cluster<br>
Here,AgroCd is present in the Kubernetes cluster which acts as a Controller.<br>
In this way, we succesfully created the **Jenkins Pipeline For Java Based Applications**<br>

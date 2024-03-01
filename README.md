# Jenkins-Pipeline-for-Java-based-application
![image](https://github.com/yashwanth4748/Jenkins-Pipeline-for-Java-based-application/assets/123750192/e7c4fdf2-866c-4a51-86c9-7b818d11ea21)

<h3 align="left">Languages and Tools:</h3>
Git,Jenkins,Maven,SonarQube,Docker,ArgoCD,Kubernetes


**Continuous Integration**<br>
First, we will create a webhook in Github where our source code is present.<br>
The webhook is triggered whenever a commit or push occurs.<br>
Jenkins will be notified using this webhook with the new update.<br>
Then Jenkins, which was installed on our EC2 instance, will start building the pipeline.<br>
Here, we do not need to install MAVEN; we can use docker agents in this project which come with inbuilt maven.<br>
The Maven then starts to build the code starting from unit testing of the code.<br>
From the unit testing stage, if it is successful, then it moves to static code analysis.<br>
If it fails, then email or Slack notifications will be sent.<br>
Here we use SonarQube for static code analysis; if it fails, then the above step repeats.<br>
Building the pipeline moves further with successful static code analysis and continued by docker agents.<br>
Here we install the Docker Plugin in Jenkins, which is useful to use the docker agents.<br>
Then our docker image will be created and updated in the Docker Container Registry (docker Hub, ECR).<br>

**Continuous Delivery**<br>
We use Agro Image Updater which continuously monitors the Docker Container Registry and updates the images into Git.<br>
In this project, instead of Agro Image Updater, I used shell script commands to do this process.<br>
Once there is a change in Git, AgroCd updates it to CI pipeline.<br>
Here, AgroCD always maintains the state between Git and the Kubernetes Cluster.<br>
AgroCD is present in the Kubernetes cluster, which acts as a Controller.<br>
In this way, we successfully created the Jenkins Pipeline For Java Based Applications.<br>

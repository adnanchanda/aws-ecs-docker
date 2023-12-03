# aws-ecs-docker
deploy docker container to a ecs cluster 


Step1
Build a docker image using "docker build -t express app ." command.
Run it on your local machine using "docker build -p 4200:300 (docker image id)" to check if the image is working on your local machine . You can check the application on "localhost:4200"

Step2
Now Login to your AWS account through your browser, After Logging in search Amazon ECR ->Create Repo -> Public ->write Repo Name -> click on Create Repo.

Step3
After the Repository is created click on the created repo and click on "view push commands" and copy paste eacg and every command in your IDE terminal.Now your image is pushed on AWS.

Step4
Now we need to create a cluster , for that we need to search Elastic container services(ECS)-> Create Cluster  -> Cluster Name -> provisioning model = On-Demand Insatnce ->  EC2 Instance Type = t2.micro -> EC@ AMI ID= Linux 2 AMI -> VPC=default -> Subnets = Default -> Create Cluster. After the cluster is  created click on the cluster and define the task to it 

Step5
For task definition click on task definition -> task name -> Task memory (MiB) = 100 -> Task CPU (unit) = 1vCPU -> Add container -> Contaier Name -> Image* = "copy the image id pushed on the ECR" -> Port Mapping = (Host port) = 4200 & (Container Port) = 3000 -> protocol TCP -> Add Container - Create Task Definition.

Step6
Now go back to ecs -> Run new task -> click on the task you created -> click on the cluster you created -> NUmber of tasks = 1 -> Run new task.

Step7 
Now go back to EC2 and change the inbound security groups of the EC2 to public .

Step8
Copy the Public IP of the EC2 and paste it like this "Public IP:4200".



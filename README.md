# docker-image-push-to-ecr
- A Python dockerized hello world app This repo aims at showing how simple it can be to build a Docker container running a Python (very simple) app, Once you understand how this simple example works, it's easy to apply it to bigger apps.
- **Steps to run directly the python code**
- It's highly recommended to install the (empty) dependencies in a virtual environment.
- **Creating the virtual environment:**
- ```
  virtualenv venv
  ```
- **Activating the virtual environment:**
- ```
  source venv/bin/activate
  ```
- **Running the code:**
- ```
  python app.py
  ```
- **Steps to run the python code withing a Docker container**
- **Build the image:**
- ```
  docker buildx build -t 'docker-build' /path/to/dockerfile
  ```
- **Run the container:**
- ```
  docker run docker-build
  ```
- **push to remote repo**
- ```
  git add .
  git commit -m "docker-image-push-to-ecr"
  git push origin main
  ```
- **create AWS IAM user**
- go to aws consol and serach IAM
- click on IAM and create user
- # Get Access Key ID and Secret Access Key for an IAM Account
- Using credentials associated with an IAM account is the recommended way to access AWS resources because you can control the permissions of an IAM user.

- In order to get an Access Key ID and Secret Access Key for an IAM AWS account:

- Open the IAM console
- In the sidebar click on Usersclick users
- Click on the Security Credentials tab, scroll down to the Access keys section and click on Create access key
- create access key iam user
- Download the file with the Access key id and Secret access key. Note that the Secret Access Key can only be retrieved at the moment of creation.
- **Create one AWS ECR repository:**

- First all of go to the AWS Management Console and search “ECR” in the search menu and click on the “Elastic Container Registry”.
- Then click on create a repository and choose private and then write your repository name into the given input field and create a repository.
- After creating your ECR repository, go back to your `main.yml` file and edit the field ‘ECR_REPOSITORY’, and enter the name of your ECR_REPOSITORY.

- **Add your AWS secrets to GitHub secrets**

- In order to access your AWS ECR registry, you’ve to add your AWS secrets (ACCESS_KEY and SECRET_KEY).
- Since these are credentials we can’t reveal them in public hence need to set them as Environment Variables which are hidden and secured in the environment. So, go to the setting menu of your repository and in that click on ‘secrets’.

- **GitHub Secrets**
- Then simply add AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY to your IAM user in github secrets.

- (Note: Make sure that your IAM user has proper valid IAM permissions. Your IAM user must have “AmazonEC2ContainerRegistryFullAccess” IAM permissions.)

- We’ve almost completed all the steps. Now,

- Make a commitment to your repository.
- Once the changes are pushed to the repository, check out the ‘Actions’ tab in your repository.

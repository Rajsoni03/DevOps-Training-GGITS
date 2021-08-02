# DevOps-Training-GGITS

## DevOps

Step 1- Developer -- Code -Git/ GitHub<br>
Step 2- Build (.exe)  (Tools - Jenkins/Maven)<br>
Step 3- Testing (Selenium)<br>
Step 4- Quality Assurance<br>
Step 5- Deploy (Tools - Chef/Docker/Puppet) <br>
Step 6- Maintenance + Employee Training<br>
Step 7- Monitoring<br>

## Git and GitHub
<img src="Screenshot/1.png?raw=true" width="700">
<img src="Screenshot/2.png?raw=true" width="700">

## Create New Repository on GitHub

Step 1 : - Click on + icon show in top right corner <br>
Step 2 : - Select New Repository option <br>

<img src="Screenshot/3.png?raw=true" width="700">

Step 3 : - Name the Repository

<img src="Screenshot/4.png?raw=true" width="700">

Step 4 : - Click on Create Repository button

<img src="Screenshot/5.png?raw=true" width="700">

Step 5 : - Copy the URL.

<img src="Screenshot/6.png?raw=true" width="700">

Your new repository has been created successfully.



## Install Git on EC2 Instance

Login with ec2-user 

```shell
# switch to superuser 
sudo su 

# update the packages
yum update -y

# install git
yum install git -y

# check git version
which git
```

## Git Configuration

```shell
# Set Configuration
git config --global user.name "FirstName LastName"
git config --global user.email user@gmail.com

# Check Configuration
git config --list
```


## Create Project Directory and File on EC2 Instance

```shell
# create directory 
mkdir Project

# move inside Project directory
cd Project

# craete new file 
cat > myFile.txt 
My name is _____.
```
(press `Ctrl + D` to save file and quit)

## Manage Project Versions in Local Repository

```shell
# initialise the local directory with git
git init 

# Staging the changes
git add myFile.txt
or 
git add . 

# check all files in staging area
git status

# Save the changes on local repository
git commit -m "File-v.1.0"

# checks commit history
git log
```
<img src="Screenshot/7.png?raw=true" width="700">

## Push Project to GitHub (Remote Repository

```shell
# Connect local repository to GitHub repository
git remote add origin GitHub_Repo_URL

# Push to GitHub
git push -u origin master
```

## Terms 

```shell
Working Space - 
Staging Area - 
Local Repo - 
Remote Repo - 
Commit ID and Commit - 
Cheeksum - 
Version ID - 
Tag - 
Snapshot - 
push - 
branch - 
checkout - 
```

## Chef

Chef is a Configuration Management Tool.
Chef Architecture has 3 Components

- Workstation (Where we write the code)
  - CookBook
  - Recipe
- Chef Server (Where we store the code)
  - Knife
- Chef Client (Node)  (Where we apply the code)
  - Ohai

<img src="Screenshot/8.png?raw=true" width="700">
<img src="Screenshot/9.png?raw=true" width="700">
<img src="Screenshot/10.png?raw=true" width="700">
<img src="Screenshot/11.png?raw=true" width="700">
<img src="Screenshot/12.png?raw=true" width="700">



































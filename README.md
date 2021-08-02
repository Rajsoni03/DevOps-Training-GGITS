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
<img src="Screenshot/7.jpg?raw=true" width="700">

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


## Installation of Chef on AWS EC2

- Goto www.chef.io using windows machine
- Click on Download button on top right corner
- Click on Chef Workstation
- Select your OS for download ( select Amazon Linux for EC2) 

<img src="Screenshot/13.png?raw=true" width="700">

- Click on download and fill the information form (if there are)
- If the downloading is started, pause them
- Press `Ctrl + j` for go to downloads in chrome
- Right click on link and **copy link address** (url)

<img src="Screenshot/14.png?raw=true" width="700">

- Open your EC2 terminal using putty
- login with ec2-user

```shell
# switch to root user 
sudo su

# download chef workstation in linux
wget <Paste Chef URL> 
```

<img src="Screenshot/15.png?raw=true" width="700">

```shell
# check the downloaded file
ls
```

<img src="Screenshot/16.png?raw=true" width="700">



```shell
# install the chef package
yum install <paste the above chef-workstation path>
or 
yum install <paste the above chef-workstation path> -y
```

<img src="Screenshot/17.png?raw=true" width="700">

```shell
# Check chef version
which chef
chef -v
```

<img src="Screenshot/18.png?raw=true" width="700">


## Create Cookbook

```shell
# Create a directory
mkdir cookbooks

# change directory 
cd cookbooks

# list directory 
ls

# create a new cookbook
chef generate cookbook test-cookbook1
```

<img src="Screenshot/19.png?raw=true" width="700">

```shell
# install tree package 
yum install tree -y

# show the tree structure of the directory
tree
```

<img src="Screenshot/20.png?raw=true" width="700">
<img src="Screenshot/21.png?raw=true" width="700">


## Create Recipe

```shell
# change directory 
cd test-cookbook1

# create new recipe
chef generate recipe test-recipe1

# show the tree structure of the directory
tree
```

<img src="Screenshot/22.png?raw=true" width="700">

## Write Code in Recipe

The code is written in ruby language.
The file extension/format of the ruby file is rb.
 
To edit the code in CLI, there are 3 types of code editor.
- vi
- vim
- nano

```shell
# open recipe file in vi editor
vi ./recipes/test-recipe1.rb
```

<img src="Screenshot/23.png?raw=true" width="700">

- Press i for **INSERT MODE**

<img src="Screenshot/24.png?raw=true" width="700">

- Add the following code in Recipe file

```ruby
file '/myfile' do
content 'Welcome to DevOps - Chef configuration Management Tool - GGITS'
action:create
en
```

<img src="Screenshot/25.png?raw=true" width="700">

- Press `Esc` to exit from **INSERT MODE**

<img src="Screenshot/26.png?raw=true" width="700">

- Type **:wq** and press `Enter` to save and exit.

<img src="Screenshot/27.png?raw=true" width="700">

```shell
# read the Recipe file using cat
cat ./recipes/test-recipe1.rb
```

<img src="Screenshot/28.png?raw=true" width="700">

## Run the Recipe

```shell
# execute the recipe file
chef exec ruby -c ./recipes/test-recipe1.rb
```

<img src="Screenshot/29.png?raw=true" width="700">

```shell
# run the Recipe on all nodes
chef-client -zr "recipe[test-cookbook1::test-recipe1]"
end
```

<img src="Screenshot/30.png?raw=true" width="700">

```shell
# check the files in root 
ls /
```

<img src="Screenshot/31.png?raw=true" width="700">
If the Recipe is successfully executed then you will see the myfile is created in root directory.<br>

```shell
# read myfile using cat 
cat /myfile
```

<img src="Screenshot/32.png?raw=true" width="700">
(We wrote this message in test-recipe.rb file.)
























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

## Important Terms & Definitions

<b>Working Space - </b> It is where the code is written & is called the workspace.<br>
<b>Staging Area - </b> When code needs to be committed, it is added to the staging area. In other words we can say when the code needs to be finalized it comes in staging area. This process is called "Add".<br>
<b>Local Repo - </b> When the code is final, we commit the code from staging area to local repository. Local repo is present inside the Linux machine.<br>
<b>Remote Repo - </b> A remote repo is a git repository hosted on the internet or some other network.<br>
<b>Commit ID and Commit - </b>Commit ID is the metadata  stored with the file, it is 40 alphanumeric characters. Bringing the file from staging area to Local repository is called "Commit", it means that all the code that has been written is finally saved.<br>
<b>Cheeksum - </b> It is a numeric value attached with the file, when the file is updated the checksum value changes hence we get to know that the file/data/code has been updated.<br>
<b>Version ID - </b> Reference to identify each change, when the user updates the file the version ID depicts about who did so.<br>
<b>Tag - </b> With the commit ID a tag can also be attached which contains a message of what has been updated lastly.<br>
<b>Snapshot - </b> The changes that are made in file is snapshot, changes that are made in a particular time.<br>
<b>Push - </b> What all has been committed in local repository now is pushed to Central Repository(GitHub/GitLab or any other) this is called push.<br>
<b>Push - </b> Pull operation copes the changes from a remote repository to a local machine. Pull operation is also used as synchronization between the two repositories<br>
<b>Branch - </b> Code is same so only one repository is created but when we want to work in parallel, 'branch' is created in which changes are personal to that branch only and finally it is clubbed together with other branches.<br>
<b>Checkout - </b> This command Is used to switch in between the branches and check for the updated files or any new commits to it.<br>


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


## Install and Run Apache Web Server on EC2 using Chef

```shell
# list directory
ls

# change directory
cd cookbooks
```

<img src="Screenshot/33.png?raw=true" width="700">

```shell
# create new cookbook
chef generate cookbook apache-cookbook

# change directory
cd apache-cookbook
```

<img src="Screenshot/34.png?raw=true" width="700">

```shell
# create new recipe
chef generate recipe apache-recipe
```

<img src="Screenshot/35.png?raw=true" width="700">

```shell
# show directory 
tree
```

<img src="Screenshot/36.png?raw=true" width="700">

```shell
# open recipe in vi editor
vi ./recipes/apache-recipe.rb
```

add following code in recipe
```ruby
package 'httpd' do
action :install
end

file '/var/www/html/index.html' do
content '<h1>Hello World!</h1><h3>This is My First Website</h3>'
action :create
owner 'root'
group 'root'
end

service 'httpd' do
action [:enable, :start]
end
```

<img src="Screenshot/37.png?raw=true" width="700">
press `Es`c then press **:wq** and press `Enter` to save and exit

```shell
# execute the recipe
chef exec ruby -c ./recipes/apache-recipe.rb
```
<img src="Screenshot/38.png?raw=true" width="700">

```shell
# run the recipe 
chef-client -zr "recipe[apache-cookbook::apache-recipe]"
```

<img src="Screenshot/39.png?raw=true" width="700">


## AWS EC2 Security Setup

STEP 1 : - Select EC2 instance then select Security Column

<img src="Screenshot/40.png?raw=true" width="700">

STEP 2 : - Click on Security Group ID

<img src="Screenshot/41.png?raw=true" width="700">

STEP 3 : - Click on Edit inbound rules

<img src="Screenshot/42.png?raw=true" width="700">

STEP 4 : - Change Type from HTTPS to HTTP and save rules

<img src="Screenshot/43.png?raw=true" width="700">

## Open Web Page

STEP 1 : - Copy Public IPv4 address of your EC2 instance

<img src="Screenshot/44.png?raw=true" width="700">

STEP 2 : - Paste the address on web browser 

<img src="Screenshot/45.png?raw=true" width="700">

You're web-page is successfully deployed.


## Update Website

```shell
# open recipe using vi
vi ./recipes/apache-recipe.rb
```

<img src="Screenshot/46.png?raw=true" width="700">

```shell
# execute and run recipe
chef exec ruby -c ./recipes/apache-recipe.rb
chef-client -zr "recipe[apache-cookbook::apache-recipe]"
```

<img src="Screenshot/47.png?raw=true" width="700">    

<img src="Screenshot/48.png?raw=true" width="700">                                                        


## Attributes of Chef

```shell
ohai

ohai ipaddress

ohai memory

ohai memory/total
```

## Show the Attributes of Chef using Recipe

STEP 1:- Create a new Recipe

```shell
cd cookbooks
 
cd apache-cookbook

chef generate recipe attributes-recipe
```

<img src="Screenshot/49.png?raw=true" width="700">

STEP 2 :- Edit the recipe

```shell
vi ./recipes/attributes-recipe.rb
```

```shell
# execute and run recipe
chef exec ruby -c ./recipes/apache-recipe.rb
chef-client -zr "recipe[apache-cookbook::apache-recipe]"
```

STEP 3 :- Add the following code in recipe

```ruby
file '/basicfile' do
content "This is a file to get and learn attributes
HOSTNAME: #{node['hostname']}
IPADDRESS: #{node['ipaddress']}
MEMORY: #{node['memory']['total']}"
owner 'root'
group 'root'
action :create
end
```

<img src="Screenshot/50.png?raw=true" width="700">   

STEP 4 :- Execute and run the recipe

```shell
chef exec ruby -c ./recipes/attributes-recipe.rb
chef-client -zr "recipe[apache-cookbook::attributes-recipe]"
```

<img src="Screenshot/51.png?raw=true" width="700">  


## Chef Server (Attaching Chef Server to WorkStation)


STEP 1:- Open https://manage.chef.io <br>


STEP 2:- Create your account <br>


STEP 3:- Go to starter kit  <br>

<img src="Screenshot/52.png?raw=true" width="700"> 

STEP 4:- Download and Extract the file.

<img src="Screenshot/53.png?raw=true" width="700">  

STEP 5:- After extracting the file we will have file named chef-repo and we have to copy this file to our Linux system to do that

STEP 6:- Download WinSCP Applicatrion in windos machine. With this we can transfer files from our local windows machine to Linux machine.
WinSCP Link - https://winscp.net/eng/download.php

STEP 7:- Install it (just click next ...next while installing)

STEP 8:- Open WinSCP, this screen will come up

<img src="Screenshot/54.png?raw=true" width="700">  

STEP 9:- Fill these empty fields 
- Host name = PUBLIC IPv4 DNS OF LINUX MACHINE
- User name = ec2-user

<img src="Screenshot/55.png?raw=true" width="700">  

STEP 10:- Go to Advance option.
- Go to Authentication
- Give the same private key as your Linux machine (that ppk private key)

<img src="Screenshot/56.png?raw=true" width="700">  

STEP 11:- After selecting the private key, click and just Login

<img src="Screenshot/57.png?raw=true" width="700"> 

STEP 12:- Now two windows will open left one will be for windows and right one for Linux. From window of windows go to chef-repo folder drag that folder to Linux machine.

<img src="Screenshot/58.png?raw=true" width="700"> 

STEP 13:- Now we can go to Linux CLI and check if the chef-repo file is there by typing ls command

```shell
cd chef-repo

ls -a

cd .chef

ls 

cat config.rb 
```
(chef server url will come up along with some other info)

<img src="Screenshot/59.png?raw=true" width="700"> 

STEP 14:- Now we can connect our workstation by using knife command

```shell
knife ssl check 
```
<b>ssl - secure socket layer</b>

<img src="Screenshot/60.png?raw=true" width="700"> 

This means your workstation is successfully connected to Chef Server


## Create New Chef Node

<b>*Important*</b><br>
Note the Availability Zone of your Work Station Machine (We create Node Machine at same Availability Zone)

<img src="Screenshot/61.png?raw=true" width="700"> 

STEP 1:- Create new AWS Linux Machine <br>

STEP 2:- Select Availability Zone same as workstation machine

<img src="Screenshot/62.png?raw=true" width="700"> 

STEP 3:- Write the default executable code (It execute while instance is initialling)

<img src="Screenshot/63.png?raw=true" width="700"> 

STEP 4:- Add Tag

<img src="Screenshot/64.png?raw=true" width="700"> 

STEP 5:- Configure Security Group

<img src="Screenshot/65.png?raw=true" width="700"> 

STEP 6:- Create New key pair

<img src="Screenshot/66.png?raw=true" width="700">

## Connect Nodes to Chef Server

STEP 1:- Login in workstation machine with <b>ec2-user</b>

```shell
# switch to super user
sudo su

# list directory
ls

# Change directory
cd cookbooks

# list directory
ls
```

<img src="Screenshot/67.png?raw=true" width="700"> 

STEP 2:- Move apache-cookbook to chef-repo/cookbooks

<img src="Screenshot/68.png?raw=true" width="700"> 

```shell
# go to perent directory
cd ..

# move apache-cookbook and test-cookbook1
mv cookbooks/apache-cookbook chef-repo/cookbooks/
mv cookbooks/test-cookbook1 chef-repo/cookbooks/

# delete old cookbooks directory
rm -rf cookbooks

# list directory
ls
```

<img src="Screenshot/69.png?raw=true" width="700"> 

```shell
# check chef-repo/cookbooks
cd chef-repo
cd cookbooks
ls
```

<img src="Screenshot/70.png?raw=true" width="700"> 

STEP 3:- Copy Node-key.pem file to Chef workstation using WinSCP software

<img src="Screenshot/71.png?raw=true" width="700"> 


```shell
# Check the key
cd .. 
ls
```

<img src="Screenshot/72.png?raw=true" width="700"> 

STEP 4 :- Bootstrapping (Connecting Node to Chef Server using Knife)

```shell
knife bootstrap <node private IP> --ssh-user ec2-user --sudo -i Node-key.pem -N Node1
```

<img src="Screenshot/73.png?raw=true" width="700"> 
<img src="Screenshot/74.png?raw=true" width="700"> 


```shell
# Show all nodes
knife node list
```

<img src="Screenshot/75.png?raw=true" width="700"> 


STEP 5:- Set Cookbook to Run List of Chef Node

```shell
# Set Cookbook 
knife node run_list set Node1 "recipe[apache-cookbook::apache-recipe]"

# Check the run_list of the Node
knife node show Node1
```

<img src="Screenshot/76.png?raw=true" width="700"> 

STEP 6:- Upload the cookbook to Node 

```shell
knife cookbook upload apache-cookbook
```

<img src="Screenshot/77.png?raw=true" width="700"> 


## Cherf Node Setup

STEP 1:- Convert Node-key.pem to Node-key.ppk using putty-gen<br>

STEP 2:- Login to node machine with ec2-user

```shell
# switch to super user
sudo su

# run the pull request
chef-client 
```

STEP 3:- Automate the pull request process

```shell
# open crontab file using vi editor
vi /etc/crontab
```

Add the following line
```shell
* * * * * root chef-client 
```

<img src="Screenshot/78.png?raw=true" width="700"> 

Save and quit from editor using <br>:wq</b>

## Check the Web page

STEP 1:- Copy Node's Public IPv4 address 

<img src="Screenshot/79.png?raw=true" width="700"> 

Step 2:- Paste on Web Browser 

<img src="Screenshot/80.png?raw=true" width="700"> 


## Automate Chef Node While Creating/Launching

Add the default command in <b>Configuration Instance Details Step</b>

```shell
#!/bin/bash
sudo su
yum update -y
echo "* * * * * root chef-client"  >>  /etc/crontab
```

<img src="Screenshot/81.png?raw=true" width="700"> 


## Update the Web Page

Goto Chef Work Station Terminal<br>

STEP 1:- Edit the Recipe

```shell
# Open apache-recipe in vi editor
vi apache-cookbook/recipes/apache-recipe.rb
```

<img src="Screenshot/82.png?raw=true" width="700"> 

STEP 2 :- Upload the cookbook to Node

```shell
knife cookbook upload apache-cookbook
```

<img src="Screenshot/83.png?raw=true" width="700"> 

STEP 3:- Check the Website

<img src="Screenshot/84.png?raw=true" width="700"> 


## Interview Questions

- Q.1  Why DevOps? Where you used DevOps?
- Q.2  Which s/w you used in DevOps?
- Q.3  Which tool u use?
- Q.4  Difference b/w Development and Operations.
- Q.5  Git / GitLab / GitHub?
- Q.6  Which platform you use in DevOps?
- Q.7  Why infinite loop in DevOps?
- Q.8  Where you use Git Bash?
- Q.9  Configuration Management and Types of Version Control Systems ?
- Q.10  Chef workstation / Chef server/ Chef nodes/ Chef client / knife / recipe / bootstrapping,
- Q.11  Operational tool in DevOps?
- Q.12  Have you do testing in the DevOps project?
- Q.13  Agile description / Scrum Framework?
- Q.14  CI/CD (*Imp)
- Q.15  Learn more about cloud computing (*Imp)?
- Q.16  LINUX Command
  - package install command
  - file system
  - remove command
  - learn more basics command


## Final Project (Connect Chef-Server and Nodes to GitHub Repository and Automate them)

STEP 1:- Create a New Folder in your Windows machine.

<img src="Screenshot/85.png?raw=true" width="700"> 

STEP 2 :- Create a index.html file in the folder.

<img src="Screenshot/86.png?raw=true" width="700"> 

STEP 3 :- Open index.html file in any text editor and write the html code.

<img src="Screenshot/87.png?raw=true" width="700"> 

STEP 4 :- Create New GitHub Repository

<img src="Screenshot/88.png?raw=true" width="700"> 

STEP 5 :- Open Git Bash in same folder.

<img src="Screenshot/89.png?raw=true" width="700"> 

STEP 6 :- Connect local repository to GitHub repository and push the code.
```bash
git init

git add .

git commit -m "index.html file added"

git remote add origin <github_repo_ssh_url>

git push -u origin master
```

<img src="Screenshot/90.png?raw=true" width="700"> 

STEP 7 :- Check GitHub Repository

<img src="Screenshot/91.png?raw=true" width="700"> 

STEP 8 :- Open EC2 instance terminal with ec2-user

```shell
# switch to super user
sudo su

# goto apache-cookbook directory
cd chef-repo/cookbooks/apache-cookbook/

# open apache recipe in vi editor
vi recipes/apache-recipe.rb
```

STEP 9 :- Deleting existing html file <br>

Add the following ruby code in apache-recipe.rb file

```ruby
file '/var/www/html/index.html' do 
action :delete
end
```

<img src="Screenshot/92.png?raw=true" width="700"> 

STEP 10 :- Test the recipe in chef server

```shell
# Execute the recipe
chef exec ruby -c ./recipes/apache-recipe.rb 

# deploy the recipe
chef-client -zr "recipe[apache-cookbook::apache-recipe]"
```

<img src="Screenshot/93.png?raw=true" width="700"> 

STEP 11 :- Deploy the cookbook to chef nodes

```shell
# goto parent directory 
cd ..

# Upload the apache-cookbook 
knife cookbook upload apache-cookbook
```

<img src="Screenshot/94.png?raw=true" width="700"> 

it will delete index.html file from all connected nodes<br><br>

STEP 12 :- Connect Chef to GitHub 

```shell
# goto apache-cookbook directory
cd chef-repo/cookbooks/apache-cookbook/

# open apache recipe in vi editor
vi recipes/apache-recipe.rb
```

Add the following ruby code in apache-recipe.rb file

```ruby
package 'httpd' do
action :install
end

package 'git' do
action :install
end

bash 'git_pull' do
user 'root'
cwd '/var/www/html'
code <<-EOH
git init
git remote add origin <YOUR_GITHUB_REPO_URL>
git pull origin master
EOH
end

service 'httpd' do
action [:enable, :start]
end
```

<img src="Screenshot/95.png?raw=true" width="700"> 

STEP 13 :- Test the recipe in chef server

```shell
# Execute the recipe
chef exec ruby -c ./recipes/apache-recipe.rb 

# deploy the recipe
chef-client -zr "recipe[apache-cookbook::apache-recipe]"
```

<img src="Screenshot/96.png?raw=true" width="700"> 


STEP 14 :- Copy Chef-server IPv4 and Check the web-page 

<img src="Screenshot/97.png?raw=true" width="700"> 
<img src="Screenshot/98.png?raw=true" width="700"> 
We successfully connected our chef server to GitHub repository.<br> <br>


STEP 15 : - deploy the recipe to chef node machines

```shell
# goto parent directory 
cd ..

# Upload the apache-cookbook
knife cookbook upload apache-cookbook
```

<img src="Screenshot/99.png?raw=true" width="700"> 

STEP 16 :- Copy Chef-Node IPv4 and Check the web-page

<img src="Screenshot/100.png?raw=true" width="700"> 

<img src="Screenshot/101.png?raw=true" width="700"> 


STEP 17 :- Now we want to automate the process of pull the code from GitHub and uploading the cookbook to chef nodes.<br>

Open chef workstation terminal

```shell
# open crontab file
vi /etc/crontab
```

Add the following command 

```shell
* * * * * root "cd /var/www/html && git pull origin master && cd /home/ec2-user/chef-repo/cookbooks knife cookbook upload apache-cookbook"
```

<img src="Screenshot/102.png?raw=true" width="700"> 

STEP 18 :- Test the automation.<br>

Update the html file in your local machine

<img src="Screenshot/103.png?raw=true" width="700"> 

Commit changes and push to GitHub

<img src="Screenshot/104.png?raw=true" width="700">

Copy your node IPv4 and paste in web browser 
 
<img src="Screenshot/105.png?raw=true" width="700"> 

Now our chef is successfully connected to GitHub and deployment is fully automated. <br><br>


STEP 19:- Edit Html code with your creativity and push to GitHub. Your website is automatically updated within a minute.

<img src="Screenshot/106.png?raw=true" width="700"> 

HTML code link - https://github.com/Rajsoni03/GGITS-Training/blob/master/index.html

<img src="Screenshot/107.png?raw=true" width="700"> 

Congratulations Your Project is Successfully Automated.












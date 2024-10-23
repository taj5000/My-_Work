 <h1 align="center"> Docsify Setup</h1>


 ### <span style="color: skyblue;">Docsify- 
 * Docsify is a documentation site generator that focuses on simplicity and ease of use.

 * With Docsify, we can quickly turn our documentation content into a user-friendly website with navigation, search functionality, and other useful features.

 >> ### <span style="color: teal;">Setup of Docsify

## <span style="color: Blue;">Step 1

 Here we are asking Podman to display information about all containers, including those that are not currently running, in the current environment.

> **podman ps -a**

![image](text.png)

>> ps - **The ps command stands for "process status." In the context of podman, it is used to list containers and their current status.**

>> -a- **The -a flag is a command-line option that stands for "all." When used with the ps command, it instructs podman to show all containers, including those that are stopped or exited, in addition to the running containers** 

## <span style="color: Blue;">Step 2

Make directory with the name of **myapp** and then instruct the system to change the current diarectory to the **myapp**diarectory 
>  **mkdir myapp**

>  **cd myapp**

![Alt text](doc2.png)

>> mkdir: **mkdir is a command-line utility that stands for "make directory." It is used to create a new directory (also known as a folder) within a file system.**

>> myapp - **Is the name of directory that I have created**

>> cd: **cd is a command-line command that stands for "change directory." It is used to navigate between different directories (folders) in a file system.**

## <span style="color: Blue;">Step 3

Instruct vim editor to open file named **Docker file** for editing.
![Alt text](docs4.png)

> Here **vi** is the Vim text editor and here i am instructing it to open a file name **Dockerfile** for editing. 
**Dockerfile is the name of the file that I want to open.


## <span style="color: Blue;">Step 4
Now create an empty file with the name of **index.html** also make md file with the name of **README.md**
 > **touch index.html**

![Alt text](docs3.png)

> #### Now enter the index.html file and paste the HTML syntax.

![Alt text](index.png)

## <span style="color: Blue;">Step 5

>Now enter the README.md file using the vim command so that the Document text can be updated automatically.

> **vim README.md**

![Alt text](readme.png)

## <span style="color: Blue;">Step 6

Now move the file **dockerfile** from the myapp directory to the current directory 
>**mv myapp/dockerfile .**

> Also instruct the Podman to built docker image using the dockefile named Dockerfile and tag the resulting image as **docsify/demo**.
Syntex : **podman build -f dockerfile -t docsify/demo** 

* **-f(--file)** -This option is used to specify the path to the Docker file that should be used for building the image.
* **-t(--Tag)** - This option used to specify a name and optional tag for the image being build. 

![Alt text](docs5.png)

>>This output provides a detailed view of the steps taken to build the docker image and indicates the use of cached layers to optimizing the build process. The resulting image is tagged as **localhost/docsify/demo:latest**


## <span style="color: Blue;">Step 7
>Now list the container images that are currently available in your system using the container management tool.

> **podman ps**

![Alt text](docs6.png)

## <span style="color: Blue;">Step 8 
**Run the docker image** 

>**podman run -itp 3000:3000 --name=docsify -v $(pwd):/docs docsify/demo**

![Alt text](docs7.png)

* The command started a container, named it "docsify", mapped port 3000 from the host to the container, mounted the current working directory from the host into the container's "/docs" directory, and launched a Docsify server that is accessible at "http://localhost:3000". 
* The provided output confirms that the container is successfully serving content and listening on the specified port.


## <span style="color: Blue;">Step 9

>Run local host on browser.

![Alt text](browser.png)

# <span style="color: Grey;">GitHub
GitHub is a widely used platform for hosting and managing software projects using the Git version control system. It provides a collaborative environment for developers to work together on projects, track changes, and manage code repositories.

>> ### <span style="color: teal;">Setup of GitHub

## <span style="color: Blue;">Step 1

> Create a new repository.

> Click on **New repository**

![Alt text](Git1.png)

## <span style="color: Blue;">Step 2


>Now enter your repository name and make it **public**

![Alt text](Git2.png)





# <span style="color: Grey;">Docsify and Git intigration 

![Alt text](Git8.png)

## <span style="color: Blue;"> Step 1

![Alt text](git4.png)
#### For creating a new repository on CLI follow all these steps 
* git init
* git add README.md 
* git commit -m "first commit" 


![Alt text](Git5.png)

![Alt text](Git6.png)

## <span style="color: Blue;">Step 4

>**When we change  and update something in our document , run following commands:**
* git branch -M main
* git remote add origin http://github.com.taj4990/docsify_taj.git
* git push -u origin main
* Enter the user name and then enter.
* Now for password goto Git settings and create token and make some changes.

![Alt text](taj.png)


* Click on developer setting
in the left hand side bottom .


![Alt text](taj1.png)


* Select Personal access token.

![Alt text](<taj 2.png>)

* Select classic token.

![Alt text](taj3.png)


* Generate classic token.
![Alt text](GitN5.png)

* Varify login
![Alt text](GitN6.png)

* Give name of your token and marks all the boxes and click on create.
![Alt text](GitN7.png)

![Alt text](GitN8.png)

* **after that copy the token and paste that on your CLI(Command line interface).**


![Alt text](Git7.png)

>>**git branch -M main**

* **git: This is the command-line interface for the Git version control system.**

* **branch: This is a subcommand in Git used to manage branches within a repository.**

* **-M: This is a command-line option that stands for "move" or "move/rename."** 

* **main: This is the new name I am  assigning to the current branch.**

>>git push -u origin main

* **push: This is a Git command used to send my local changes to a remote repository.**

* **-u: This is a command-line option that stands for "set upstream." When used with the git push command, it establishes a tracking relationship between my local branch and the remote branch I am  pushing to.**
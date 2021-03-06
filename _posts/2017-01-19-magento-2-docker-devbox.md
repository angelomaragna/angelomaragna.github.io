---
layout: post
title: "Magento 2 devbox - Docker quick start guide [PART 1]"
---
_Firing up the container_



This guide, was tried on macOS SIERRA where Docker was already installed.

First of all, a brief introduction. Docker is a virtualization environment where you will use one or more images fired up into "containers" for your work.
Images usually represetns those essential parts of the services you need to run, such as the apache web server. Remember, containers are not virtual machines. They run into special environments as if they had their own life. 
Therefore you can expect to fire up an httpd (apache) container with no shell access at all.


Here are the steps to run Magento 2 devbox into a docker environment. 

1 **Clone the git repository**
```git clone https://github.com/magento/magento2devbox-web.git```

2 **Move into the folder**

3 **Compile our custom image** (expect it to take while...)
```docker build -t magento2devbox ./```
With this command we tell docker to build a custom image named "magento2devbox". Docker will read the current directory for the Dockerfile containing the configuration a will begin the compilation. You should see it downloading a bunch of "docker containers" and after that the custom commands run a series of initial configurations.

You will now have a new image, ready to be fired into a container. You can check a new image "magento2devbox" has been created with:
```docker images```

4 **quit any other local web server**
(please, don't have me say this thing twice...)

5 **fire up your containers**
```docker run --name devbox -p 80:80 -p 22:22 -it magento2devbox```
We now told docker to run a new container from the image "magento2devbox" in interactive mode (-it) and name it "devbox". We also told it to forward ports 22 and 80 from the host to the container.
NOTE: you will have to keep this terminal session open as long as you want to use the devbox. You can run the container in background with different commands but as we may like to have everything under control, in this tutorial we will use it this way.

At this point, you will need to open another shell.

6 **check the devbox is running**

Run in terminal the command
```docker ps```
You should see a line like this:
![](images/docker-ps.png)
where the column PORTS will tell us on which ports the new container is currently listening.



Now, you can login open your browser to your localhost and log into your container with the command
```ssh magento2@127.0.0.1```
Environment up, running and ready to go. 

[...to be continued]


---



## Docker command tips

**Stop all containers and delete them all**
(Note this will not remove the images from your machine)
```docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q)```


Angelo
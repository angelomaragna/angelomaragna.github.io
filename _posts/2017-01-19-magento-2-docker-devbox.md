#Magento 2 devbox - Docker quick start guide

_[this document is a work in progess]_

This guide, was tried on macOS SIERRA where Docker was already installed.
A brief introduction about Docker. Docker is a virtualization environment where you will use one or more images be fired up into "containers" and use only those bits of environment you will need for your work.
So, you can expect to fire up an httpd (apache) container with no shell access at all.

Here the steps to run the environment. 

1 **Clone the git repository**
```git clone https://github.com/magento/magento2devbox-web.git```

2 **Move into the folder**

3 **Compile our custom image** (expect it to take while...)
```docker build -t magento2devbox ./```
With this command we tell docker to build a custom image named "magento2devbox". Docker will read the current directory for the Dockerfile containing the configuration a will begin the compilation. You should see it downloading a bunch of "docker containers" and after that the custom commands run a series of initial configurations.

You will now have a new image, ready to be fired into a container. You can check the new image created with:
```docker images```





Angelo

_[this document is a work in progess]_


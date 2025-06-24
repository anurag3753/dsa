
Video1 URL : https://www.youtube.com/watch?v=JRmV_mKnnyU
Video2 URL: https://www.youtube.com/watch?v=b0jb_uC9Dck
Github : https://github.com/sudhanshuvlog/GFG-Workshop2025

![[Pasted image 20250528214823.png]]

Business/Marketing Team comes with an idea. They create a requirements document around it. This document is then read by the development team. Once understood clearly, development team decides on the tech stack to implement the respective idea. After some weeks/months the idea finally comes to reality by the development team.


![[Pasted image 20250528220811.png]]

Once the implementation is completed. Generally the code goes through several stages before actually landing inside the production servers.
- Testing (unit tests are executed for the implemented code)
- Tools like Sonarcube(static code analysis) and more are invoked on the code.
- Linting is checked (for python code is checked against the PEP standards)

Sonarcube :- Used for static code analysis in multiple companies.
	- Identifies code duplicity
	- Identifies security leaks like (password) hardcoded inside the code
	- Identifies dead code


![[Pasted image 20250528223300.png]]

- Finally, the code is bundled and then deployed on the dev servers.
- Development team checks, if the features implemented are working as expected on the dev servers.
- Once given Green by Dev team, Later the code is deployed on the QA servers, where QA team looks at the features, it compares it by reading the requirements document provided by the business team and any discrepancy, calls out to the entire (code->testing->static analysis ..) chain getting repeated.
- Once given Green by QA team. Then we deploy our code in the pre-prod servers/staging environment. Here, the main thing we verify is that no other existing features should be getting impacted because of this new feature. You also check for the overall performance of the application. Integration testing is DONE here.
- Once we get the Green in the Pre-prod environment, then we deploy the code on the production. Otherwise, the cycle repeats.

Devops: It is nothing but a set of practices that team needs to follow to deliver high quality sotware. Devops comes with an umbrella of tools, which makes our task easy. 
Also one more role of devops is to create automation to be relevant in the market. This automation goal is to minimize the TTM.


TTM: Time to market means whenever an idea comes up in your mind, how quickly you can take that to your end consumer.
If you want to release your ideas very quickly, you need to use automation in your flow to make it fast.


![[Pasted image 20250529114904.png]]

These 1-6 steps are the part of the CI-CD infrastructure. CI means continuous integration (steps 1-4) are part of continuous integration and (5-6) steps are part of continuous delivery.

![[Pasted image 20250529120429.png]]

AWS:



![[Pasted image 20250529173945.png]]


We prefer Linux in our servers, because of its advantage listed inside the image. Furthermore, companies are taking base Linux image and doing their customizations on top of it and giving their name to that Linux flavor (like Petalinux, Fedora, Centos). These are nothing but base Linux kernel with some customizations on top of it. These various flavors of Linux are also known as Linux distributions like (Redhat, Kali, Ubuntu).


![[Pasted image 20250529193213.png]]

To provide multiple microservices, Amazon prefers to host each microservice on a separate hardware. But there could be scenario like Black Friday sale, where one microservice will face load higher than the other services.
To address this, when some services are underutilized, but some services need more resources. We came up with the solution of **Hypervisor/Virtualization** technology, which allows to host multiple OS on the same hardware.

![[Pasted image 20250530110120.png]]

- This virtualization technology gave the birth to the **Cloud Computing.** 
- **Virtualization** is the technology name, but the tool that will give you this service is known as **Hypervisor**.

![[Pasted image 20250530110947.png]]

In AWS, it has got physical hardware available with it. Whenever we request, it creates a VM and gives to us. This virtualization technology is the key to Cloud computing. 

We can request for an EC2 instance from the amazon and then we can use it to perform any of our development tasks. To connect than EC2 instance we need to use ssh and provide the private key.


![[Pasted image 20250530112545.png]]

# Redhat Package Manager
- amazon linux uses red hat behind the scenes. Hence, it uses the **yum** package manager.
- By default **Apache web server** reads html from a location **/var/www/html**
- We can use **cat** command to write content to the file as well.
#### Installing web server Apache
```shell
yum install httpd # install the apache package manager
rpm -q httpd # Query the red hat package manager for the package name httpd
```
- Further all the packages in the Red Hat comes with the extension of .rpm(red hat package manager)
```shell
# To start the service inside the linux we use `systemctl`
systemctl start httpd # systemctl will start httpd service
systemctl status httpd # You should see it in running state
```
- By default, we will not be able to access our website. Because of firewall. We need to allow certain ports in order to access the website. In AWS, these firewall rules are present under `security group`.
- Inside you Ec2 instance, Goto the security group and then update the inbound & outbound rules.

![[Pasted image 20250530202924.png]]
- 0.0.0.0 means anyone on the internet can connect to my EC2 instance on port 80/8080

---------------------------Lecture 2------------------------------------
RTPT : Regression Testing and Performance Testing. Regression Testing here means if because of this new feature if any already working feature is impacted. Performance Testing checks for any performance impact in the overall application because of this new feature.

- yum is the package manager in Red Hat.
- apt is the package manager in Ubuntu.

#### How to view configuration file for apache

/etc : Contains the configuration files for the linux.
/etc/httpd/conf/httpd.conf
	- Like default http location to look for **/var/www/html**
	- Default port to listen to: **80**

![[Pasted image 20250601201035.png]]

Containerization : Technology Name
Docker : One such tool which uses this technology.

Containerization docker : It involves packaging the applications and their dependencies into self-contained, portable units called **containers.** 
**Other definition:** Package Software into Standardized Units for Development, Shipment and Deployment.

This docker set of steps has multiple names. Bundle/Template/Package/Image all are its names.

**This bundle is used by the Docker to launch the containers within seconds.**

### Docker Vs VMs

![[Pasted image 20250601202255.png]]

### Docker Architecture



![[Pasted image 20250601214006.png]]


```shell
yum install docker # Install docker
systemctl start docker # It starts docker server/engine/daemon
```

- There are many folks who have created a lot of docker images/templates/bundle and put them to be used by others. These images are kept at a central location known as **Docker Hub/Image Registry.** 
- Lets pull images from docker hub and use it first. [Docker Hub](https://hub.docker.com/repositories/)
```shell
docker pull ubuntu # Experiment to download official ubuntu image from docker registry
docker run ubuntu # IT launches the container from ubuntu image
# This failed as ubuntu runs an interactive bash by default. So right way to work with this container is :
ducer run -it ubuntu # i -> interactive, t -> terminal
exit # Takes you out of the container
docker start <container_id>/<container_name> # to start again a stopped container
# IF you do docker ps , then it will show that container again started running.
docker attach <container_id>/<container_name> # Will again attach me back to the container.
docker inspect <container_id>/<container_name> # List complete details about the container. Like ip adress etc..
```
#### Docker Commands
- docker ps : List of all running docker containers.
- docker images: It list down various images present inside my local system.
- docker ps -a: List down all containers that are running or failed
- docker inspect <container_id>/<container_name> : List more details about your container
- Ctrl + p + q : Comes out of the container w/o exiting the container.

Container Features:
- Container has its own file system.
- It has its own ip address. These ip address are not coming from the real network card. These are SDNs (Software defined networks)
- Each one is isolated.
- Once i have an image, from that image, I can launch millions of containers within seconds.
- 



2:00:00
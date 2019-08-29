# Jenkins + Jenkins job builder + Newman docker image
There is my version of Jenkins docker image.   
This image based on the [official Jenkins docker image](https://hub.docker.com/_/jenkins) and also includes Node.js, Newman, Python, PIP, VIM, and Jenkins job builder.       
This is a fully completed solution for working with Jenkins, Jenkins job builder, and Postman collections.  

## Tools
Docker, Jenkins, Jenkins job builder, Node.js, Newman, Python, PIP, VIM

## Usage

### Common  
Usage information official Jenkins docker image [here](https://github.com/jenkinsci/docker/blob/master/README.md)

### How to create docker container and start Jenkins
* open command line
* check Docker version `docker --version`
  * if Docker doesn't find install from [Docker](https://docs.docker.com/docker-for-windows/install/)
* clone git repository `https://github.com/MaryGeraseva/6-docker-jenkins-newman-jjb.git`
* create and open folder for Jenkins 
 * `cd [$user.dir]/6-docker-jenkins-newman-jjb`
 * `mkdir jenkins-data`
 * `cd jenkins-data`
* build Jenkins image `docker build -t [$image-name] ./`
* build container `docker run -v [$user.dir]/6-docker-jenkins-newman-jjb/jenkins-data:/var/jenkins_home --name [$image-name] -p 8080:8080 -p 50000:50000 [$container-name]`
* open Jenkins, create new user and download required plugins


### How to add jobs with Jenkins job builder
Jenkins job builder (JJB) is an additional application which takes simple descriptions of Jenkins jobs in YAML or JSON format and uses them to configure Jenkins. 
More information about Jenkins job builder [here](https://docs.openstack.org/infra/jenkins-job-builder/) 
Sample files and usage in [my project](https://github.com/MaryGeraseva/4-jenkins-job-builder).


## For feedback
**e-mail:** mary.geraseva@gmail.com  
**telegram:** @MaryGeraseva  
**skype:** mary_geraseva  
[linkedIn](https://www.linkedin.com/in/maria-geraseva/)

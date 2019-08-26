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
I use Jenkins jobs builder files from [my previous project](https://github.com/MaryGeraseva/4-jenkins-job-builder) as an example.

* open personal configuration `localhost:8080/me/configure`

![alt text](https://github.com/MaryGeraseva/screenshots/blob/master/configure.png)

* add user token

![alt text](https://github.com/MaryGeraseva/screenshots/blob/master/add%20token.png)

* generate and copy user token

![alt text](https://github.com/MaryGeraseva/screenshots/blob/master/generate%20tocken.png)

![alt text](https://github.com/MaryGeraseva/screenshots/blob/master/copy%20tocken.png)

* go into docker container as root `docker exec -u 0 -it [$container-name] bash`
* clone repository with JJB files `git clone https://github.com/MaryGeraseva/4-jenkins-job-builder.git`
* go to folder with JJB files `cd 4-jenkins-job-builder/linux`
* open configuration file jenkins_jobs.ini in Vim `vim jenkins_jobs.ini`
  * input  `i` and correct personal authentication data `[$user-name]` and `[$user-token]`
  * input `Esc` or `Ctrl+C`
  * input `:wq` for saving and quit
* add jobs with JJB from command-line  
`jenkins-jobs --conf ./jenkins_jobs.ini update ./jobs.yaml`
* check changes in your Jenkins

More information about Jenkins job builder [here](https://docs.openstack.org/infra/jenkins-job-builder/)

## For feedback
**e-mail:** mary.geraseva@gmail.com  
**telegram:** @MaryGeraseva  
**skype:** mary_geraseva  
[linkedIn](https://www.linkedin.com/in/maria-geraseva/)

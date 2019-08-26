# Jenkins job builder project

Jenkins job builder (JJB) is an additional application which takes simple descriptions of Jenkins jobs in YAML or JSON format and uses them to configure Jenkins.
This project contains Windows and Linux version Jenkins job builder files for running postman collections with Jenkins from [this project](https://github.com/MaryGeraseva/5-postman-api-tests).

## Tools
Jenkins and Jenkins job builder

## Usage

### How to add jobs in Jenkins on Windows
* open command line
* check python version `python --version`
  * if python doesn't find install from [Python](https://www.python.org/downloads/)
* check python version `pip --version`
   * if python doesn't find install   
     * `curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py`   
     * `python python3-pip -y`
* install jenkins job builder `pip install jenkins-job-builder`
* check jenkins job builder in your OS `jenkins-jobs`
  * if previous command doesn't exist check/refresh in $PATH correct path to python scripts folder `[$user.dir]\Python\Python<version>\Scripts`
* check Node.js `node -v`
  * if Node.js doesn't find install version 8.X or 10.X from [Node.js](https://nodejs.org/en/)
* check Newman `newman -v`
  * if Newman doesn't find install with Node.js `npm install -g newman`
* clone repository with JJB files `git clone https://github.com/MaryGeraseva/4-jenkins-job-builder.git`
* go to folder with windows files version `cd [$user.dir]/4-jenkins-job-builder/windows`
* start your Jenkins and open personal configuration `localhost:8080/me/configure`

![alt text](https://github.com/MaryGeraseva/screenshots/blob/master/configure.png)

* add user token

![alt text](https://github.com/MaryGeraseva/screenshots/blob/master/add%20token.png)

* generate and copy user token

![alt text](https://github.com/MaryGeraseva/screenshots/blob/master/generate%20tocken.png)

![alt text](https://github.com/MaryGeraseva/screenshots/blob/master/copy%20tocken.png)

* open configuration file jenkins_jobs.ini in `[$user.dir]/4-jenkins-job-builder/windows`  
and correct personal authentication data `[$user-name]` and `[$user-token]`
* add jobs with JJB from command-line  
`jenkins-jobs --conf ./jenkins_jobs.ini update ./jobs.yaml`
* check changes in your Jenkins

### How to add jobs in Jenkins on Linux in docker container
[There is my version](https://github.com/MaryGeraseva/6-docker-jenkins-newman-jjb) of Jenkins docker image.   
It based on the official Jenkins docker image and also includes Node.js, Newman, Python, PIP, VIM and JJB.       
This is a fully completed solution for working with Jenkins, JJB, and Postman collections.  

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

## For feedback
**e-mail:** mary.geraseva@gmail.com  
**telegram:** @MaryGeraseva  
**skype:** mary_geraseva  
[linkedIn](https://www.linkedin.com/in/maria-geraseva/)

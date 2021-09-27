# README #

This README would normally document whatever steps are necessary to get your application up and running.

### What is this repository for? ###


### How do I get set up? ###
Import as a maven project using pom.xml
mvn clean install
mvn spring-boot:run

http://localhost:8080/greeting

curl -v localhost:8080/books
curl -v localhost:8080/books/1
curl -v -X POST localhost:8080/books -H "Content-type:application/json" -d "{\"name\":\"Spring REST tutorials\",\"author\":\"developer\",\"price\":\"9.99\"}"
curl -v -X PATCH localhost:8080/books/4 -H "Content-type:application/json" -d "{\"author\":\"oracle\"}"
curl -v -X PATCH localhost:8080/books/4 -H "Content-type:application/json" -d "{\"name\":\"New Spring REST\"}"
curl -v -X DELETE localhost:8080/books/4



##Command to build Docker Image
docker build -t myapacheimage .
docker run -p 80:80 --name=App1  myapacheimage
docker stop App1

docker build -f Dockerfile_Nginx -t mynginximage .
docker run -p 80:80 --name=App2 mynginximage
docker stop App2

## running app in Docker ##
mvn package spring-boot:repackage
docker build -f DockerfileWebApp -t mydockerwebapp .
docker run -p 8085:8085 --name=myapp1 mydockerwebapp
docker stop myapp1



################################
docker system prune -a     == To delete all the images



#########################################
Jenkins docker installation command given below: https://jenkins.io/doc/book/installing/#debian-ubuntu
docker run -u root --rm -d -p 8080:8080 -p 50000:50000 -v jenkins-data:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock jenkinsci/blueocean

This started the jenkins blue ocean docker container: https://hub.docker.com/r/jenkinsci/blueocean/
run as docker run -p 8080:8080 jenkinsci/blueocean
user jenkinsadmin/jenkinsadmin/info@testmail.com
http://localhost:8080/


-------------------------------------------------------------------------
#### Few Git Commands ####
git log --all --decorate --oneline --graph
alias graph="git log --all --decorate --oneline --graph"
create a new branch: git branch branchname - branch name point to the same commit as the checked out branch
git commit -a -m "comment whilt commiting"   --- stages the files and commits with -a option
git diff branch1..branch2
git branch --merged    ----shows what branches are merged
git branch -d branchname    --- to delete branch with name as branchname
--------------------------------
Merging branch1 in to branch2
first checkout branch2
git merge branch1
--------------------------------


Kubernetes:
Checking kubernetes is running or not:
1. Create pod.yaml using below code

apiVersion: v1
kind: Pod
metadata:
  name: demo
spec:
  containers:
  - name: testpod
    image: alpine:3.5
    command: ["ping", "8.8.8.8"]


2. In PowerShell, navigate to where you created pod.yaml and create your pod:
kubectl apply -f pod.yaml
3. Check that your pod is up and running:
kubectl get pods
4. Check that you get the logs you’d expect for a ping process:
kubectl logs demo
5. Finally, tear down your test pod:
kubectl delete -f pod.yaml


Docker Commands:
docker run --detach --name webserver nginx
docker rm $(docker ps -a -q)
winpty docker run --interactive --tty ubuntu bash
winpty docker run -it ubuntu bash
docker run -d -p 80:80 --name webserver nginx
docker run -d -p 80:80 docker/getting-started
docker run -dp 3000:3000 getting-started
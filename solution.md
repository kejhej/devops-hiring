# devops-challenge solution

This work was done on docker for windows that comes with kubernetes as well.
App was dockerized and modification was done so that data in db survives restarts.
Hope it will work for minikube as well.

# in the repo root directory after cloning it
cd devops-hiring

docker run -d -p 5000:5000 --restart=always --name registry registry:2

docker build . -t polls
docker tag polls localhost:5000/polls
docker push localhost:5000/polls

Adjust path to db/ directory that is in repository in polls-deployment.yml depending where you clone this repository
Db file is in db/ directory when you are placed in repository's root directory
Let's say if you clone repo to /home/myuser/devops-hiring then path should be /home/myuser/devops-hiring/db

kubectl.exe apply -f polls-deployment.yml
kubectl.exe apply -f polls-service.yml

http://localhost:30008/polls

credentials to admin panel http://localhost:30008/admin:
admin/alamakota

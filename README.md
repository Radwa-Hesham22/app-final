# Objective

![MicrosoftTeams-image (15)](https://user-images.githubusercontent.com/118529639/221260204-3f77cdc2-e1e1-4796-ae1c-7fcf173dc931.png)

1- Clone app repo

```
git clone https://github.com/Radwa-Hesham22/app-final.git
```
2- Unlock jenkins

```
gcloud compute ssh --zone "asia-east1-b" "private-vm"  --tunnel-through-iap --project "quick-asset-377911"
gcloud container clusters get-credentials primary --zone asia-east1-b --project quick-asset-377911
kubectl get pods -n devops-tools
kubectl exec -it <pod_name> -n devops-tools /bin/bash
cat /var/jenkins_home/secrets/initialAdminPassword
```
Copy password and unlock jenkins on the browser


3- Install plugins

![image](https://user-images.githubusercontent.com/118529639/221268111-0942a079-bdd5-4a9d-9fc9-fc5377688486.png)


4- Create credentials for docker hub by username and password

![image](https://user-images.githubusercontent.com/118529639/221268725-a4cde3ba-a15f-4eb2-ba80-78b8e26d26a6.png)

5-Create credentials for slave 

![image](https://user-images.githubusercontent.com/118529639/221268925-c2a87ed9-c841-44db-b2ad-7c12305d4820.png)

6-Create slave node ,add credentials to it and launch agents via SSH

![image](https://user-images.githubusercontent.com/118529639/221269139-e1adeb3f-432b-4a45-963a-663419a4369c.png)

7-Go back to terminal

```
exit
kubectl get pods -n devops-tools
kubectl exec -it <pod_name> -n devops-tools /bin/bash
service ssh start
passwd jenkins
chown jenkins:jenkins /var/run/docker.sock

```
8- Go back to jenkins slave node and launch

![image](https://user-images.githubusercontent.com/118529639/221270473-05247bbd-c077-4fe7-9bc2-f1011b138bf0.png)

9- Go back to terminal 

```
su jenkins
gcloud auth login
gcloud container clusters get-credentials primary --zone asia-east1-b --project quick-asset-377911
exit 

```
10- In VM

```
gcloud container clusters get-credentials primary --zone asia-east1-b --project quick-asset-377911
kubectl create name space dev

```

11- Back to jenkins on browser and create pipeline using git repo

![image](https://user-images.githubusercontent.com/118529639/221271800-496c1fdd-db51-43bd-b134-34d1cb5bf96e.png)

![image](https://user-images.githubusercontent.com/118529639/221271936-9425297f-19ff-4cd5-8ea8-8d5e481b9a06.png)

12- Build now

![image](https://user-images.githubusercontent.com/118529639/221272140-a062c092-163a-4b6f-9fac-cfac94ea45df.png)

13- App image built and pushed on docker hub

![image](https://user-images.githubusercontent.com/118529639/221272360-1767b9c2-8447-4088-a57e-766e03450d9b.png)

![image](https://user-images.githubusercontent.com/118529639/221272417-6fe0f79d-9666-4bf8-bd6e-a71586bb5ee2.png)

14- Deployment and service are created

![image](https://user-images.githubusercontent.com/118529639/221272619-9d0837c7-bc2f-45a0-b7f0-528333ee5c13.png)

15- Back to terminal 

```
kubectl get svc -n dev

```
16- Check it on your browser by external ip

![image](https://user-images.githubusercontent.com/118529639/221273076-af75b131-3622-4b9b-a32e-292906926a74.png)






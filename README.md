 This is just to demonstrate how docker compose can start more than one application in parrallel
 The demonstration consists of two containers serving two different html content.
 The containers include :
    
   1) Rice page: which you can get by pulling from "docker pull ipsegs/food-site:rice"
    2) Beans Page: which you can get by pulling from "docker pull ipsegs/food-site:beans"

 Using a Dockerfile provided in each page's folder, I was able to configure both the rice and beans containers.

 After that, I created a docker-compose yaml resource to spin up both containers

  Using the "docker-compose up" command, both containers were started.

To be able to perform a name resolution for each page, you can get each containers IP address using this method:

	1) Confirm the name of the network docker-compose is running on:
	   
	docker network ls

	2) confirm the name of the images being run:
	
	docker-compose images

	3) Perform this command for each images

   	docker container inspect --format '{{ .NetworkSettings.Network.docker-compose network.IPAddress }}' docker-compose container 


Remember to replace the 'docker-compose network' with the main docker compose network found in 'docker network ls' 
also docker-compose container with the container name found when using docker-compose images

After getting the ip address

 you can map the ipaddress to the hostname in a config file called /etc/hosts
 
to do this

for example if the ip address gotten for beans is 192.168.49.2

Open the config file with your file editor, either nano or vi:
 sudo vi /etc/hosts

assuming the hostname you have in mind is Beans.food.com, add this to the config file:

192.168.49.2    beans.food.com

close and save, then use the hostname to access the webpage using your web browser.

n/b The hostname to IP address is a temporary fix, if you bring down the running container and try bringing them back up, the IP address may likely change. 

you can repeat the process for hostname to IP resolution. 

thank you


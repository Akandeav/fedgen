# Colab Notebook

## How to Guide  
This document describes how to get the colab notebook hosted  
on the FEDGEN cloud running on your local machine. The notebook  
uses a docker image found [here](https://hub.docker.com/r/sorokine/docker-colab-local "docker image")  

1. Download ssh key file ```victor-key``` from the project folder  

2. ssh into FEDGEN cloud colab instance  
In your terminal enter:  
```ssh -i <victor-key location> ubuntu@172.16.60.154```  
you should be logged in with a prompt like this ```ubuntu@colab``` in your terminal.    

3. Run the following command to launch the colab server  
~~~
docker run \
> -it --rm -p 8081:8081 \
> -v "$PWD":/opt/colab \
> -v $HOME/.cache/torch:/root/.cache/torch \
> sorokine/docker-colab-local:latest
~~~  
if you get a token like this, ```token=5ee95811e30955ce07be864b32299f5f4c4f14d339161460```,  or  
a url like ```http://localhost:8081/?token=abcdef123456...```, proceed to step 4.  
Otherwise, check the [doc](https://hub.docker.com/r/sorokine/docker-colab-local "help")  

4. Port forward the FEDGEN instance on your local machine  

To port forward, on your terminal run:  
```ssh -i <victor-key/location> ubuntu@172.16.60.154 -L 8081:localhost:8081```  
you should be logged in with a prompt like this ```ubuntu@colab``` in your terminal.  
if you recieve an error like ```failed: port is already allocated.```, try changing the port  
after the localhost i.e ```8081:localhost:<this port>``` to an available port on your computer or,  
free the port ```8081``` on your computer.

5. Login on your browser  
enter the url from the FEDGEN cloud instance.  
the url should look like this ```http://localhost:8081/?token=028t6y0...```.  

6. Share with others *(optional)*  
to connect multiple computers to colab while the server is running on the FEDGEN instance, repeat  
steps 4 and 5 on the computer.  
*Do not forget to share the url with collaborators*  


  


## Docker Command Structure

Modern Structure:

`
docker <management command> <sub command> (options) 
` 
  
`
example: docker container run container_name
`          

Old Structure:  

`
docker <command> (options)
`

`
example: docker run container_name
`


## Docker System Commands

Check installation details (client/server).
```
docker version
````
      
Shows Docker disk usage.
```
docker system df
```
      
Removes unused containers, networks, and volumes.
```
docker system prune
```
      
Deletes all unused images.
```
docker image prune -a 
```


##  Docker Configuration

 Authenticate with Docker Hub or other registries.
  ```
docker login
  ```
    
 Logout (recommended for security).
```
docker logout
```

   
## Container Management

List running containers.
```
docker container ls
```

List all containers (including stopped ones).
```
docker container ls -a
```
      
Remove container(s).
```
docker container rm <id>
```
      
Force remove running container.
```
docker container rm -f <id>
```


## Inspecting Containers

Access container shell.
```
docker container exec -it <container> bash
```
      
Show logs.
```
docker container logs <container>
```
      
Show processes.
```
docker container top <container>
```
      
Live resource usage.
```
docker container stats
```
      
Configuration details.
```
docker container inspect <container>
```








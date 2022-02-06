- View all images:
  docker images -a
  
  
- Delete orphaned image artifacts (handy when a Docker build fails part way through):
  docker system prune
  
  
  
- Remove Docker images:
  docker rmi [image_name]:[tag_name]
  
  
- Bash into a running container:
  docker exec -it [containter_name] /bin/bash

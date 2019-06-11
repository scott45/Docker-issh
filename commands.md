docker system prune - (remove stopped containers, networks not used by atleast one container, all dangling images/build cache)
docker volume rm $(docker volume ls -q -f "dangling=true") - remove dangling volumes
docker rm $(docker ps -q -f "status=exited") - remove exited containers
docker rmi $(docker images -q -f "dangling=true") - remove dangling images
docker run -it --rm alpine sh - autoremove interactive container after it exits 
docker info - inspect docker resources
watch -n 2 'docker ps --format "table {{.ID}}\t {{.Image}}\t {{.Status}}"' - display table for active containers refreshed 2 sec 
brew install docker-completion brew install docker-compose-completion - install docker command completion
docker run --restart=always "image" - restart always when the container exits
docker run --restart=on-failure:10 redis - restart container on failure and a maximum restart count of 10
docker run --net=host ... - use docker host network stack
docker run --net=container:<name|id> ... - use another container network stack

# create an attachable overlay network
docker network create --driver overlay --attachable scott

# create bsuinge container and attach it to create scott overlay network
docker run -it -rm --net=scott businge sh

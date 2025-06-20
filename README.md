# Various useful docker build and docker compose files.

## Docker swarms using docker-compose 
To start each of the swarms, simply switch to the folder of interest and run `docker compose up -d`.
If this is the first time you're running it then docker will first pull the latest images (which can be quite large).
Docker will then start the dockers, connect them to a shared network, and connect dockers to volumes to allow persistent usage for the next time you start the swarm.

To update any of the containers just use `docker pull` to update the container and then run again `docker compose up -d`. 
This will shut down only the dockers that were updated and start them up again with the new version

To stop the swarm run `docker compose down`

## Custom dockers using docker build 
Currently there aren't any of those, but perhaps in the future...

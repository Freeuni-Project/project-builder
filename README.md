(Python 3.9 is required for this project to run smoothly)
Please make sure that this structure is satisfied:
-Folder
  -project-service
  -user-service
  -ticket-service
  .
  .
  -project-builder


If you are running this project for the first time make sure you are in the project-builder directory and:

1. Build the docker-compose.deploy file using 
docker-compose -f .\docker-compose.deploy.yml build

2. Run docker containers using (remove -d if you don't want to run it in detach mode)
docker-compose -f docker-compose.deploy.yml up -d

3. For first time run we have to initialize and migrate database, please follow this steps
docker exec -it cuser-service flask db init
docker exec -it cuser-service flask db migrate
docker exec -it cuser-service flask db upgrade

docker exec -it cproject-service flask db init
docker exec -it cproject-service flask db migrate
docker exec -it cproject-service flask db upgrade

docker exec -it cticket-service flask db init
docker exec -it cticket-service flask db migrate
docker exec -it cticket-service flask db upgrade


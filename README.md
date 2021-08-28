(Python 3.9 is required for this project to run smoothly, NPM is required if you are trying to run in locally)<br />
Please make sure that this structure is satisfied:<br />
-Project Directory<br />
&nbsp;&nbsp;-backend-service <br />
&nbsp;&nbsp;-client-service<br />
&nbsp;&nbsp;-statistics-service<br />
&nbsp;&nbsp;.<br />
&nbsp;&nbsp;.<br />
&nbsp;&nbsp;-project-builder<br />

<br />
If you are running this project for the first time make sure you are in the project-builder directory and:<br />

1. create docker micro_network<br />
docker network create micro_network<br />

2. Build the docker-compose.deploy file using<br />
docker-compose -f docker-compose.yml build<br />

3. Run docker containers using (remove -d if you don't want to run it in detach mode)<br />
docker-compose -f docker-compose.yml up -d<br />

4. For first time run we have to initialize and migrate database, please follow this steps<br />
docker exec -it cbackend-service flask db init<br />
docker exec -it cbackend-service flask db migrate<br />
docker exec -it cbackend-service flask db upgrade<br />
docker exec -it cstatistics-service flask db init<br />
docker exec -it cstatistics-service flask db migrate<br />
docker exec -it cstatistics-service flask db upgrade<br />

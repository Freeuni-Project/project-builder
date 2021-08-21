(Python 3.9 is required for this project to run smoothly)<br />
Please make sure that this structure is satisfied:<br />
-Folder<br />
&nbsp;&nbsp;-project-service <br />
&nbsp;&nbsp;-user-service<br />
&nbsp;&nbsp;-ticket-service<br />
&nbsp;&nbsp;.<br />
&nbsp;&nbsp;.<br />
&nbsp;&nbsp;-project-builder<br />

<br />
If you are running this project for the first time make sure you are in the project-builder directory and:<br />

1. create docker micro_network<br />
docker network create micro_networtk<br />

2. Build the docker-compose.deploy file using<br />
docker-compose -f .\docker-compose.deploy.yml build<br />

3. Run docker containers using (remove -d if you don't want to run it in detach mode)<br />
docker-compose -f docker-compose.deploy.yml up -d<br />

4. For first time run we have to initialize and migrate database, please follow this steps<br />
docker exec -it cuser-service flask db init<br />
docker exec -it cuser-service flask db migrate<br />
docker exec -it cuser-service flask db upgrade<br />
docker exec -it cproject-service flask db init<br />
docker exec -it cproject-service flask db migrate<br />
docker exec -it cproject-service flask db upgrade<br />
docker exec -it cticket-service flask db init<br />
docker exec -it cticket-service flask db migrate<br />
docker exec -it cticket-service flask db upgrade<br />


#Volumes have to be created first

docker volume create python-service
docker volume create go-service

#Startup
docker-compose up

#startup flask
sudo docker exec -it microservices-using-rabbitmq_python-service_1 bash

FLASK_APP=main.py python -m flask run --port 3000 --host 0.0.0.0


#startup go listener
sudo docker exec -it microservices-using-rabbitmq_go-service_1 bash
go run main.go

#Note
When running under MacOSX it's easier to have this project in your home path.
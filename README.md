# hackathon-ittalent

Marcello Alexandre e Mogleson Lima

vagrant up
docker build -t marcelloale/go-api-mongo .
docker login -u marcelloale
docker push marcelloale/go-api-mongo
vagrant ssh server2 # server2 CentOs/7
git clone https://github.com/ittalent2023-2/go-mongo-crud-rest-api.git
cd go-mongo-crud-rest-api.git
vi docker-compose.yml
docker-compose up

vagrant ssh server1
vagrant@marcelloemogleson:~$ curl -X GET 'http://10.10.10.12:9080/users/bob@gmail.com'
{"user":{"id":"ObjectID(\"651e06b8e0a8b511bbffe60c\")","name":"Bob","email":"bob@gma
vagrant@marcelloemogleson:~$ e"}}vagrPOST 'http://10.10.10.12:9080/users' -H "Content-Type: application/json" -d '{"name": "Maria", "email": "maria@gmail.com", "password": "ilovejoao"}'{"user":{"id":"ObjectID(\"651e0760e0a8b511bbffe60d\")","name":"Maria","email":"maria@gmail.com","password":"ilovejoao"}}
vagrant@marcelloemogleson:~$ curl -X PUT 'http://10.10.10.12:9080/users/bob@gmail.com' -H "Content-Type: application/json" -d '{"password": "loveyoualice"}'{"user":{"id":"","name":"","email":"bob@gmail.com","password":"loveyoualice"}}
vagrant@marcelloemogleson:~$ curl -X DELETE 'http://10.10.10.12:9080/users/bob@gmail.com'
# Cheatsheets

- [Cheatsheets](#cheatsheets)
  - [Git and Github](#git-and-github)
  - [MongoDB](#mongodb)
  - [JAVA/ MAVEN](#java-maven)
  - [DOCKER](#docker)
    - [Run Individual Microservice](#run-individual-microservice)

## Git and Github

```bash
# copy repository using https protocol
git clone https://github.com/<your-github-account>/<repo-name>.git
# alternative, if public ssh keys added to github account
git clone git@github.com:<your-github-account>/<repo-name>.git

## enter into a working directory (default branch is origin/master)
git checkout <branch-name>
git checkout -b <new-branch-name>
git status

# editing changes 
git add -u . 
git commit -m "your comments"
git push -u <repo> --all

# handling mutliple brances
git checkout <origin>
git pull <origin>
git merge <dev>
git push <origin>

#configurations
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
git remote -v
git remote rm origin
git remote add <name> <url> 
```

## MongoDB

```
.findOne()._id.getTimestamp()
.pretty()
.limit(1).sort({$natural:-1})
.dropped()
db.epod.find({_id: 13}).pretty()
db.epod.find({status: "verified_2"}, { doId: 1})
db.counter.insert( { _id: "counterId" , seq: 0 } )    
```

## JAVA/ MAVEN
```
java -jar target/epod-0.0.1-SNAPSHOT.jar
java -jar target/test-0.0.1-SNAPSHOT.jar --dsq.port="8082"
mvn spring-boot:run
mvn clean package -Dmaven.clean.failOnError=false
mvn clean install
```

## DOCKER

```
docker rm $(docker ps -a -q)
docker rmi $(docker images -a -q)

docker-compose build
docker-compose up -d
docker-compose -f docker-compose.yml up mongodb

docker exec -it mongodb bash
```
 
### Run Individual Microservice

Go to the directory that has your Dockerfile and run the following command to build the Docker image. 
```bash
docker build -t ./dsqServer .
```

Run the image
```bash
docker run -p 49160:8082 -d <your username>/node-web-app
```
In the example above, Docker mapped the 8082 port inside of the container to the port 49160 on your machine.

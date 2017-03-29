# web

Readme for webapp_redis
cd webapp_redis
chomod +x bin/webapp
cd ..
docker network create app
docker network inspect app
docker run -d --net=app --name db uday1bhanu/redis
docker network inspect db
docker run -d -p 4567 --name webapp -v $PWD/webapp_redis:/opt/webapp uday1bhanu/sinatra
docker network inspect db

docker ps
  make sure both(webapp and redis) are running
Test:
docker port webapp_redis
curl -i -H 'Accept: application/json' -d 'name=Foo status=Bar' http://localhost:32781/json
curl -i http://localhost:32781/json

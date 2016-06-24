# mezzanine
mezzanine project in dockerised container on aws

To implement this project in existing aws environment do following steps

docker run -d --name db postgres
docker run -P --name mezzanine_web -p 8000:80 --link db:mezzanine_db harshad007/mezzanine

# mimsic-nginx-reverse-proxy

## How to create the docker image and run the container for mimsic-nginx-reverse-proxy:

Note: arz1120 is docker hub account. you may create your own docker hub account.
To create docker image execute this from the terminal in mimsic-nginx-reverse-proxy directory:
docker build -t arz1120/nginx-reverse-proxy:1 .

To run the container:
docker network create --driver bridge dev-net
docker run -dit --name nginx-reverse-proxy-container --network dev-net -p 80:80 arz1120/nginx-reverse-proxy:1

## How to modify default.conf and create a nginx container without creating docker image:

Run the container from original nginx image:
docker run -dit --name nginx-container -p 80:80 nginx:latest

Copy the default config file from the original nginx container to a folder on the host machine:
docker cp nginx-container:/etc/nginx/conf.d/default.conf /work/default.conf

Modify the default.conf file and copy it from the host machine to the container:
docker cp /work/default.conf nginx-container:/etc/nginx/conf.d/

Restart the container
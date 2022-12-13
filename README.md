# mimsic-nginx-reverse-proxy

How to create the docker image and run the container for mimsic-nginx-reverse-proxy:

Note: arz1120 is docker hub account. you may create your own docker hub account.
To create docker image execute this from the terminal in mimsic-nginx-reverse-proxy directory:
docker build -t arz1120/nginx-reverse-proxy:1 .

To run the container:
docker network create --driver bridge dev-net
docker run -dit --name nginx-reverse-proxy-container --network dev-net -p 80:80 arz1120/nginx-reverse-proxy:1
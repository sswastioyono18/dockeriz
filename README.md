## docker build 
Build dockerfile in this path (represented as .) then tag it as `sactio1811/dockerize:latest`
- `sactio1811` is the dockerhub username
- `dockerize` is the repo name
- `latest` is the version
```
docker build . -t sactio1811/dockerize:latest
```

## docker run 
the image we just built with name `--name dockerize`  forward port 8080 in docker into 29293 in your PC
```
docker run -p 29293:8080 --name dockerize sactio1811/dockerize:latest
```

## docker compose
You can orchestrate multiple container with one command, very useful if you are lazy
```
docker-compose up -d
```

## communication between container
- use network. By default, container run within docker network so they can communicate with each other
- custom network
add `networks` in container you want to put into the network
```
 networks:
   - kb-backend1
```
and add these in the bottom
```
networks:
 kb-backend1:
    external: false
    name: kb-backend1
```



# build smaller image (1/10 original image)
big image size is no no. Focus on making smaller image or using small image (alpine or debian)
```
docker build -f Dockerfile_small_image -t sactio1811/dockerize-small-image:latest .                                                                                                                                                                                                        ✔  at 10:03:34  
```
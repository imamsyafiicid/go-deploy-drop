# Create a file called Dockerfile and fill the configuration
FROM golang:1.23.2-alpine3.20
  # make sure the version match with go.mod
RUN mkdir /app
  # create a app filder
ADD . /app
  # add all files in this repo to the app folder
WORKDIR /app
RUN go build -o main .
CMD ["/app/main"]

# Create image
docker build -t my-go-app .

# running the app manually 
docker run -it -p 8080:8081 my-go-app

# create the container
docker run -d -p 8080:8081 my-go-app

# kill the container
docker kill [id]

# Reference https://www.youtube.com/watch?v=lIbdPrUpGz4
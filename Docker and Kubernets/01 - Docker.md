# Quicky Review
## What is Docker
Is a **containerization** platform, meaning that it enables you to package your applications into images and run them as "**containers**" on any platform that can run Docker.
Solve the problem that a project runs in one machine and not run in another, with Docker is possible to say that will work as expected independent of the enviroment.

![[Pasted image 20250130153736.png]]

## Dockerfile
Instructions that create a image of our application as a container.
We can put this container online.

```DockerFile
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env
WORKDIR /app  

# Copia o projeto e restaura as dependências
COPY *.csproj ./
RUN dotnet restore  

# Copia o restante dos arquivos e publica a aplicação
COPY . ./
RUN dotnet publish -c Release -o out  

# Imagem final
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build-env /app/out .  

# Define o comando de execução
ENTRYPOINT [ "dotnet", "PlatformService.dll" ]
```

Here we create our project image, and we can push to docker hub

## Docker Hub
Here we can save our images and use in others projects.
To create a image we have to create our project image using a dockerfile.

### Build a image
```C#
docker build -t <docker user id>/<image name>:<version> . //Don't forget the DOT

docker build -t kirmct/platformservice .

//Building using visual studio pre config
docker build -t <image name> -f <file location>
docker build -t teste-2 -f Teste2/Dockerfile .
```

### Push a image to Docker Hub
```C#
docker push <docker user id>/<image name>:<version>

docker push kirmct/platformservice


//Publishing using visual studio pre config
docker login -u <docker user id> //colocar senha que pede
docker login -u kirmct

docker tag <image name> <docker user id>/<image name>:<version>
docker push <docker user id>/<tag name>:<version>

docker tag teste-2 kirmct/teste-2:latest
docker push kirmct/platformservice

```

### List Running Docker Containers
```C#
docker ps
```

### Run a Docker Image
```C#
docker run -p <external port>:<internal port> -d <docker user id>/<image name>

docker run -p 8080:80 -d kirmct/platformservice

//Runnig using visual studio pre config
docker run -d -p <external>:<internal docker> --name <container name> <image name>
docker run -d -p 5000:8080 --name teste-2-demo teste-2
```

### Stop Running a Container
```C#
docker stop <container id>
```

### Re-start a Container
```C#
docker start <container id>
```


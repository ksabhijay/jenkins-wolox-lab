# wolox-lab

jenksin X wolox-ci

## Jenkins for this project

> https://github.com/guitarrapc/jenkins-lab/tree/master/wolox

## Project reference

https://github.com/Wolox/rails-bootstrap

## docker build

```shell
$ docker build -t wolox-dotnet -f .woloxci/Dockerfile .

Step 1/10 : FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
 ---> cef7866e800b
Step 2/10 : WORKDIR /app
 ---> Using cache
 ---> f249a8d3adad
Step 3/10 : COPY Sample.csproj .
COPY failed: stat /var/lib/docker/tmp/docker-builder030485339/Sample.csproj: no such file or directory
PS C:\git\guitarrapc\wolox-lab>
PS C:\git\guitarrapc\wolox-lab> docker build -t wolox-dotnet -f .woloxci/Dockerfile .
Sending build context to Docker daemon   47.1kB
Step 1/10 : FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
 ---> cef7866e800b
Step 2/10 : WORKDIR /app
 ---> Using cache
 ---> f249a8d3adad
Step 3/10 : COPY src/Sample.csproj .
 ---> 1706665423aa
Step 4/10 : RUN dotnet restore
 ---> Running in b16476a03051
  Restore completed in 178.26 ms for /app/Sample.csproj.
Removing intermediate container b16476a03051
 ---> 37cd918033d7
Step 5/10 : COPY src/. .
 ---> d834b10daddc
Step 6/10 : RUN dotnet publish -c Release -o out
 ---> Running in afe80ee2d843
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 55.11 ms for /app/Sample.csproj.
  Sample -> /app/bin/Release/netcoreapp3.1/Sample.dll
  Sample -> /app/out/
Removing intermediate container afe80ee2d843
 ---> 58903f420cca
Step 7/10 : FROM mcr.microsoft.com/dotnet/core/runtime:3.1 AS runtime
3.1: Pulling from dotnet/core/runtime
8ec398bc0356: Pull complete
fdb3dcd3402e: Pull complete
ace51becb785: Pull complete
51bc279b6324: Pull complete
Digest: sha256:814490388507af9003abd961d62b5c542ebb5defd98151c6a1092550359b8c46
Status: Downloaded newer image for mcr.microsoft.com/dotnet/core/runtime:3.1
 ---> a708cda756ab
Step 8/10 : WORKDIR /app
 ---> Running in 836a849c1e4f
Removing intermediate container 836a849c1e4f
 ---> 0e05bd1773e3
Step 9/10 : COPY --from=build /app/out ./
 ---> 71a5bc497cde
Step 10/10 : ENTRYPOINT ["dotnet", "Sample.dll"]
 ---> Running in a959fbceb2d3
Removing intermediate container a959fbceb2d3
 ---> 5fd33ba1a1cb
Successfully built 5fd33ba1a1cb
Successfully tagged wolox-dotnet:latest
```

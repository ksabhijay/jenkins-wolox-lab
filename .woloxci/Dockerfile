FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /app

COPY src/Sample.csproj .
RUN dotnet restore

COPY src/. .
RUN dotnet publish -c Release -o out


FROM mcr.microsoft.com/dotnet/core/runtime:3.1 AS runtime
WORKDIR /app
COPY --from=build /app/out ./
ENTRYPOINT ["dotnet", "Sample.dll"]

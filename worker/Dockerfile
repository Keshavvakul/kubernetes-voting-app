FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build

WORKDIR /src

# Restore 
COPY *.csproj .
RUN dotnet restore Worker.csproj

# build 
COPY . .
RUN dotnet build Worker.csproj -c Release -o ./build

# Stage 2: publish stage
FROM build AS publish
RUN dotnet publish 'Worker.csproj' -c Release /publish


# Stage 3: Run Stage
FROM mcr.microsoft.com/dotnet/runtime:7.0 

WORKDIR /app
COPY --from=publish /publish .
ENTRYPOINT ["dotnet", "Worker.dll"]
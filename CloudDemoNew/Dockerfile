#FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build-env
#WORKDIR /app
# Copy csproj and restore as distinct layers
#COPY *.csproj ./
#RUN dotnet restore
# Copy everything else and build
#COPY . ./
#RUN dotnet publish -c Release -o publish
# Build runtime image
#FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
#WORKDIR /app
#COPY --from=build-env /app/out .
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY CloudDemoNew.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -c release -o /app
FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "CloudDemoNew.dll"]

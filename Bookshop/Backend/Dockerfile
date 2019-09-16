FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build-env
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY ASPdotNET/*.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY ASPdotNET/./* ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
WORKDIR /app
COPY --from=build-env /app/out .
ENV ASPNETCORE_URLS=http://+:5001
EXPOSE 5001/tcp
# _name.ddl = ddl file name
ENTRYPOINT ["dotnet", "_name.dll"]
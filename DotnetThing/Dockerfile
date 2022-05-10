FROM mcr.microsoft.com/dotnet/sdk:6.0 as build
WORKDIR /app

COPY DotnetThing.csproj ./ 
# this command pulls down the nuget packages
RUN dotnet restore 
# Copy everything else (unless it is in the .dockerignore file or, if that doesn't exist, the .gitignore file)
COPY . ./ 
RUN dotnet publish -c Release -o out



FROM mcr.microsoft.com/dotnet/runtime:6.0.5
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "DotnetThing.dll"]
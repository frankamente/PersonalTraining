[![Build status](https://dev.azure.com/frankamente/PersonalTraining/_apis/build/status/PersonalTraining-ASP.NET-CI%20(1))](https://dev.azure.com/frankamente/PersonalTraining/_build/latest?definitionId=3)  [![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=PersonalTraining&metric=alert_status)](https://sonarcloud.io/dashboard?id=PersonalTraining)

Comandos para subir una nueva versión a Heroku:
* dotnet publish -c Release
* Copiar el fichero dockerfile que se encuentra en el proyecto PersonalTraining a la carpeta bin/Release/netcoreapp2.1/publish de este mismo proyecto
* heroku login (una vez identificados, ctrl+c)
* heroku container:login
* docker build -t personaltraining ./PersonalTraining/bin/Release/netcoreapp2.1/publish
* docker tag personaltraining registry.heroku.com/personaltraining/web
* docker push registry.heroku.com/personaltraining/web
* heroku container:release web --app personaltraining

Para correrlo en local:
* docker build -t personaltraining ./PersonalTraining/bin/Release/netcoreapp2.1/publish
* docker run -p 8000:80 personaltraining
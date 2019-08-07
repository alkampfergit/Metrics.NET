# How to manually build and publish internal nuget packages.

1. Compile Solution Metrics in release, unload all projects except Metrics and Owin.Metrics
1. Pack with dotnet both projects
	- dotnet pack .\Src\Adapters\Owin.Metrics\Owin.Metrics.csproj --configuration release /p:Version=0.5.4.1001
	- dotnet pack .\Src\Adapters\Owin.Metrics\Owin.Metrics.csproj --configuration release /p:Version=0.5.4.1001
1. Now use a version of nuget packages with credential manager to upload to [this package source](https://dev.azure.com/prxm/Jarvis/_packaging?_a=feed&feed=Proximo) 
	-  .\nuget.exe push -Source "Proximo" -ApiKey AzureDevOps C:\develop\Proximo\Metrics.NET\Src\Metrics\bin\release\metrics.0.5.4.1001.nupkg
	-  .\nuget.exe push -Source "Proximo" -ApiKey AzureDevOps C:\develop\Proximo\Metrics.NET\Src\Adapters\Owin.Metrics\bin\Release\Owin.Metrics.0.5.4.1001.nupkg
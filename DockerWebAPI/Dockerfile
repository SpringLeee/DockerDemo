 FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443 


FROM mcr.microsoft.com/dotnet/sdk:5.0 AS publish
WORKDIR /src
COPY ./ DockerWebAPI/
WORKDIR "/src/DockerWebAPI"
RUN dotnet restore "DockerWebAPI.csproj"
RUN dotnet publish "DockerWebAPI.csproj" -c Release -o /app/publish 
 

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "DockerWebAPI.dll"]
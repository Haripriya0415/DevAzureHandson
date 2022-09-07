

FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443 

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["AzuredemoWebApi/AzuredemoWebApi.csproj", "AzuredemoWebApi/"]
RUN dotnet restore "AzuredemoWebApi/AzuredemoWebApi.csproj"
COPY . .
WORKDIR "/src/AzuredemoWebApi"
RUN dotnet build "AzuredemoWebApi.csproj" -c Release -o /app/build 
FROM build AS publish
RUN dotnet publish "AzuredemoWebApi.csproj" -c Release -o /app/publish 
FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "AzuredemoWebAPi.dll"]
 



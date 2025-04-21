# 1. Byg image
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Kopier filerne fra den lokale mappe til containeren
COPY ./backend /app/backend  # Kopier kun backend-mappen korrekt

# Tjek om projektfilen findes (fejlfinding)
RUN ls -l /app/backend/BookBuddy.Api

# Kør restore og publish for backend
RUN dotnet restore /app/backend/BookBuddy.Api/BookBuddy.Api.csproj
RUN dotnet publish /app/backend/BookBuddy.Api/BookBuddy.Api.csproj -c Release -o /app/out

# 2. Kør image
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app/out . 

# Log output-filerne for fejlfinding
RUN ls -l /app

ENTRYPOINT ["dotnet", "BookBuddy.Api.dll"]

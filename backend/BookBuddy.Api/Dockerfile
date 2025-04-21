# 1. Byg image
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app
COPY . . 
RUN dotnet restore ./backend/BookBuddy.Api/BookBuddy.Api.csproj
RUN dotnet publish ./backend/BookBuddy.Api/BookBuddy.Api.csproj -c Release -o /app/out

# 2. Kør image
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app/out . 

# Log output-filerne for fejlfinding
RUN ls -l /app

ENTRYPOINT ["dotnet", "BookBuddy.Api.dll"]

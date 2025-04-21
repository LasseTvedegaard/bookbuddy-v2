FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Brug den rigtige sti for at kopiere filerne
COPY ./backend/BookBuddy.Api /app/backend

RUN ls -l /app/backend/BookBuddy.Api

RUN dotnet restore /app/backend/BookBuddy.Api/BookBuddy.Api.csproj
RUN dotnet publish /app/backend/BookBuddy.Api/BookBuddy.Api.csproj -c Release -o /app/out

FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app/out .

RUN ls -l /app

ENTRYPOINT ["dotnet", "BookBuddy.Api.dll"]

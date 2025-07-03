FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY ["University backend.csproj", "./"]
RUN dotnet restore "University backend.csproj"
COPY . .
RUN dotnet build "University backend.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "University backend.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "University backend.dll"]

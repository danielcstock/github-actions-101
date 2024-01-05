FROM mcr.microsoft.com/dotnet/runtime:7.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY ["github-actions-101/github-actions-101.csproj", "github-actions-101/"]
RUN dotnet restore "github-actions-101/github-actions-101.csproj"
COPY . .
WORKDIR "/src/github-actions-101"
RUN dotnet build "github-actions-101.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "github-actions-101.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "github-actions-101.dll"]

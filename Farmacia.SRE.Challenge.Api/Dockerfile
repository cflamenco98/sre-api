FROM mcr.microsoft.com/dotnet/aspnet:3.1-focal AS base
WORKDIR /app
EXPOSE 80

ENV ASPNETCORE_URLS=http://+:80
ENV TZ=America/Tegucigalpa

FROM mcr.microsoft.com/dotnet/sdk:3.1-focal AS build
WORKDIR /src
COPY ["Farmacia.SRE.Challenge.Api.csproj", "./"]
RUN dotnet restore "Farmacia.SRE.Challenge.Api.csproj"
COPY . .
RUN dotnet build "Farmacia.SRE.Challenge.Api.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Farmacia.SRE.Challenge.Api.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Farmacia.SRE.Challenge.Api.dll"]

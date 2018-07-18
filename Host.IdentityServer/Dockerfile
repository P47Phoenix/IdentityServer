FROM microsoft/dotnet:2.1.2-aspnetcore-runtime-stretch-slim-arm32v7 AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /src
COPY . .
RUN dotnet publish -c Release -o /app -r linux-arm

FROM base AS final
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "Host.IdentityServer.dll"]

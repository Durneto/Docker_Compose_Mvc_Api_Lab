FROM microsoft/dotnet:2.1-sdk AS build-env
WORKDIR /web

# Copiar csproj e restaurar dependencias
COPY *.csproj ./
RUN dotnet restore

# Build da aplicacao
COPY . ./
RUN dotnet publish -c Release -o out

# Build da imagem
FROM microsoft/dotnet:2.1-aspnetcore-runtime AS runtime
WORKDIR /web
COPY --from=build-env /web/out .
ENTRYPOINT ["dotnet", "Frontend.dll"]

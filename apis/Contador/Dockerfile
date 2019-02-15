FROM microsoft/dotnet:2.1-sdk as build-env
WORKDIR /app

# Copia o arquivo csproj e restaura as dependencias
COPY *.csproj ./
RUN dotnet restore

# Builda a aplicação
COPY . ./
RUN dotnet publish -c Release -o out

# builda a imagem
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT [ "dotnet", "Contador.dll" ]
FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
WORKDIR /src/

COPY /src/*.csproj ./
RUN dotnet restore

COPY ./src ./

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
WORKDIR /
COPY --from=build /src/out /

EXPOSE 80
ENTRYPOINT ["dotnet", "Approve.dll"]
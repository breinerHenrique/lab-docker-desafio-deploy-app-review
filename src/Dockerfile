FROM mcr.microsoft.com/dotnet/sdk:5.0 as build
WORKDIR /source
COPY *sln .
COPY /Review.Web/*.csproj ./Review.Web/
RUN dotnet restore

COPY /Review.Web/ ./Review.Web
RUN dotnet publish -c release -o /app --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app
COPY --from=build /app ./
EXPOSE 8282
ENTRYPOINT ["dotnet", "Review.Web.dll"]
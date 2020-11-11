FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS publish
COPY ["src/Blogifier/Blogifier.csproj", "source/Blogifier/"]
COPY ["src/Blogifier.Core/Blogifier.Core.csproj", "source/Blogifier.Core/"]
COPY ["src/Blogifier.Models/Blogifier.Models.csproj", "source/Blogifier.Models/"]
RUN dotnet restore source/Blogifier/Blogifier.csproj
WORKDIR /source
COPY /src .
RUN dotnet publish "Blogifier/Blogifier.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "Blogifier.dll"]
# Use the official .NET SDK image as the base image
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the .csproj and .nuget files to the container
COPY *.csproj .
COPY NuGet.Config .

# Restore NuGet packages
RUN dotnet restore

# Copy the rest of the source code to the container
COPY . .

# Build the application
RUN dotnet publish -c Release -o out

# Create a smaller runtime image
FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "YourApp.dll"]

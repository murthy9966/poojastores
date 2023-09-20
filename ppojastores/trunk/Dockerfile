
FROM mcr.microsoft.com/dotnet/sdk:3.1 
COPY . /app/
WORKDIR /app/
RUN dotnet build
RUN dotnet run
EXPOSE 8086
ENTRYPOINT ["dotnet", "run", "--urls", "http://0.0.0.0:5000"]

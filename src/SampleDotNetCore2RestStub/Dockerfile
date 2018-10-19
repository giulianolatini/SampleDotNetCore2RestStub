FROM microsoft/dotnet:2.0-sdk AS build
WORKDIR /root/
COPY *.csproj ./
RUN dotnet restore
COPY . ./
RUN dotnet publish -c Release -o output

FROM microsoft/dotnet:2.0-sdk
WORKDIR /root/
COPY --from=build /root/output .

ENV ASPNETCORE_ENVIRONMENT docker
ENV ASPNETCORE_URLS="http://*:80"
EXPOSE 80/tcp

ENTRYPOINT ["dotnet", "SampleDotNetCore2RestStub.dll"]
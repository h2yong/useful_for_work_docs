```shell
docker run -it -d --rm -p 5050:8080 -p 8443:8443 --name wiremock -v /data/wiremock:/home/wiremock wiremock/wiremock:2.34.0 --https-port 8443 --verbose
```
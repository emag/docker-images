# kie-wb

KIE Workbench + WildFly Dockerfile

## Usage

### Build Docker image

``` sh
$ docker build -t kie-wb .
```

### Run Docker container

``` sh
$ docker run -it --rm -p 8080:8080 kie-wb
```

Access http://localhost:8080/kie-wb/

| user     | password  |
|----------|-----------|
| mariano  | mypass    |

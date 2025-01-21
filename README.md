## Docker Compose:
### Executando uma aplicação HTML num container apache (HTTPD)

- Estrutura do projeto:
  
  ```  
  - compose.yml
  - website
      - index.html
  ```

  [compose.yml](https://github.com/vivianikelly/docker-projeto1-dio/blob/main/compose.yml)

  ```
  services:
  apache:
    image: httpd:latest
    container_name: my-apache-app
    ports:
    - '8080:80'
    volumes:
    - ./website:/usr/local/apache2/htdocs
  ```

- Implantação com docker compose

```
$ docker-compose up -d
Creating network "docker-projeto1-dio_default" with the default driver
Creating my-apache-app ... done
```

- Resultado esperado

Apresentou o contêiner em execução e o mapeamento de portas conforme abaixo:

```
$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                       NAMES
5e00cc447c91   httpd:latest   "httpd-foreground"       2 minutes ago   Up 2 minutes   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp     my-apache-app

Após o aplicativo iniciar, foi executado curl para validação:

```
$ curl localhost:8080
<html>
<h3>Hello World!! Este é o meu primeiro projeto Docker!</h3>
</html>
```

- Parado e removido o contêiner

```
$ docker compose down
 ✔ Container my-apache-app              Removed                                                                                                       
 ✔ Network docker-projeto1-dio_default  Removed
```

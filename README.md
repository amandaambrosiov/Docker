# 🐳 Guia Rápido - Docker (Windows e Linux)

Docker é uma plataforma de código aberto que automatiza o processo de construção, distribuição e execução de aplicativos dentro de containers. Ele permite que os desenvolvedores empacotem seus aplicativos e suas dependências em containers portáteis, garantindo que o aplicativo tenha o mesmo ambiente em qualquer lugar que seja executado.

## Instalação

### Windows: 

Docker Desktop for Windows 
> Necessário instalar WSL no Windows. 
~~~
wsl --install
~~~

### Linux:
~~~
sudo apt-get update
sudo apt-get install docker.io'
~~~~

## Comandos principais

#### Verificar versão:

~~~
docker --version
~~~

#### Iniciar o Docker:

~~~
sudo systemctl start docker
~~~

#### Verificar status do Docker:

~~~
sudo systemctl status docker
~~~

#### Lista todas as imagens:

~~~
docker images
~~~

#### Listar containers em execução:

~~~
docker ps
~~~

#### Listar todos os containers (inclusive os parados):

~~~
docker ps -a
~~~

#### Parar um container:

~~~
docker stop <nome_do_container>
~~~

#### Remover um container:

~~~
docker rm <nome_do_container>
~~~

#### Remover uma imagem:

~~~
docker rmi <nome_da_imagem>
~~~

#### Exibir logs de um container:

~~~
docker logs <nome_do_container>
~~~

#### Ver o uso de recursos (CPU, memória):

~~~
docker stats
~~~

## Comandos principais Docker Compose

#### Iniciar os serviços definidos no docker-compose.yml:

~~~
docker-compose up
~~~

#### Iniciar os serviços em segundo plano:

~~~
docker-compose up -d
~~~

#### Parar os serviços:

~~~
docker-compose down
~~~

#### Ver o status dos containers:

~~~
docker-compose ps
~~~

## Exemplos de Arquivos

#### Estrutura básica de um Dockerfile

~~~
# Usa uma imagem base oficial
FROM node:18

# Cria o diretório da aplicação
WORKDIR /app

# Copia os arquivos do projeto
COPY . .

# Instala as dependências
RUN npm install

# Expõe a porta usada pelo app
EXPOSE 3000

# Comando para rodar o app
CMD ["npm", "start"]
~~~

O Dockerfile é um arquivo de texto que contém uma sequência de instruções para montar uma imagem Docker personalizada. Ele funciona como uma receita que define o ambiente da sua aplicação.

#### Exemplo básico de docker-compose.yml

~~~
version: "3.8"

services:
  web:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/app
    depends_on:
      - db

  db:
    image: postgres
    restart: always
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydatabase
~~~

É um arquivo YAML que permite orquestrar múltiplos containers (serviços) de forma simples. Você pode configurar a aplicação, o banco de dados, volumes, redes e muito mais em um só lugar.

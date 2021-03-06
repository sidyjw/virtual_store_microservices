# Virtual Store 


## Tópicos


## Descrição do Projeto

> Status do Projeto: Em Desenvolvimento

Loja virtual com o objetivo de solidificar o conhecimento em microsserviços, ASP.NET Core, Docker, MongoDB, RabbitMQ, Redis e Ocelot API Gateway.

## Instruções para executar o projeto

Primeiramente, clone o repositório:

```
  git clone https://github.com/sidyjw/virtual_store_microservices.git
```    

O projeto fornece suporte ao Docker, caso deseje utilizar o docker-compose basta executar os seguintes comandos na pasta raiz do projeto:

```
  cd src
  docker-compose -f docker-compose.yml -f docker-compose.override.yml up -d
```

## Microsserviços


## API Catalog com MongoDB


### Descrição

API REST responsável pelo CRUD dos produtos. Foi usado o **[Repository pattern](https://docs.microsoft.com/en-us/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)** para realizar as operações nos dados.

A persistência é feita pelo **MongoDB** e é utilizado o [driver oficial](https://docs.mongodb.com/drivers/csharp/) para manipular o banco de dados.


### Dependências



* [MongoDB.Driver ](https://www.nuget.org/packages/MongoDB.Driver/2.13.0)


## API Basket com Redis


### Descrição

API REST responsável pelo CRUD dos carrinhos de compra. Foi usado o **[Repository pattern](https://docs.microsoft.com/en-us/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)** para realizar as operações nos dados.

É feito um cache dos dados utilizando o **Redis**. O repository usa o [driver oficial](https://www.nuget.org/packages/Microsoft.Extensions.Caching.StackExchangeRedis/5.0.1) do Redis para realizar as manipulações dos dados.

As informações de disconto são obtidas ao consumir o [Serviço gRPC Discount](#serviço-grpc-discount-com-postgresql).

### Dependências



* [Microsoft.Extensions.Caching.StackExchangeRedis](https://www.nuget.org/packages/Microsoft.Extensions.Caching.StackExchangeRedis/5.0.1)
* Microsoft.VisualStudio.Azure.Containers.Tools.Targets
* [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/13.0.1)
* [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/)


## API Discount com PostgreSQL


### Descrição

API REST responsável por gerenciar os cupons de desconto. Para auxiliar na manipulação do banco PostgreSQL foi usado o [Dapper ORM](https://dapper-tutorial.net/dapper).

A escolha do **Dapper** foi feita para poder atingir uma alta performance nas querys ao mesmo tempo em que exemplifica a flexibilidade da arquitetura de microsserviços por mostrar que é possível usar várias formas de armazenar os dados. 


### Dependências



* [Dapper](https://dapper-tutorial.net/dapper)
* Microsoft.VisualStudio.Azure.Containers.Tools.Targets
* [Npgsql](https://www.nuget.org/packages/Npgsql/5.0.7)
* [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/)


## Serviço gRPC Discount com PostgreSQL

### Descrição

Serviço [gRPC](https://grpc.io) responsável por gerenciar os cupons de desconto.

Esse serviço será consumido pela [Api Basket](#api-basket-com-redis). Por isso, utilizei o gRPC para realizar a [comunicação entre processos.](https://pt.wikipedia.org/wiki/Comunica%C3%A7%C3%A3o_entre_processos)

### Dependências

* [AutoMapper.Extensions.Microsoft.DependencyInjection](https://www.nuget.org/packages/AutoMapper.Extensions.Microsoft.DependencyInjection/8.1.1/)
* [Grpc.AspNetCore](https://www.nuget.org/packages/Grpc.AspNetCore/2.34.0/)
* [Dapper](https://dapper-tutorial.net/dapper) 
* [Npgsql](https://www.nuget.org/packages/Npgsql/5.0.7)

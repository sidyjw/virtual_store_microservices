# Virtual Store 


## Tópicos


## Descrição do Projeto

> Status do Projeto: Em Desenvolvimento

Loja virtual com o objetivo de solidificar o conhecimento em microsserviços, ASP.NET Core, Docker, MongoDB, RabbitMQ, Redis e Ocelot API Gateway.


## Microsserviços


## API Catalog com MongoDB


### Descrição

API REST responsável pelo CRUD dos produtos. Foi usado o **[Repository pattern](https://docs.microsoft.com/en-us/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application) **para realizar as operações nos dados.

A persistência é feita pelo **MongoDB** e é utilizado o [driver oficial](https://docs.mongodb.com/drivers/csharp/) para manipular o banco de dados.


### Dependências

* [MongoDB.Driver ](https://www.nuget.org/packages/MongoDB.Driver/2.13.0)


## API Basket com Redis


### Descrição

API REST responsável pelo CRUD dos carrinhos de compra. Foi usado o **[Repository pattern](https://docs.microsoft.com/en-us/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application) **para realizar as operações nos dados.

É feito um cache dos dados utilizando o **Redis**. O repository usa o [driver oficial](https://www.nuget.org/packages/Microsoft.Extensions.Caching.StackExchangeRedis/5.0.1) do Redis para realizar as manipulações dos dados.


### Dependências

* [Microsoft.Extensions.Caching.StackExchangeRedis](https://www.nuget.org/packages/Microsoft.Extensions.Caching.StackExchangeRedis/5.0.1)
* Microsoft.VisualStudio.Azure.Containers.Tools.Targets
* [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/13.0.1)
* [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/)
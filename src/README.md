# Virtual Store 


## T�picos


## Descri��o do Projeto

> Status do Projeto: Em Desenvolvimento

Loja virtual com o objetivo de solidificar o conhecimento em microsservi�os, ASP.NET Core, Docker, MongoDB, RabbitMQ, Redis e Ocelot API Gateway.


## Microsservi�os


## API Catalog com MongoDB


### Descri��o

API REST respons�vel pelo CRUD dos produtos. Foi usado o **[Repository pattern](https://docs.microsoft.com/en-us/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application) **para realizar as opera��es nos dados.

A persist�ncia � feita pelo **MongoDB** e � utilizado o [driver oficial](https://docs.mongodb.com/drivers/csharp/) para manipular o banco de dados.


### Depend�ncias

* [MongoDB.Driver ](https://www.nuget.org/packages/MongoDB.Driver/2.13.0)


## API Basket com Redis


### Descri��o

API REST respons�vel pelo CRUD dos carrinhos de compra. Foi usado o **[Repository pattern](https://docs.microsoft.com/en-us/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application) **para realizar as opera��es nos dados.

� feito um cache dos dados utilizando o **Redis**. O repository usa o [driver oficial](https://www.nuget.org/packages/Microsoft.Extensions.Caching.StackExchangeRedis/5.0.1) do Redis para realizar as manipula��es dos dados.


### Depend�ncias

* [Microsoft.Extensions.Caching.StackExchangeRedis](https://www.nuget.org/packages/Microsoft.Extensions.Caching.StackExchangeRedis/5.0.1)
* Microsoft.VisualStudio.Azure.Containers.Tools.Targets
* [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/13.0.1)
* [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/)
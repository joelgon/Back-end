## Teste Prático Back-end Pleno O POVO


### Introdução

Sistema para Jornalistas (com autenticação)

Desenvolva uma **API** voltada para jornalistas onde os mesmos poderão criar, editar, excluir e listar notícias e tipos de notícias. A API deverá ser desenvolvida em **NODEJS**, utilizando o framework nestjs. docker-compose para criar uma instancia do redis para simular uma fila sqs.

É de suma importância se utilizar das melhores práticas para um projeto seguro e organizado, como a utilização de **controllers**, **Guards**, **Interceptors** ou semelhantes, controle de exceções, utilização de um **ORM** (*Object Relational Mapper*) para operações de banco de dados *(Eloquent, Doctrine ou outro*). Utilize um **banco de dados relacional** para persistir os dados da aplicação (*PostgreSQL de preferência*).

Para que os Jornalistas possam realizar suas operações básicas eles devem estar autenticados no sistema. Utilize **JWT** (*JSON Web Token*) para controle de autenticação gerando um Token com **5 MINUTOS** de expiração.

#### Entidades

-	**Jornalistas do Jornalista**
	-	Id - Primary Key
	-	Nome - Obrigatório
	-	Sobrenome - Obrigatório
	-	Email - Obrigatório
	-	Senha (Criptografada) - Obrigatório

- **Notícias**
	- Id da notícia - Primary Key
	- Id do jornalista - Obrigatório
	- Id do tipo da notícia - Obrigatório
	- Título - Obrigatório
	- Descrição - Obrigatório
	- Corpo da notícia - Obrigatório
	- Imagem de destaque (link) - Não obrigatório

- **Tipos de Notícia**
	- Id - Primary Key
	- Id do Jornalista - Obrigatório
	- Nome do Tipo - Obrigatório

*Caso queira, você poderá criar propriedades.*

#### Rotas Obrigatórias:

- **Jornalistas**
	- **POST /api/register** (rota para criação de novos jornalistas)
	- **POST /api/login** (rota para autenticação jornalistas)
	- **POST /api/me** (rota que retorna os dados do jornalista, a senha deverá estar oculta. Essa rota necessita de autenticação)

- **Notícias** (Todas as requisições para as rotas de Notícias devem ser autenticadas por um token JWT gerado para o jornalista)
	- **POST /api/news/create** (Cria uma notícia)
	- **POST /api/news/update/{news_id}** (Altera uma notícia do jornalista)
	- **POST /api/news/delete/{news_id}** (Exclui uma notícia do jornalista)
	- **GET /api/news/me** (Lista todas as notícias do jornalista)
	- **GET /api/news/type/{type_id}** (Lista todas as notícias do jornalista por tipo)

- **Tipos de Notícias** (Todas as requisições para as rotas de Notícias devem ser autenticadas por um token JWT gerado para o jornalista)
	- **POST /api/type/create** (Cria um novo tipo de notícia)
	- **POST /api/type/update/{type_id}** (Altera um tipo de notícia do jornalista)
	- **POST /api/type/delete/{type_id}** (Exclui um tipo de notícia do jornalista, uma exceção deverá ser lançada caso se tente deletar uma notícia que esteja sendo referenciada em Notícias)
	- **GET /api/type/me** (Lista todos os tipos notícias do jornalista)

#### Eventos Obrigatórios:
- **Criação de jornalista** emitir um evento que dispara um e-mail contendo o novo jornalista
- **Criação de notícia** emitir um evento que dispara um e-mail contendo a notícia

## Processo de submissão

O teste deve ser **versionado e disponibilizado no GitHub do candidado**.  
Enviar o link para:  [joel.goncalves@gcbinvestimentos.com](mailto:joel.goncalves@gcbinvestimentos.com)

Boa sorte a todos e  
Bom trabalho!!

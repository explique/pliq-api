# pliq-api
https://www.pliq.io

Esse é um repositório para auxílio na API PliQ - Lealdade e Qualificação.

Colocaremos materiais e webhooks para que a integração seja facilitada.
Nota: Qualquer erro ou sugestão, por favor nos contate.

## Instruções para realizar a integração

### URL de acesso

https://api.pliq.io/api/ (Para clientes ambiente de produção)

ou

https://sandboxapi.pliq.io/api/ (Para ambiente de sandbox)

## Requisição HTTP
Seguimos a estrutura padrão do estilo RESTful

GET: lista ou consulta dados
POST: criação de dados
PUT: atualização de dados
DELETE: remoção de dados
Dica: quando estiver listando, você pode escolher os campos que deseja trazer enviando o parâmetro "attribute" na URL.

### Como autenticar
É necessário passar o token privado de autenticação para conseguir realizar as operações. Para conseguir esse token, acesse na PliQ a seção Companhia -> Integrações -> Tokens.

### Códigos de respostas

* 200 (application/json)
> Sucesso

* 401 (text/json)
> Algum parâmetro enviado errado

* 403 (text/json)
> Acesso negado

* 404 (text/json)
> Registro não encontrado

* 500 (text/json)
> Erro do servidor

### Padrão de endpoints

```
Para listagem, use GET: /endpoint/
Para inserção, use POST: /endpoint/
```

## Header
A requisição deve conter:

* Content-Type: application/json
* Access-Token: SEU_TOKEN_AQUI

### Seções (endpoints) disponíveis

Segue as seções que você pode acessar pela API

#### Listar Pesquisas

Para listar as pesquisas utilizaremos a seguinte configuração

* O método usado será : 
> GET
* A URL usada será : 
> <url_acesso>/survey/all

Esse método é responsável por listar todas as pesquisas, seus códigos e alguns detalhes, como por exemplo as perguntas usadas.

Para pegar o código de uma pesquisa específica, deve-se primeiro listar todas as pesquisas e pegar o atributo "code" do retorno.

#### Enviar Transmissão

Para enviar a transmissão utilizaremos a seguinte configuração

* O método usado será : 
> POST
* A URL usada será : 
> <url_acesso>/survey/transmission

Esse método é responsável por transmitir pesquisas, para uma determinada pesquisa a partir do seu código que foi identificado no método de Listagem de Pesquisas.

```
{
	"Token": {
		"code": "token_code"
	},
	"Survey": {
		"code": "survey_code"
	},
	"Customer": {
		"name": "customer_name",
		"phone": "customer_phone"
	}
}
```

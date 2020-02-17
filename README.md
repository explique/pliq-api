# pliq-api
https://www.pliq.io

Esse é um repositório para auxílio na API PliQ - Lealdade e Qualificação.

Colocaremos materiais e webhooks para que a integração seja facilitada.
Nota: Qualquer erro ou sugestão, por favor nos contate.

## Instruções para realizar a integração

### URL de acesso

https://api.pliq.io/api/ (Para clientes ambiente de produção)

ou

https://pliqapisandbox.azurewebsites.net/api/ (Para ambiente de sandbox)

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

* O método usado será : 
> GET
* A URL usada será : 
> <url_acesso>/survey/all

Para listar as pesquisas utilizaremos a seguinte configuração.

Esse método é responsável por listar todas as pesquisas, seus códigos e alguns detalhes, como por exemplo as perguntas usadas.

O body deve ser preenchido usando o seguinte padrão:

```
{
    "code": "token_code"
}
```

Parâmetros 

Parâmetro | Tipo | Obrigatório | Descrição
------------ | ------------- | ------------ | -------------
token_code | String | Sim | Chave do token da empresa. Obtida na tela de integrações.

##### Retorno

```
[
    {
        "title": "survey_title",
        "description": "survey_description",
        "code": "survey_code",
        "active": "survey_active",
        "createdat": "survey_createdat",
        "questions": [
            {
                "title": "question_title",
                "sequence": "question_sequence"
            }
        ]
    }
] 
```

#### Enviar Transmissão

* O método usado será : 
> POST
* A URL usada será : 
> <url_acesso>/survey/transmission

Onde __survey_code__ é o código da pesquisa para qual você deseja disparar.

Para enviar a transmissão utilizaremos a seguinte configuração.

Esse método é responsável por transmitir para uma determinado contato a partir do seu código que foi identificado no método de Listagem de Pesquisas.

O body deve ser preenchido usando o seguinte padrão:

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

Parâmetros 

Parâmetro | Tipo | Obrigatório | Descrição
------------ | ------------- | ------------ | -------------
token_code | String | Sim | Chave do token da empresa. Obtida na tela de integrações.
survey_code | String | Sim | Chave da pesquisa. Obtida no método __<url_acesso>/survey/all__.
customer_name | String | Sim | Nome do cliente.
customer_phone | String | Sim | Telefone do cliente.

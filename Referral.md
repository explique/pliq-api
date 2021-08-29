# pliq-api
https://www.pliq.io

Esse é um repositório para auxílio na API PliQ - Experiência e Fidelização de Clientes.

Colocaremos materiais e webhooks para que a integração seja facilitada.
Nota: Qualquer erro ou sugestão, por favor nos contate.

## Instruções para realizar a integração

### URL de acesso

https://api.pliq.io/v1/api (Para clientes ambiente de produção)

ou

https://sandboxpliqapi.azurewebsites.net/v1/api (Para ambiente de sandbox)

## Requisição HTTP
Seguimos a estrutura padrão do estilo RESTful

GET: lista ou consulta dados
POST: criação de dados
PUT: atualização de dados
DELETE: remoção de dados
Dica: quando estiver listando, você pode escolher os campos que deseja trazer enviando o parâmetro "attribute" na URL.

### Como autenticar
É necessário passar o token privado de autenticação para conseguir realizar as operações. Para conseguir esse token, acesse na PliQ a seção Integrações -> Tokens.

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

### Seções (endpoints) disponíveis

Segue as seções que você pode acessar pela API

### Listar Programas de Indicação

* O método usado será : 
> GET
* A URL usada será : 
> <url_acesso>/referral_program/all

Para listar os programas de indicação utilizaremos a seguinte configuração.

Esse método é responsável por listar todos os programas de indicação.

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
        "id": "referral_id",
        "name": "referral_name",
        "coin_name": "referral_coin_name",
        "active": "referral_active",
        "startdate": "referral_startdate",
        "enddate": "referral_enddate",
        "url_program": "referral_url_program",
        "enddate": "referral_enddate",
	"pipeline": "referral_pipeline",
	"pipeline_internal_id": "referral_pipeline_internal_id",
        "language": "referral_language",     
        "url_photo": "referral_url_photo",     
        "url_banner": "referral_url_banner"
    }
] 
```

### Listar Membros do Programa

* O método usado será : 
> GET
* A URL usada será : 
> <url_acesso>/referral_program/members

### Listar Indicações do Programa

* O método usado será : 
> GET
* A URL usada será : 
> <url_acesso>/referral_program/referrals

### Listar Produtos

* O método usado será : 
> GET
* A URL usada será : 
> <url_acesso>/products/all

Para listar os produtos utilizaremos a seguinte configuração.

Esse método é responsável por listar todos os produtos.

#### Retorno

```
[
    {
        "id": "product_id",
        "name": "product_name",
        "sku": "product_sku",
	"price": "product_price",
	"commission_amount": "product_commission_amount",
	"commission_percentage": "product_commission_amount"
    }
] 
```


### Listar Pipelines

* O método usado será : 
> GET
* A URL usada será : 
> <url_acesso>/pipelines/all

Para listar todos os pipelines utilizaremos a seguinte configuração.

Esse método é responsável por listar todos os pipelines.

#### Retorno

```
[
    {
        "id": "pipeline_id",
        "name": "pipeline_name",
        "internal_id": "pipeline_internal_id"
    }
] 
```

### Listar as fases do Pipeline

* O método usado será : 
> GET
* A URL usada será : 
> <url_acesso>/pipelines/stages/?pipeline_internal_id=

Para listar as fases de um pipeline utilizaremos a seguinte configuração.

Esse método é responsável por listar todas fases de um pipeline.

#### Retorno

```
[
    {
        "id": "stage_id",
        "name": "stage_name",
        "internal_id": "stage_internal_id",
	"win_probability": "stage_win_probability",
	"sequence": "stage_sequence"
    }
] 
```

### Negar Indicação 

* O método usado será : 
> POST
* A URL usada será : 
> <url_acesso>/referral_program/referral/changestatus

O body deve ser preenchido usando o seguinte padrão:

```
{
	"token": {
		"code": "token_code"
	},
	"referral_share": {
		"id": "referral_share_id",    
		"member_code": "referral_member_code",            
		"referral_program_id": "referral_program_id",
		"stage_internal_id": "stage_internal_id",
        	"status_lost": "referral_status_lost",
        	"details": "referral_details",
        	"createdat": "referral_createdat"
	}
}
```

#### Retorno

```
{
	"message": "Success"
}
```

### Aprovar Indicação

* O método usado será : 
> POST
* A URL usada será : 
> <url_acesso>/referral_program/referral/approve

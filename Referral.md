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
> <url_acesso>/referral_program/member/all

### Listar Indicações do Programa

* O método usado será : 
> GET
* A URL usada será : 
> <url_acesso>/referral_program/referral/all

### Listar Produtos

* O método usado será : 
> GET
* A URL usada será : 
> <url_acesso>/product/all

Para listar os produtos utilizaremos a seguinte configuração.

Esse método é responsável por listar todos os produtos.

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
> <url_acesso>/pipeline/all

Para listar todos os pipelines utilizaremos a seguinte configuração.

Esse método é responsável por listar todos os pipelines.

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
> <url_acesso>/pipeline/stage/?pipeline_internal_id=

Para listar as fases de um pipeline utilizaremos a seguinte configuração.

Esse método é responsável por listar todas fases de um pipeline.

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

### Listar Status de Motivo de Perda de Negócio

* O método usado será : 
> GET
* A URL usada será : 
> <url_acesso>/status_lost/all

Para listar os status de motivo de perda de negócio utilizaremos a seguinte configuração.

Esse método é responsável por listar todos os  motivos de perda de negócio.

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

#### Retorno

```
[
    {
        "id": "status_lost_id",
        "name": "status_lost_name",
        "internal_id": "status_lost_internal_id"
    }
] 
```

### Mudar Status da Indicação 

* O método usado será : 
> POST
* A URL usada será : 
> <url_acesso>/referral_program/referral/stage_change

O body deve ser preenchido usando o seguinte padrão:

```
{
	"token": {
		"code": "token_code"
	},
	"referral_share": {
		"id": "referral_share_id",    
		"referral_program_id": "referral_program_id",		
		"member_code": "referral_member_code",            
		"stage_internal_id": "stage_internal_id",
        	"status_lost_internal_id": "referral_status_lost_internal_id",
        	"details": "referral_details",
        	"createdat": "referral_createdat",
		"products": [{
			"sku": "product_sku",
			"price": "product_price",
			"quantity": "product_quantity"		
		}]
	}
}
```

Parâmetros 

Parâmetro | Tipo | Obrigatório | Descrição
------------ | ------------- | ------------ | -------------
token_code | String | Sim | Chave do token da empresa. Obtida na tela de integrações.
referral_share_id | String | Sim | Chave da indicação. Obtida no método __<url_acesso>/referral_program/referral/all__.
referral_program_id | String | Sim | Chave do programa de indicação. Obtida no método __<url_acesso>/referral_program/all__.
member_code | String | Sim | Chave do membro. Obtida no método __<url_acesso>/referral_program/member/all__.
stage_internal_id | String | Sim | Chave da fase. Obtida no método __<url_acesso>/pipeline/stage/?pipeline_internal_id=__.
status_lost_internal_id | String | Sim* | Em caso de fase onde o negócio foi perdido. Chave do status de perda do negócio via indicação. Obtida no método __<url_acesso>/status_lost/all__.
details | String | Não | Detalhes sobre o motino do negócio da indicação perdida.
createdat | Timestamp | Não | Data que ocorreu a mudança de fase da indicação.
products | Array<object> | Sim* | Em caso de fase onde onde o negócio foi realizado.
product_sku | String | Sim* | Código do produto ou serviço que foi realizado o negócio.	
product_price | String | Sim* | Valor do produto ou serviço que foi realizado o negócio.
product_quantity | String | Sim* | Quantidade do produto ou serviço que foi realizado o negócio.

#### Retorno

```
{
	"message": "Success"
}
```

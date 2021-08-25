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

### Negar Indicação 

* O método usado será : 
> POST
* A URL usada será : 
> <url_acesso>/referral/deny

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
        	"status_lost": "referral_status_lost",
        	"details": "referral_details",
        	"createdat": "referral_createdat"
	}
}
```

#### Retorno

```
[
    {
        "message": "Success"
    }
] 
```

### Aprovar Indicação

* O método usado será : 
> POST
* A URL usada será : 
> <url_acesso>/referral/approve

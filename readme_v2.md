# pliq-api
https://www.pliq.io

Esse é um repositório para auxílio na API PliQ - Unindo clientes e empresas ao redor do mundo.

Colocaremos materiais e webhooks para que a integração seja facilitada.
Nota: Qualquer erro ou sugestão, por favor nos contate.

## Instruções para realizar a integração

### URL de acesso

https://api.pliq.io/v2/api (Para clientes ambiente de produção)

ou

https://sandbox-api.pliq.io/v2/api (Para ambiente de sandbox)

## Requisição HTTP
A API da PliQ utiliza o padrão REST através do protocolo HTTPS. Os métodos variam de acordo com a função utilizada:

Método | Ação
------------ | ------------- 
GET | lista ou consulta dados 
POST | criação de dados 
PUT / PATCH | atualização de dados 
DELETE | remoção de dados 

Dica: quando estiver listando, você pode escolher os campos que deseja trazer enviando o parâmetro "attribute" na URL.

### Como autenticar
É necessário passar o token privado de autenticação para conseguir realizar as operações. Para conseguir esse token, acesse na PliQ a seção Integrações -> Tokens.

### Códigos de respostas

Código | Status | Descrição
------------ | ------------- | -------------
200 | OK | Sua requisição foi bem sucedida
400 | Bad Request | Algum parâmetro obrigatório não foi enviado ou é inválido. Neste caso a própria resposta indicará qual é o problema.
401 | Unauthorized | Não foi enviada Napikey ou ela é inválida. Verifique as credenciais de autenticação da requisição.
404 | Not Found | O endpoint ou o objeto solicitado não existe.
403 | Forbidden | Requisição não autorizada ou uso de parâmetros não permitidos podem gerar este código.
429 | Too Many Requests | Muitas requisições em um determinado período de tempo.
500 | Internal Server Error | Algo deu errado no servidor.

### Padrão de endpoints

```
Para listagem, use GET: /endpoint/
Para inserção, use POST: /endpoint/
```

## Header
A requisição deve conter no Header:

* Content-Type: application/json
* PLIQ_TOKEN: SEU_TOKEN_AQUI

### Seções (endpoints) disponíveis

Segue as seções que você pode acessar pela API

### Visualizar Respostas em Lote
Fornecemos também um método de visualização de respostas em lote por período. Esse método pode ser utilizado com os seguintes parâmetros.

O método será: GET

A URL a ser usada deve ser: __<url_acesso>/surveys/feedbacks__

Parâmetros opicionais de cabeçalho, ?survey_code=&days=&startedat=&finishedat=	
	
O body deve ser preenchido usando o seguinte padrão

Parâmetros header

Parâmetro | Tipo | Obrigatório | Descrição
------------ | ------------- | ------------ | -------------
pliq_token | String | Sim | Chave do token da empresa. Obtida na tela de integrações.
	
Parâmetros de cabeçalho

Parâmetro | Tipo | Obrigatório | Descrição
------------ | ------------- | ------------ | -------------
survey_code | String | Não | Chave da pesquisa. Obtida no método __<url_acesso>/surveys/all__.	
days | String | Não* | Quantidade de dias da resposta com base no dia atual.
startedat | String | Não* | Data de início de respostas.
finishedat | String | Não* | Data de final de respostas.

	
Exemplo de retorno:
```
[
    {
        "id_company": "company_id",
        "full_name": "company_fullname",
        "id_survey": "survey_id",
        "url_survey": "survey_code",
        "type_survey": "type_survey",
        "type_survey_label": "type_survey_label",
        "fk_survey_sample": "type_survey_sample",
        "title": "survey_title",
        "description": "survey_description",
        "id_survey_response": "survey_response_id",
        "participant_key": "participant_key",
        "abandonment": "abandonment",
        "closed_loop": "closes_loop",
        "name": "contact_name",
        "name_key": "contact_name_key",
        "respondedat": "survey_response_data",
        "createdat": "survey_response_created",
        "sendedat": "survey_response_send",
        "tags": "survey_response_tags",
        "referral_share_code": "referral_share_code",
        "nps_value": "nps_value",
        "nps_feedback": "nps_feedback",
	"anonymous": "anonymous",
	"timezone","timezone",
	"responses","[fk_question, value, fk_type_question, answers, data_response]"
    }
]
```
	

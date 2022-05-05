## Webhook

Esse link tem o objetivo de explicar como usar a integração da PliQ via webhook.

**Serão necessários 2 passos.**

1. Ter uma conta contratada na PliQ.
2. Configurar o endereço POST url para recebimento da comunicação.

## Evento

O evento é gerado quando um feedback é processado pela pliq em qualquer pesquisa que a empresa esteja realizando com seus clientes.

Aqui está uma resposta de evento que inclui um exemplo:

##### Retorno

```
{
  "id": 9999999,
  "url_survey": "alsdk9kjlakdflk38afjsdfl",
  "answeredat": "2020-01-01T17:17:42.1630076Z",
  "name": "Treinamento",
  "participant_key": "tech@pliq.io",
  "anonymous": false,
  "answers": [
    {
      "fk_question": 1,
      "value": 9,
      "fk_type_question": 1,
      "answers": null,
      "data_response": "2020-01-01T17:17:38"
    },
    {
      "fk_question": 2,
      "value": "Meu feedback",
      "fk_type_question": 2,
      "answers": null,
      "data_response": "2020-01-01T17:17:41"
    },
    {
      "fk_question": 3,
      "value": [
        "Resolutividade",
        "Simpatia"
      ],
      "answers": null,
      "data_response": "2020-01-01T17:17:50"
    }
  ]
}
```

### Objeto Feedback 

Nome | Tipo | Descrição
------------ | ------------- | ------------
id | number | Chave única referente ao feedback.
url_survey | string | Chave da pesquisa. 
answeredat | string  | Data e hora do recebimento da resposta em UTC.
name | string | Nome de quem respondeu a pesquisa em caso de não ser anônimo.
participant_key | string | Email ou telefone do cliente em caso de não ser anônimo.
anonymous | boolean | Identifica se o feedback da pesquisa foi anônimo.
answers | array | Lista de objetos resposta. 

### Objeto Answer 

Nome | Tipo | Descrição
------------ | ------------- | ------------
fk_question | number | Chave única referente a pergunta.
value | object | Valor da resposta da pergunta.
fk_type_question | number | Chave única referente ao tipo de pergunta.
answers | object | Valor de respostas para QUIZ (em breve).
data_response | string | Data e hora do recebimento da resposta da pergunta em UTC.
  
  

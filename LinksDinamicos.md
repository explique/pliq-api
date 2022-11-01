# pliq - links dinâmicos
https://www.pliq.io

Esse é um repositório para auxílio na API PliQ - Plataforma de Pesquisa e Vendas por indicação.

Colocaremos materiais e webhooks para que a integração seja facilitada.
Nota: Qualquer erro ou sugestão, por favor nos contate.

### URL de acesso

https://app.pliq.io/ (Para clientes ambiente de produção)

ou

https://sandbox.pliq.io/ (Para ambiente de sandbox)


### Instruções para gerar links dinâmicos

Parâmetros opcionais de cabeçalho, ?n=&k=t=

Parâmetros de cabeçalho

Parâmetro | Tipo | Obrigatório | Descrição
------------ | ------------- | ------------ | -------------
n | String | Não | Identifica o nome da pessoa que está respondendo a pesquisa.
k | String | Não | Identifica o email ou telefone da pessoa que está respondnedo a pesquisa.
t | String | Não | Identifica as tags da pessoa que está respondendo a pesquisa.

Exemplo:

### URL de acesso

https://app.pliq.io/survey-response/<token_pesquisa> (Para clientes ambiente de produção)

https://app.pliq.io/survey-response/XXXXX?n=Nome do cliente&k=11967660992&t=PliQ;Empresa;Tecnologia

ou

https://sandbox.pliq.io/survey-response/<tokenpesquisa> (Para ambiente de sandbox)

https://sandbox.pliq.io/survey-response/XXXXX?n=Nome do cliente&k=11967660992&t=PliQ;Empresa;Tecnologia
  
  

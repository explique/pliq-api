## PluginJS

Esse link tem o objetivo de explicar como usar a integração da PliQ via script.

## Exemplo de uma integração via PluginJS funcionando

Para ver o funcionamento de um exemplo clique no link a seguir: https://www.pliq.io/teste-pluginjs/

### Vídeo explicativo

Para ver um vídeo explicando a configuração do plugin em uma página no wordpress clique: https://www.loom.com/share/0de9d903744f409f8c3726417b66fa5d

**Serão necessários 3 passos.**

1. Ter uma conta contratada na PliQ.
2. Criar sua pesquisa que vai ser utilizada nessa integração
3. Configurar a sua plataforma ou sistema para começar a monitorar a experiência do cliente.

### Passo 1
Caso ainda não tenha sua conta acesse: www.pliq.io e entre em contato conosco para a escolha do melhor plano para atender as suas necessidades.

### Passo 2
Com o seu acesso em mãos, basta seguir o passo a passo para a criação de sua pesquisa conforme o link a seguir (link).

### Passo 3
Configuração da plataforma.

Acesse a PliQ, entre na listagem das pesquisas e escolha a opção comunicação.

![alt text](https://pliqdrive.blob.core.windows.net/pliqdrive/Help/pliq-menu-pesquisa.png)

> Imagem01 : Menu de Ações da Pesquisa.

Ao acessar a comunicação escolha a aba Popup, conforme imagem a seguir.
![alt text](https://pliqdrive.blob.core.windows.net/pliqdrive/Help/pliq-comunicacao-popup.png)

> Imagem02 : Detalhes da comunicação, opção Popup.

### Dados importantes para o uso do PluginJS

**Url de exibição** 

Caminho no sistema onde será gerado o gatilho para disparo da pesquisa.

É permitido o uso de código Regex ou link direto.

Exemplo: 

Link direto: https://app.pliq.io/home, 

Código regex: 


**Quantidade de exibições do modal** 

Quantas vezes o modal popup deverá aparecer para o cliente até que ele responda a pesquisa.

Exemplo: 3 vezes

**Tempo para o modal ser exibido** 

Quantos segundos o plugin deverá esperar até que ele apresente o modal para o cliente responder a pesquisa.

Exemplo: 5 segundos

## Script URL

Esse script deve ser colocado dentro de sua página web ou webapp. 

```
<script>
(function (p, l, i, q, j, s) {
     p._pliqStt={ surveyUrl: '<Token da sua pesquisa aqui>', key: '<Id do objeto aqui>'};
     j=l.getElementsByTagName('head')[0];s=l.createElement('script');
     s.async=1;s.src=i+q.split(';')[0];j.appendChild(s);
     s=l.createElement('link');s.rel='stylesheet';s.href=i+q.split(';')[1];j.appendChild(s);
})(window, document, 'https://pliqdrive.blob.core.windows.net/sandbox/App/Plugin/app', '.js;.css');
</script>
```

**surveyUrl** 

É o token que é gerado automaticamente pela PliQ que identifica de forma única cada pesquisa. 


**key** 

É o objeto web dentro de seu sistema web, webapp ou CSM como wordpress. Esse objeto deve conter a informação do email do cliente que normalmente faz login no seu sistema.

## PluginJS V2

Estamos disponibilizando uma nova possibilidade de uso do pluginJS que atualmente é FULLSCREEN, nessa nova versão a pesquisa se apresenta no canto inferior direito da página conforme imagem abaixo.

![image](https://user-images.githubusercontent.com/790876/165365038-47e1bb5b-c606-4d46-8019-5bb63db3d681.png)

Para utilizar essa nova versão você deve mudar o seguinte caminho da URL (https://pliqdrive.blob.core.windows.net/pliqdrive/App/Plugin/v2/app).

```
<script>
(function (p, l, i, q, j, s) {
     p._pliqStt={ surveyUrl: '<Token da sua pesquisa aqui>', key: '<Id do objeto aqui>'};
     j=l.getElementsByTagName('head')[0];s=l.createElement('script');
     s.async=1;s.src=i+q.split(';')[0];j.appendChild(s);
     s=l.createElement('link');s.rel='stylesheet';s.href=i+q.split(';')[1];j.appendChild(s);
})(window, document, 'https://pliqdrive.blob.core.windows.net/pliqdrive/App/Plugin/v2/app', '.js;.css');
</script>
```

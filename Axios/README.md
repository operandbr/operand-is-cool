# Axios

HTTP client baseado em Promise para navegadores e node.js

## Características

- Fazer [XMLHttpRequests](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) a partir do navegador
- Fazer [requisições http](http://nodejs.org/api/http.html) a partir do node.js
- Suporta a API [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- Intercepta request e response
- Transforma dados de request e response
- Cancela requests
- Transformações automáticas para dados JSON
- Suporte client side para proteção contra [XSRF](http://en.wikipedia.org/wiki/Cross-site_request_forgery)

## Suporte a Navegadores

![Chrome](https://raw.github.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png) | ![Firefox](https://raw.github.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png) | ![Safari](https://raw.github.com/alrra/browser-logos/master/src/safari/safari_48x48.png) | ![Opera](https://raw.github.com/alrra/browser-logos/master/src/opera/opera_48x48.png) | ![Edge](https://raw.github.com/alrra/browser-logos/master/src/edge/edge_48x48.png) | ![IE](https://raw.github.com/alrra/browser-logos/master/src/archive/internet-explorer_9-11/internet-explorer_9-11_48x48.png) |
--- | --- | --- | --- | --- | --- |
Latest ✔ | Latest ✔ | Latest ✔ | Latest ✔ | Latest ✔ | 8+ ✔ |

[![Browser Matrix](https://saucelabs.com/open_sauce/build_matrix/axios.svg)](https://saucelabs.com/u/axios)

## Promise

O que é?

Um Promise representa um proxy para um valor que não é necessariamente conhecido quando a promessa é criada. Isso permite a associação de métodos de tratamento para eventos da ação assíncrona num caso eventual de sucesso ou de falha. Isto permite que métodos assíncronos retornem valores como métodos síncronos: ao invés do valor final, o método assíncrono retorna uma promessa ao valor em algum momento no futuro.

## Instalando a Axios

Usando cdn:

```html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

## Examplo

Fazendo um request `GET`

```js
// Fazendo um request para um usuário, passando id na url
axios.get('/user?ID=12345')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
// Ou, alternativamente, o request pode ser feito desta forma:
axios.get('/user', {
    params: {
      ID: 12345
    }
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
// ou em um padrão diferente (e que iremos utilizar)
axios.get('/v1/user/12345')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

Fazendo um request `POST`

```js
axios.post('/user', {
    firstName: 'Fred',
    lastName: 'Flintstone'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

Fazendo múltiplos requests concorrentes

```js
function getUserAccount() {
  return axios.get('/v1/user/12345');
}

function getUserPermissions() {
  return axios.get('/v1/user/12345/permissions');
}

axios.all([getUserAccount(), getUserPermissions()])
  .then(axios.spread(function (acct, perms) {
    // Apenas quando os dois requests completarem
  }));
```

## API axios

Requests podem ser feitos também passando dados para o objeto `axios`.

##### axios(config)

```js
// PUT
axios({
  method: 'put',
  url: '/v1/user/12345',
  data: {
    firstName: 'Barney',
    lastName: 'Rubble'
  }
});
```

```js
// GET
axios({
  method:'get',
  url:'/v1/user/12345',
})
  .then(function(response) {
  console.log(response.data)
});
```

### Request Aliases

Para facilitar, aliases foram criados para todos os métodos de request suportados.

##### axios.get(url[, config])
##### axios.delete(url[, config])
##### axios.options(url[, config])
##### axios.post(url[, data[, config]])
##### axios.put(url[, data[, config]])


### Response


Quando usar `then`, você receberá o `response` da seguinte forma:

```js
axios.get('/user/12345')
  .then(function(response) {
    console.log(response.data);
    console.log(response.status);
    console.log(response.statusText);
    console.log(response.headers);
    console.log(response.config);
  });
```

Quando estiver usando `catch`, ou passando um [callback de rejeição](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then) como segundo parâmetro do `then`, o response estará disponível através do objeto `error`.

## Config Defaults

Você pode definir padrões de configuração que serão aplicados em todas as requisições.

### Global axios defaults

```js
axios.defaults.baseURL = 'https://api.example.com';
axios.defaults.headers.common['Authorization'] = AUTH_TOKEN;
axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
```

Você pode definir quais códigos de status HTTP com a config `validateStatus`.

```js
axios.get('/user/12345', {
  validateStatus: function (status) {
    return status < 500; // Rejeitar apenas se status code maior ou igual a 500
  }
})
```

## Usando formato application/x-www-form-urlencoded

Por padrão, axios serializa objetos JavaScript para `JSON`. Para enviar dados no formato `application/x-www-form-urlencoded` você pode usar as seguintes opções.

### Navegador

Para o navegador você pode utilizar a API [`URLSearchParams`](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) desta forma:

```js
var params = new URLSearchParams();
params.append('param1', 'value1');
params.append('param2', 'value2');
axios.post('/foo', params);
```

## Licença

MIT
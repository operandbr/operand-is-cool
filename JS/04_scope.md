#### Escopo em JS

Escopo é o pacote de variáveis e métodos que você possui acesso em um determinado ponto do seu código. Exemplo:

```javascript
var carType = 'Sedan';
// neste ponto do código você não possui acesso à variável carName, ela está fora de escopo

function myFunction() {
    var carName = 'Volvo';
    // Aqui você possui acesso à variável carName e também possui acesso à variável carType
}
```

[Próximo](https://bitbucket.org/devs-operandbr/operand-is-cool/src/master/JS/05_events.md)
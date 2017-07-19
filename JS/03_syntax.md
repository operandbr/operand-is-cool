### Sintaxe

#### Variáveis e Comentários

Variáveis são definidas utilizando a palavra chave `var`.

```javascript
var a = 1; // Define uma variável de nome a com valor 1
var x, y; // Definição de 2 variáveis em uma única declaração

/*
  Como vocês podem perceber comentários em JS
  seguem o mesmo padrão utilizado no PHP
*/
```

#### Javascript é Case Sensitive

```javascript
var ultimonome, ultimoNome;
ultimoNome = "João";
ultimonome = "Ninguém";
```

Portanto no exemplo acima temos duas variáveis completamente distintas

#### Operadores

* `=` => Atribuição
* `==` => Comparação de igualdade
* `!` => Negação
* `!=` => Comparação de diferença
* `===` => Comparação de igualdade levando em conta o tipo de variável
* `!==` => Comparação de diferença levando em conta o tipo de variável
  * `x = y; //Atribui para x o valor de y`
* `+` => Adição
  * `x = x + y; //Atribui para x o valor de x + y`
* `+=` => Atribuição + soma
  * `x += y; //Atribui para x o valor de x + y`
* `-` => Subtração
* `-=` => `x = x - y`
* `*` => Multiplicação
* `*=` => `x = x * y`
* `/` => Divisão
* `/=` => `x = x / y`
* `%` => Módulo de divisão
  * `10 % 3 === 1`
* `%=` => `x = x % y`
* `++` =>	Incremento (Muito utilizado em laços de repetição)
* `--` =>	Decremento (Muito utilizado em laços de repetição)

#### Concatenação

Para concatenar valores em JS você deve utilizar o operador `+`

```javascript
  x = 'Texto ' + variavel;
```

#### Tipos de Dados

As variáveis em Javascript tem tipos dinâmicos, ou seja o tipo da variável depende do seu conteúdo.

```javascript
var length = 16;                               // Number
var lastName = "Johnson";                      // String
var x = {firstName:"John", lastName:"Doe"};    // Object
var cars = ["Saab", "Volvo", "BMW"];           // Object

x = 10; // Agora x é do tipo Number
```

#### Funções

Funções Javascript são blocos de código feitos para executar uma tarefa específica, exemplo:

```javascript
function multiplica(valor1, valor2) {
    return valor1 * valor2;
}
```

[Próximo](https://bitbucket.org/devs-operandbr/operand-is-cool/src/master/JS/04_scope.md)

### HTML DOM (Document Object Model)

Quando uma página WEB é carregada o browser cria um Objeto de Model deste Documento (DOM).

Com o `DOM`, temos tudo que é necessário para criar páginas Dinâmicas.

* JavaScript pode alterar todos os elementos HTML na página
* JavaScript pode alterar todos os atributos HTML na página
* JavaScript pode alterar todos os estilos CSS na página
* JavaScript pode remover elementos HTML existentes e atributos
* JavaScript pode adicionar novos elementos HTML e atributos
* JavaScript pode reagir à todos os eventos HTML existentes na página
* JavaScript pode criar novos eventos na página

#### A interface de programação do DOM

No `DOM` todos os elementos da página são definidos como `objetos`. A interface de programação são os métodos e propriedades de cada objeto.

Uma `propriedade` é um valor que você pode recuperar ou alterar (como a propriedade `innerHTML`)
Um `método` representa uma ação que você pode realizar com o elemento (como o método `setAttribute`)

```html
<html>
<body>

<p id="demo"></p>
<p id="demo1">Hello DOM</p>

<script>
  document.getElementById("demo").innerHTML = "Hello World!"; // Altera o conteúdo HTML do elemento com o id="demo"
  document.getElementById("demo1").setAttribute('align', 'right'); // Define um novo atributo com o alinhamento à direita para o elemento com id "demo1"
</script>

</body>
</html>
```

#### O Objeto DOM Document

O objeto `document` representa sua página WEB, se você quiser acessar qualquer elemento em uma página HTML, você sempre irá começar acessando ele.

##### Encontrando Elementos HTML

* `document.getElementById(id)`	Encontra um elemento através do id
* `document.getElementsByTagName(name)`	Encontra elementos pela sua tag (p, span, div, etc...)
* `document.getElementsByClassName(name)`	Encontra elementos pela sua classe
* `document.querySelector(query)` Encontra UM elemento através de uma query que o represente.
  * `document.querySelector('.myClass') // Encontra o elemento com a classe myClass`
* `document.querySelectorAll(query)` Encontra TODOS elementos através de uma query que os representem.
  * `document.querySelector('.myClass') // Encontra todos elementos com a classe myClass`
  
##### Alterando Elementos HTML

Em primeiro lugar você precisa recuperar o objeto que representa o elemento que você deseja alterar, em seguida você poderá utilizar seus métodos e propriedades para alterá-lo como desejar.

```javascript
var element = document.getElementById('myElement');

element.innerHTML = 'new html content'; //Muda o conteúdo HTML do elemento
element.attribute = 'new value'; //Muda o valor de um atributo
element.setAttribute('attribute', 'value'); //Cria um novo atributo 
element.style.property = 'new style'; //Altera uma propriedade de CSS inline do elemento
```

[Próximo](https://github.com/operandbr/operand-is-cool/blob/master/Bootstrap/README.md)

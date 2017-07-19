# Vue.js / Componentes Web

  Tags customizadas contendo css, js e html próprios, de escopo próprio.

```html
<div id="carousel-example-generic" class="carousel slide" data-ride="carousel">
    <!-- Indicators -->
    <ol class="carousel-indicators">
        <li data-target="#carousel-example-generic" data-slide-to="0" class="active"></li>
        <li data-target="#carousel-example-generic" data-slide-to="1"></li>
        <li data-target="#carousel-example-generic" data-slide-to="2"></li>
    </ol>

    <!-- Wrapper for slides -->
    <div class="carousel-inner">
        <div class="item active">
            <img src="..." alt="...">
            <div class="carousel-caption">
            ...
          </div>
        </div>
        ...
    </div>

    <!-- Controls -->
    <a class="left carousel-control" href="#carousel-example-generic" data-slide="prev">
        <span class="glyphicon glyphicon-chevron-left"></span>
    </a>
    <a class="right carousel-control" href="#carousel-example-generic" data-slide="next">
        <span class="glyphicon glyphicon-chevron-right"></span>
    </a>
</div>
```
Utilizando Web Components será convertido em:
```html
<img-slider>
    <img src="./image1.jpg" alt="a dramatic sunset">
    <img src="./image2.jpg" alt="a rock arch">
    <img src="./image3.jpg" alt="some neat grooves">
    <img src="./image4.jpg" alt="an interesting rock">
</img-slider>
```

# DOM/Virtual-DOM

Criado pelo W3C, O DOM é uma multi-plataforma que representa como as marcações em HTML, XHTML e XML são organizadas e lidas pelo navegador que você usa. Uma vez indexadas, estas marcações se transformam em elementos de uma árvore que você pode manipular via API – que é o que fazemos quando usamos programas ou scripts para alterar funcionalidades de uma página: conteudo, estrutura ou folha de estilo.

```js
document.getElementById('myId').appendChild(myNewNode);
```

![](http://tableless.com.br/uploads/2011/07/dom_tree.gif)

Por que o DOM é lento ?

Quando uma alteração é feita no DOM, o navegador precisa fazer a leitura completa do DOM novamente para redesenhar (com direito a todos os passos, css, render, etc) o layout e refletir as alterações em tela. JQuery, Angular e outras libs manipulam o DOM, tornando todas as libs dependentes extremamente lentas, acumulando alterações e redesenho de telas.

Virtual DOM para o resgate

Virtual DOM é uma abstração do DOM, deixado em memória (JS), deixando a coisa toda mais rápida, por saber o diff entre o que está sendo alterado e então manipulando o DOM de forma otimizada só quando extremamente necessário e com cuidado, evitando utilizar métodos que disparam o redesenho da tela tornando o processo todo mais eficiente.

# Vue.js

É uma biblioteca que auxilia a criar componentes reativos com virtual dom (a partir da versão 2.0), possui comunidades fortes e dedicadas além de libs auxiliares. Vue.js é extremamente livre na sintaxe, porém ele possui um estilo de desenvolvimento mais intuitivo e organizado. É muito fácil ler um código feito com ele, os componentes são criados com objetos de configuração, sendo fácil identificar o que são eventos, ações, propriedades…

```html
<div id="demo">
    <p>{{ message }}</p>
    <input v-model="message">
</div>
```
```js
var demo = new Vue({
    el: '#demo',
    data: {
        message : 'Hello Vue.js!'
    }
})
```

Outra grande diferença é como o "html" do componente é feito. Vue.js pode ser escrito 100% em javascript puro, porém ele disponibiliza ferramentas que ampliam e melhoram o seu workflow. Vue.js possui um recurso chamado Single File Components.

my-component.vue
```html
<template>
    <div class="my-component">
        <h2>{{msg}}</h2>
    </div>
</template>
<script>
module.exports = {
    data: function () {
        return {
            msg: 'Hello'
        }
    }
}
</script>
<style>
.my-component h2 {
    color: red;
}
</style>
```

Este é um component Vue.js, tendo tudo empacotado em um arquivo apenas e para utilizá-lo (passando propriedades ou não) basta:

```html
<my-component prop1="value" prop2="value2" />
```

# Outros Exemplos

[https://br.vuejs.org/v2/examples/](https://br.vuejs.org/v2/examples/)

# Vue.js na prática

Agora vamos ver na prática como podemos trabalhar com o Vue.js (instalar Vue Devtools)

 1º Passo - inserir o Vue.js

```html
<!DOCTYPE html>
<html>
<head>
    <title>Primeiro Teste Vue.js</title>
</head>
<body>
    <div id="app">
    </div>
</body>
<script src="https://unpkg.com/vue/dist/vue.js" ></script>
<script type="text/javascript">
    new Vue({
        el : '#app',
    });
</script>
</html>
```
 2º Passo - Criar uma variável two-way databind/reativa dentro da div "app".

```html
<!DOCTYPE html>
<html>
<head>
    <title>Primeiro Teste Vue.js</title>
</head>
<body>
    <div id="app">
        <span v-bind:title="mensagem">
        {{ mensagem }}
        </span>
    </div>
</body>
<script src="https://unpkg.com/vue/dist/vue.js" ></script>
<script type="text/javascript">
    var app = new Vue({
        el : '#app',
        data : {
            mensagem: 'Hello World',
        },
        created: function() {
            console.log('Instância Vue.js criada!');
        }
    });
</script>
</html>
```

# Fluxo de vida de componentes Vue.js

- beforeCreate
O gancho beforeCreate roda a cada inicialização do componente. Dados ainda não foram setados como reativos e os eventos ainda não estão ativos.
- created
No gancho created, dados já estão reativos e os eventos também. Templates e Virtual DOM ainda não foram criados ou montados.
- beforeMount
O gancho beforeMount roda logo antres do render inicial acontecer.
- mounted
No gancho mounted você possui total acesso ao component reativo, templates e DOM renderizado (via. this.$el). Mounted é o gancho mais utilizado, frequentemente é onde se fazem as chamadads de dados para alimentar o componente e modificar o DOM. Também é onde se integra com libs não Vue.js.
- beforeUpdate
O gancho beforeUpdate roda quando a informação muda no componente e o ciclo de update é iniciado, pouco antes de ser feito p patch do DOM e ele ser renderizado novamente.
- updated
O gancho updated roda depois da informação do componente mudar e o DOM já foi renderizado neste ponto.
- beforeDestroy
beforeDestroy é executado logo antes da destruição do componente. O componente ainda est´á presente e totalmente funcional. Este é o ponto de executar cleanups ou de disparar eventos reativos à destruição do componente.
- destroyed
Neste ponto o componente não existe mais, não é mais reativo e seus eventos não existem mais. Este é outro ponto para efetuar limpezas que não necessitam de dados do componente.

![](https://vuejs.org/images/lifecycle.png)

# Diretivas Vue

São os "v-algumacoisa" declarativos que são colocados no meio do código html.
Alguns atalhos para as diretivas v-on e v-bind (muito utilizadas).

```html
<a v-bind:href="minhaURL"></a>
<a :href="minhaURL"></a>

<a v-on:click="minhaFuncao"></a>
<a @click=" minhaFuncao "></a>

<input v-model="message">
```

Exemplo com diretivas

```html
<!DOCTYPE html>
<html>
<head>
    <title>Primeiro Teste Vue.js</title>
</head>
<body>
    <div id="app">
        <span v-bind:title="mensagem" v-if="isVisible">
        {{ mensagem }}
        </span>
        <span v-else>
        Outra mensagem
        </span>
    </div>
</body>
<script src="https://unpkg.com/vue/dist/vue.js" ></script>
<script type="text/javascript">
    var app = new Vue({
        el : '#app',
        data : {
            mensagem: 'Hello World',
            isVisible: false
        },
        created: function() {
            console.log('Instância Vue.js criada!');
        }
    });
</script>
</html>
```

Exemplo 2 com diretivas v-for (loop)

```html
<!DOCTYPE html>
<html>
<head>
    <title>Primeiro Teste Vue.js</title>
</head>
<body>
    <div id="app">
        <span v-bind:title="mensagem" v-if="isVisible">
        {{ mensagem }}
        </span>
        <span v-else>
        Outra mensagem
        </span>
        <ol>
            <li v-for="item in listaDeItens">
                {{ item.nome }}
            </li>
        </ol>
    </div>
</body>
<script src="https://unpkg.com/vue/dist/vue.js" ></script>
<script type="text/javascript">
    var app = new Vue({
        el : '#app',
        data : {
            mensagem: 'Hello World',
            isVisible: false,
            listaDeItens: [
                { nome: 'Aprenda JavaScript' },
                { nome: 'Aprenda Vue' },
                { nome: 'Construa algo impressionante' }
            ]
        },
        created: function() {
            console.log('Instância Vue.js criada!');
        }
    });
</script>
</html>
```
Exemplo 3 com diretivas de classe e v-model

```html
<!DOCTYPE html>
<html>
<head>
    <title>Primeiro Teste Vue.js</title>
</head>
<body>
    <div id="app">
        <span v-bind:title="mensagem" v-if="isVisible">
        {{ mensagem }}
        </span>
        <span v-else>
        Outra mensagem
        </span>
        <ol>
            <li v-for="item in listaDeItens">
                {{ item.nome }}
            </li>
        </ol>
        <input v-model="mensagem">
    </div>
</body>
<script src="https://unpkg.com/vue/dist/vue.js" ></script>
<script type="text/javascript">
    var app = new Vue({
        el : '#app',
        data : {
            mensagem: 'Hello World',
            isVisible: false,
            listaDeItens: [
                { nome: 'Aprenda JavaScript' },
                { nome: 'Aprenda Vue' },
                { nome: 'Construa algo impressionante' }
            ]
        },
        created: function() {
            console.log('Instância Vue.js criada!');
        }
    });
</script>
</html>
```

# Propriedades computadas e observadores

Propriedades computadas são funções que podem ser feito o bind e retornam sempre aquela informação "computada". As propriedades computadas são cacheadas enquanto as de métodos não.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Primeiro Teste Vue.js</title>
</head>
<body>
    <div id="app">
        <span v-bind:title="mensagem" v-if="isVisible">
        {{ mensagem }}
        </span>
        <span v-else>
        Outra mensagem
        </span>
    </div>
</body>
<script src="https://unpkg.com/vue/dist/vue.js" ></script>
<script type="text/javascript">
    var app = new Vue({
        el : '#app',
        data : {
            mensagem: 'Hello World',
            isVisible: false
        },
        created: function() {
            console.log('Instância Vue.js criada!');
        },
        computed: {
            mensagemModificada: function () {
                return this.mensagem.toUpperCase().substring(1, 3);
            }
        },
    });
</script>
</html>
```
Observadores são estruturas que permitem o monitoramento de mudança de valor de propriedades, podendo executar callbacks. É recomendado o uso quando é feito chamadas assíncronas, então os callbacks podem ser chamados quando a propriedade é "alterada".

Exemplo completo
```html
<!DOCTYPE html>
<html>
<head>
    <title>Primeiro Teste Vue.js</title>
</head>
<body>
    <div id="app">
        <span v-bind:title="mensagem" v-if="isVisible">
        {{ mensagem }}
        </span>
        <span v-else>
        Outra mensagem
        </span>
        <p>Mensagem modificada: "{{ mensagemModificada }}"</p>
    </div>
</body>
<script src="https://unpkg.com/vue/dist/vue.js" ></script>
<script type="text/javascript">
    var app = new Vue({
        el : '#app',
        data : {
            mensagem: 'Hello World',
            isVisible: false
        },
        created: function() {
            console.log('Instância Vue.js criada!');
        },
        computed: {
            mensagemModificada: function () {
                return this.mensagem.toUpperCase().substring(1, 3);
            }
        },
        watch : {
            mensagem: function () {
                console.log('alterou o texto');
            }
        },
    });
</script>
</html>
```

# Filtros

São métodos de modificação de dados (conversão de casas, conversão de formatos de data, etc).

```html
<!DOCTYPE html>
<html>
<head>
    <title>Primeiro Teste Vue.js</title>
</head>
<body>
    <style type="text/css">
        .sucesso {
            color: green;
        }
        .erro {
            color: red;
        }
    </style>
    <div id="app">
        <span v-bind:title="mensagem" v-if="isVisible">
        {{ mensagem }}
        </span>
        <span v-else>
        Outra mensagem
        </span>
        <p>Exemplo com classes</p>
        <span v-bind:title="contador" :class="{'sucesso': contador > 0, 'erro' : contador <= 0 }">
        {{ contador }}
        </span>
        <p>Mensagem modificada: "{{ mensagemModificada }}"</p>
        <p>Mensagem com filtro UPPER aplicado: "{{ mensagem | upper }}"</p>
        <p>Mensagem com filtro UPPER e REVERSE aplicado: "{{ mensagem | upper | reverse }}"</p>
        <p>Mensagem com filtro UPPER e CUT (com params 2,6) aplicado: "{{ mensagem | upper | cut(2,6) }}"</p>
        <p>Mensagem com JS split, reverse e join aplicados: "{{ mensagem.split('').reverse().join('') }}"</p>
        <!-- Javascript split('') vai criar um array com cada letra -->
        <!-- Javascript reverse() vai inverter os itens do array -->
        <!-- Javascript join('') vai juntar os itens do array e criar uma string -->
    </div>
</body>
<script src="https://unpkg.com/vue/dist/vue.js" ></script>
<script type="text/javascript">
    // precisa ser colocado antes da instânciação do objeto Vue sendo assim global
    //Vue.filter('upper', function (text) {
    //    return text.toUpperCase();
    //});
    var app = new Vue({
        el : '#app',
        data : {
            mensagem: 'Hello World',
            isVisible: false,
            contador: 0,
        },
        created: function() {
            console.log('Instância Vue.js criada!');
        },
        computed: {
            mensagemModificada: function () {
                return this.mensagem.toUpperCase().substring(1, 3);
            }
        },
        watch : {
            mensagem: function () {
                console.log('alterou o texto');
            }
        },
        filters: {
            upper: function(text) {
                return text.toUpperCase();
            },
            reverse : function (text) {
                return text.split('').reverse().join('');
            },
            cut : function (text, index1, index2) {
                // primeiro parâmetro sempre será o input do filtro
                return text.substring(index1, index2);
            }
        }
    });
</script>
</html>
```

# Formulários

```html
<!DOCTYPE html>
    <html>
    <head>
        <title>Primeiro Teste Vue.js</title>
    </head>
    <body>
        <div id="app">
            <!-- retorna string<input type="text" name="number" v-model="number">
            {{number}} -->
            <!-- retorna number -->
            <input type="text" name="number" v-model.number="number">
            {{number}}
            <br /><br />
            <input type="checkbox" name="myCheck" v-model="myCheck" value="A">
            <input type="checkbox" name="myCheck" v-model="myCheck" value="B">
            <input type="checkbox" name="myCheck" v-model="myCheck" value="C">
            {{myCheck}}
            <br /><br />
            <input type="checkbox" name="myCheck2" v-model="myCheck2" v-bind:true-value="'A'" v-bind:false-value="'B'">
            {{myCheck2}}
            <br /><br />
            <input type="radio" name="myCheck3" v-model="myCheck3" value="A">
            <input type="radio" name="myCheck3" v-model="myCheck3" value="B">
            <input type="radio" name="myCheck3" v-model="myCheck3" value="C">
            {{myCheck3}}
            <br /><br />
            <!-- <select v-model="mySelect">
                <option>A</option>
                <option>B</option>
                <option>C</option>
            </select>
            {{mySelect}} -->
            <select v-model="mySelect" multiple>
                <option v-bind:value="1">A</option>
                <option v-bind:value="2">B</option>
                <option v-bind:value="3">C</option>
            </select>
            {{mySelect}}
        </div>
    </body>
    <script src="https://unpkg.com/vue/dist/vue.js" ></script>
    <script type="text/javascript">
        // app é o ViewModel
        var app = new Vue({
            el : '#app',
            data : {
                number: 0,
                myCheck : [],
                myCheck2 : false,
                myCheck3 : '',
                mySelect : [],
            },
        });
    </script>
    </html>
```

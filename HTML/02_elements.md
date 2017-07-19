### Elementos HTML

Como já foi comentado anteriormente elementos normalmente são formados por uma tag de abertura, conteúdo e tag de fechamento.

```html
<nome-da-tag>O conteúdo vai aqui...</nome-da-tag>
```

#### Elementos aninhados

Todas os documentos HTML consistem basicamente de elementos aninhados, sendo `<html>` o elemento raiz. Porém a ordem das tags de abertura deve ser respeitada sempre, caso contrário o navegador pode não interpretar corretamente o código.

**Uma dica é sempre escrever ambas as tags de abertura e de fechamento e somente em seguida escrever seu conteúdo.**

Exemplo:

```html
<div>
  <p>
    Quisque velit nisi, pretium ut lacinia in, elementum id enim. Mauris blandit aliquet elit, eget tincidunt nibh pulvinar a.
  <p>
  <hr>
  <p>
    Pellentesque in ipsum id orci porta dapibus. Nulla porttitor accumsan tincidunt.
  <p>
</div>
```

#### Elementos mais utilizados

* `<div>` Definem uma divisão ou seção em um documento
* `<span>` Usado para agrupar / estilizar elementos `inline` em um documento
* `<a>` Usado para criação de links
* `<b> ou <strong>` Deixa o texto em negrito
* `<br>` Quebra de linha
* `<button>` Cria um botão
* `<form>` Tag de Formulário, define propriedades como a `url` à qual o formulário será submetido.
* `<input>` Permite ao usuário inserir dados na sua página / aplicação e pode possuir alguns tipos. Abaixo alguns dos mais comuns:
    * text
    * radio
    * checkbox
    * file
    * submit
    * date (HTML5)
    * email (HTML5)
* `<select>` Utilizado para criar uma listagem do tipo `drop-down`, pode ser de múltipla seleção ou simples.
    * `<option>` tag filha do `<select>` que define uma opção da lista
    * `<optgroup>` tag filha do `<select>` que cria um grupo de opções com uma ou mais tags `<option>` dentro dela 
* `<h1> - <h6>` Utilizado para criar Títulos em uma página sendo `<h1>` o de maior relevância.
* `<img>` Utilizada para inserir imagens
* `<ul> e <ol>` Cria listas *Não ordenadas* e *Ordenadas* respectivamente
  * `<li>` Define um item da lista
* `<table>` Cria uma tabela
  * `<thead>` Cabeçalho da tabela
    * `<tr>` Linha da tabela
      * `<th>` Célula de cabeçalho
  * `<tbody>` Corpo da Tabela
    * `<tr>` Linha da tabela
      * `<td>` Célula de Conteúdo
  * `<tfoot>` Rodapé da Tabela
    * `<tr>` Linha da tabela
      * `<td>` Célula de Conteúdo
      
#### Atributos de Elementos

* Todos elementos podem possuir atributos.
* Atributos fornecem informações adicionais aos elementos.
* Atributos *SEMPRE* são especificados na `tag` de *ABERTURA*!
* Atributos normalmente seguem o padrão `nome-do-atributo="valorDoAtributo"`

Existem atributos opcionais que fornecem informações adicionais ao elemento, e em alguns casos o elemento sozinho não faz sentido se não possuir atributos, como exemplo podemos citar a `tag` `<img>`.

```html
  <img src="/images/operand-is-cool.png" height="100" width="50">
```

[Próximo](https://github.com/operandbr/operand-is-cool/blob/master/HTML/03_styling.md)

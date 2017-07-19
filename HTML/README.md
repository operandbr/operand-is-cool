### O que é HTML?

HTML (Hyper Text Markup Language) é uma linguagem de marcação para criação de páginas WEB.
O HTML descreve a estrutura das páginas WEB utilizando marcações `tags`. Os navegadores utilizam estas **tags** para renderizar o conteúdo das páginas WEB.

### Tags HTML

As tags são os nomes dos elementos que serão renderizados em tela, exemplo:

```html
<nome-da-tag>O conteúdo vai aqui...</nome-da-tag>
```
* Tags HTML na maioria dos casos são escritas em pares como no exemplo acima
  * Em alguns casos elas não possuem tag de fechamento como nestes exemplos:
    * `<br>`
    * `<hr>`
    * `<img>`

### Um documento HTML Simples

```html
<!DOCTYPE html>
<html>
<head>
    <title>Olá Mundo</title>
</head>
<body>
    <h1>Olá Mundo</h1>
</body>
</html>
```

##### Explicação do Exemplo

1. `<!DOCTYPE html>` define que este documento utiliza HTML5
2. `<html>` elemento raiz de uma página HTML, todos as demais **tags** serão filhas desta.
3. `<head>` Cabeçalho do documento, aqui vão informações sobre a página que será carregada e também seus estilos.
3. `<title>` Especifica um título para a página
4. `<body>` Contém todo conteúdo visível ao usuário final
5. `<h1>` Tag de título

[Próximo](https://bitbucket.org/devs-operandbr/operand-is-cool/src/master/HTML/02_elements.md)
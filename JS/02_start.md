#### Por onde começar

##### Tag `<script>`
A tag `script` nos permite inserir código Javascript em nossas aplicações WEB. Você pode escrever o código dentro da tag ou carregar seu conteúdo a partir de um arquivo `.js` externo.

###### Javascript escrito dentro da tag
```html
<script>
  document.getElementById("demo").innerHTML = "My First JavaScript";
</script>
```

###### Javascript de arquivo externo
```html
<script src="caminho/para/meu/arquivo.js"></script>
```

##### Vantagens do arquivo externo

* Separa o HTML da lógica da aplicação
* Torna o HTML e o Javascript mais fáceis de ler e de dar manutenção.
* Pode ser carregado (reutilizado) em diferentes páginas
* Arquivos JS em cache podem acelerar o carregamento das páginas.

[Próximo](https://bitbucket.org/devs-operandbr/operand-is-cool/src/master/JS/03_syntax.md)
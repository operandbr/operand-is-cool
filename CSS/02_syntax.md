### Sintaxe

Uma regra de CSS consiste basicamente de um seletor e um bloco de declaração.

#### Seletores
Os seletores são usados para encontrar os elementos aos quais você deseja aplicar regras de *CSS*. Os seletores podem ser o nome do elemento, id, classe, atributos entre outros.

Aqui você pode encontrar uma lista deles com exemplos [https://www.w3schools.com/cssref/css_selectors.asp](https://www.w3schools.com/cssref/css_selectors.asp)


```css
h1 {
  color: blue;
  font-size: 16px;
}
```

No exemplo acima `h1` é o seletor (que irá selecionar todos os elementos `h1` na página) e o código entre `{}` é o bloco de regras que serão aplicadas à ele.
O bloco de regras segue o padrão `propriedade: valor;`

###### Seletor ID

```css
#texto {
    text-align: center;
    color: red;
}
```

Neste exemplo será selecionado o elemento com o atributo `id="texto"`. Lembrando que o `id` deve ser **ÚNICO** em uma página web, se o elemento for se repetir deve ser usada uma classe.

###### Seletor classe

```css
.texto {
    text-align: center;
    color: red;
}
```

Neste exemplo serão selecionados todos os elementos que contenham a classe `texto`. Um elemento pode possuir mais de uma classe.

#### Agrupando seletores

Se você possuir elementos que possuem as mesmas definições de estilo você poderá agrupálos utilizando uma `,` então o código abaixo:

```css
h1 {
    text-align: center;
    color: red;
}

h2 {
    text-align: center;
    color: red;
}

p {
    text-align: center;
    color: red;
}
```

se tornaria este: 
```css
h1, h2, p {
    text-align: center;
    color: red;
}
```

#### Comentários

Comentários também podem ser utilizados em arquivos *CSS* para documentar o código. 

Os comentários serão ignorados pelo browser.

Eles começam sempre com `/*` e terminam com `*/`, podendo ser de uma única linha ou multi-linhas. exemplo:

```css
p {
    color: red;
    /* Comentário de linha única */
    text-align: center;
}

/* Comentário
de
múltiplas
linhas */
```

[Próximo](https://bitbucket.org/devs-operandbr/operand-is-cool/src/master/CSS/03_properties.md)
# Estruturas de repetição

### while

```php
<?php

$contador = 0;

while ($contador < 10) {
    echo $contador . '<br>';
    $contador++;
}

/*
0
1
2
3
4
5
6
7
8
9
*/

```

### do ... while

```php
<?php

$contador = 0;

do {
    echo $contador . '<br>';
    $contador++;
} while ($contador < 10);

/*
0
1
2
3
4
5
6
7
8
9
*/

```

### for

```php
<?php

for ($contador = 0; $contador < 10; $contador++) {
    echo $contador . '<br>';
}

/*
0
1
2
3
4
5
6
7
8
9
*/

```

### foreach

```php
<?php

$usuarios = [
    'Marvin',
    'Trillian',
    'Arthur',
];

foreach ($usuarios as $usuario) {
    echo $usuario . '<br>';
}

/*
Marvin
Trillian
Arthur
*/

// ou

foreach ($usuarios as $indice => $usuario) {
    echo $indice . ': ' . $usuario . '<br>';
}

/*
0: Marvin
1: Trillian
2: Arthur
*/

```

[<< Anterior (estruturas condicionais)](https://github.com/operandbr/operand-is-cool/blob/master/PHP-basico/EstruturasCondicionais.md)
|
[Próximo (funções) >>](https://github.com/operandbr/operand-is-cool/blob/master/PHP-basico/Funcoes.md)

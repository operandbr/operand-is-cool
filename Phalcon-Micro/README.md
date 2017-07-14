# Micro Applications

[Menu principal](https://github.com/operandbr/operand-is-cool/blob/master/README.md#conteúdo-proposto)

Como o Phalcon você pode criar aplicações "Micro". Fazendo isto, você só precisa escrever um mínimo de código fonte para criar uma aplicação PHP.

Micro aplicações são ideais para implementar API's e protótipos de forma prática e rápida.

```php
<?php
$app = new Phalcon\Mvc\Micro();

$app->get('/say/welcome/{name}', function ($name) {
    echo "<h1>Welcome $name!</h1>";
});

$app->handle();

```

# Criando uma Micro Aplicação

Phalcon\Mvc\Micro é a classe responsável por implementar uma micro aplicação.

```php
<?php
$app = new Phalcon\Mvc\Micro();
```

# Definindo rotas

Após instanciar o objeto, você irá precisar adicionar algumas rotas. Phalcon\Mvc\Router faz o gerenciamento das rotas internamente. Rotas precisam iniciar com uma "/". Um método HTTP ´é requirido quando definir uma rota, para instruir o router para identificar apenas a rota ao m´étodo HTTP correto. Abaixo um exemplo de método GET:

```php
<?php
$app->get('/diga/ola/{nome}', function ($nome) {
    echo "<h1>Olá! $nome</h1>";
});
```

A rota /diga/ola/{nome} também contém um parâmetro {$nome} que é repassado diretamente à função anônima que executará o código referente a esta rota. A rota poderá executar qualquer tipo de método "chamável" do PHP. Alguns exemplos abaixo:

```php
<?php
// Com uma função
function diga_ola($nome) {
    echo "<h1>Olá! $nome</h1>";
}

$app->get('/diga/ola/{nome}', "diga_ola");

// Com um método estático
$app->get('/diga/ola/{nome}', "AlgumaClasse::digaOla");

// Com um método em um controller
$meuController = new MeuController();
$app->get('/diga/ola/{nome}', array($MeuController, "digaOlaAction"));

// Função anônima
$app->get('/diga/ola/{nome}', function ($nome) {
    echo "<h1>Olá! $nome</h1>";
});
```

# Trabalhando com  Responses

Você é livre para retornar os dados de qualquer forma, xml, ascii, hexa, binário, uma view html completa ou no formato mais aceitado hoje para API's, o JSON.

```php
<?php
//Output direto
$app->get('/diga/ola', function () {
    echo "<h1>Olá!</h1>";
});

//Dando require de outro arquivo
$app->get('/mostrar/resultados', function () {
    require 'views/resultados.php';
});

//Retornando um JSON
$app->get('/get/json', function () {
    echo json_encode(array("uma", "informação", "importante"));
});

```

Em adição à isto, você pode fazer uso de um serviço de reponses, onde você poderá melhor manipular a resposta.

```php
<?php
$app->get('/show/data', function () use ($app) {

    //Setar o Content-Type do header
    $app->response->setContentType('text/plain')->sendHeaders();

    //Printar o conteúdo de um arquivo
    readfile("data.txt");

});
```

Ou criar um objeto response e retorná-lo:

```php
<?php
$app->get('/mostrar/dados', function () {

    //Cria um response
    $response = new Phalcon\Http\Response();

    //Seta o Content-Type do header
    $response->setContentType('text/plain');

    //Passa o conteúdo de um arquivo pro response
    $response->setContent(file_get_contents("data.txt"));

    //Retorna o response
    return $response;
});
```

# Interagindo com o Injetor de Dependencia

Nas micro aplicações, um container para o serviço Phalcon\DI\FactoryDefault é criado implicitamente; mas você pode criar um fora da aplicação e manipular os seus serviços:

```php
<?php
use Phalcon\DI\FactoryDefault,
    Phalcon\Mvc\Micro,
    Phalcon\Config\Adapter\Ini as IniConfig;

$di = new FactoryDefault();

$di->set('config', function() {
    return new IniConfig("config.ini");
});

$app = new Micro();

$app->setDI($di);

$app->get('/', function () use ($app) {
    //Lê uma configuração do arquivo config.ini
    echo $app->config->nome_aplicacao;
});

$app->post('/contato', function () use ($app) {
    $app->flash->success('Sim, foi feito o contato!');
});
```

A sintaxe de array é possível (e bem utilizada) para dar set/get dos serviços no container:

```php
<?php
use Phalcon\Mvc\Micro,
    Phalcon\Db\Adapter\Pdo\Mysql as MysqlAdapter;

$app = new Micro();

//Setup do serviço de conexão com o banco
$app['db'] = function() {
    return new MysqlAdapter(array(
        "host" => "localhost",
        "username" => "root",
        "password" => "123456",
        "dbname" => "operand_iscool"
    ));
};

$app->get('/blog', function () use ($app) {
    $noticias = $app['db']->query('SELECT * FROM noticias');
    foreach ($noticias as $noticia) {
        echo $new->titulo;
    }
});
```

# Rota não encontrada (404)

Quando um usuário tentar executar uma rota que não é encontrada, a micro aplicação por padrão tentará executar o handler "Not-Found" conforme abaixo (sempre adicione este handler):

```php
<?php
$app->notFound(function () use ($app) {
    $app->response->setStatusCode(404, "Not Found")->sendHeaders();
    echo 'This is crazy, but this page was not found!';
});
```

# Criando uma API REST básica utilizando Phalcon Micro

Utilizando Phalcon Micro, Injetor de Depenências, Banco de Dados e manipulação de responses

```php
<?php

$di = new \Phalcon\DI\FactoryDefault();

$di->set('db', function(){
    return new \Phalcon\Db\Adapter\Pdo\Mysql(array(
        "host" => "mariadb",
        "username" => "root",
        "password" => "123456",
        "dbname" => "operand_iscool"
    ));
});

$app = new \Phalcon\Mvc\Micro($di);

//Retrieves all bank accounts
$app->get('/v1/bankaccounts', function() use ($app) {

    $sql = "SELECT id,name,balance FROM bank_account ORDER BY name";
    $result = $app->db->query($sql);
    $result->setFetchMode(Phalcon\Db::FETCH_OBJ);
    $data = array();
    while ($bankAccount = $result->fetch()) {
        $data[] = array(
            'id' => $bankAccount->id,
            'name' => $bankAccount->name,
            'balance' => $bankAccount->balance,
        );
    }

    $response = new Phalcon\Http\Response();

    if ($data == false) {
        $response->setStatusCode(404, "Not Found");
        $response->setJsonContent(array('status' => 'NOT-FOUND'));
    } else {
        $response->setJsonContent(array(
            'status' => 'FOUND',
            'data' => $data
        ));
    }

    return $response;

});

//Adds a new bank account
$app->post('/v1/bankaccounts', function() use ($app) {

    $bankAccount = $app->request->getPost();
    $response = new Phalcon\Http\Response();

    try {
        $result = $app->db->insert("bank_account",
            array($bankAccount['name'], $bankAccount['balance']),
            array("name", "balance")
        );

        $response->setStatusCode(201, "Created");
        $bankAccount['id'] = $app->db->lastInsertId();
        $response->setJsonContent(array('status' => 'OK', 'data' => $bankAccount));

    } catch (Exception $e) {
        $response->setStatusCode(409, "Conflict");
        $errors[] = $e->getMessage();
        $response->setJsonContent(array('status' => 'ERROR', 'messages' => $errors));
    }

    return $response;

});

//Updates bank account based on primary key
$app->put('/v1/bankaccounts/{id:[0-9]+}', function($id) use ($app) {

    $bankAccount = $app->request->getPut();
    $response = new Phalcon\Http\Response();

    try {
        $result = $app->db->update("bank_account",
            array("name", "balance"),
            array($bankAccount['name'], $bankAccount['balance']),
            "id = $id"
        );

        $response->setJsonContent(array('status' => 'OK'));

    } catch (Exception $e) {
        $response->setStatusCode(409, "Conflict");
        $errors[] = $e->getMessage();
        $response->setJsonContent(array('status' => 'ERROR', 'messages' => $errors));
    }

    return $response;

});

//Deletes bank account based on primary key
$app->delete('/v1/bankaccounts/{id:[0-9]+}', function($id) use ($app) {
    $response = new Phalcon\Http\Response();

    try {
        $result = $app->db->delete("bank_account",
            "id = $id"
        );

        $response->setJsonContent(array('status' => 'OK'));

    } catch (Exception $e) {
        $response->setStatusCode(409, "Conflict");
        $errors[] = $e->getMessage();
        $response->setJsonContent(array('status' => 'ERROR', 'messages' => $errors));
    }

    return $response;
});

//Retrieves bank account based on primary key
$app->get('/v1/bankaccounts/search/{id:[0-9]+}', function($id) use ($app) {

    $sql = "SELECT id,name,balance FROM bank_account WHERE id = ?";
    $result = $app->db->query($sql, array($id));
    $result->setFetchMode(Phalcon\Db::FETCH_OBJ);
    $data = array();
    $bankAccount = $result->fetch();

    $response = new Phalcon\Http\Response();

    if ($bankAccount == false) {
        $response->setStatusCode(404, "Not Found");
        $response->setJsonContent(array('status' => 'NOT-FOUND'));
    } else {
        $response->setJsonContent(array(
                'id' => $bankAccount->id,
                'name' => $bankAccount->name,
                'balance' => $bankAccount->balance,
        ));
    }

    return $response;

});

//Searches for bank account with $name in their name
$app->get('/v1/bankaccounts/search/{name}', function($name) use ($app) {

    $sql = "SELECT id,name,balance FROM bank_account WHERE name LIKE ? ORDER BY name";
    $result = $app->db->query($sql, array("%".$name."%"));
    $result->setFetchMode(Phalcon\Db::FETCH_OBJ);
    $data = array();
    while ($bankAccount = $result->fetch()) {
        $data[] = array(
            'id' => $bankAccount->id,
            'name' => $bankAccount->name,
            'balance' => $bankAccount->balance,
        );
    }

    $response = new Phalcon\Http\Response();

    if ($data == false) {
        $response->setStatusCode(404, "Not Found");
        $response->setJsonContent(array('status' => 'NOT-FOUND'));
    } else {
        $response->setJsonContent(array(
            'status' => 'FOUND',
            'data' => $data
        ));
    }

    return $response;

});

$app->get('/', function () use ($app) {
    echo "Operand Is Cool!";
});

$app->notFound(function () use ($app) {
    $app->response->setStatusCode(404, "Not Found")->sendHeaders();
    echo 'This is crazy, but this page was not found!';
});

$app->handle();

```

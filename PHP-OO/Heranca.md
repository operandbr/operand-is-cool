# Herança

Em orientação a objetos, a herança pode ser implementada com a palavra chave `extends`

```php
<?php

class Usuario
{
    public $id;
	public $nome;
    public $email;

    public function setId($id)
    {
        $this->id = $id;
    }

	public function setNome($nome)
    {
        $this->nome = $nome;
    }

    public function setEmail($email)
    {
        $this->email = $email;
    }

    public function getId()
    {
        return $this->id;
    }

	public function getNome()
    {
        return $this->nome;
    }

    public function getEmail()
    {
        return $this->email;
    }
}

class Admin extends Usuario
{
    public $senha;

    public function setSenha($senha)
    {
        $this->senha = md5($senha);
    }

    public function getSenha()
    {
        return $this->senha;
    }
}

$admin = new Admin();

$admin->setId(1);
$admin->setNome('Arthur');
$admin->setEmail('arthur@coracaodeouro.com');
$admin->setSenha('admin123');

echo $admin->getId() . '<br>';
echo $admin->getNome() . '<br>';
echo $admin->getEmail() . '<br>';
echo $admin->getSenha() . '<br>';
```

[<< Anterior (objeto - segunda parte)](https://github.com/operandbr/operand-is-cool/blob/master/PHP-OO/Objeto2.md)
|
[Próximo (visibilidade) >>](https://github.com/operandbr/operand-is-cool/blob/master/PHP-OO/ModificadoresAcesso.md)

# Docker básico

Nasceu como um projeto open source da DotCloud, uma empresa de PaaS (Platform as a Service) que apesar de estar mais interessada em utilizar LXC apenas em suas aplicações, 
acabou desenvolvendo um produto que foi muito bem aceito pelo mercado.

## Host X Máquina Virtual (VM) X Docker

O host é o computador. (nenhuma novidade)

**VM**

Um segundo S.O inteiro rodando virtualmente em cima do S.O do host.

**Docker**

O docker possui containeres, que são como se fossem serviços empacotados em seus respectivos ambientes.

Serviços pontuais rodando com todas as libs necessárias isoladas do host, porém, compartilhando o kernel do host e algumas libs quando necessário.

[Uma imagem vale mais que mil palavras](https://bytebucket.org/devs-operandbr/operand-is-cool/raw/21d6f3bd90ecf78e2c09c4b78ab184306365ce07/Docker-basico/images/dockervsvm.png?token=690eada9e269e63f1da4bdab35cc66364237898c)

[Menu principal](https://bitbucket.org/devs-operandbr/operand-is-cool/src/master/README.md)
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

[Uma imagem vale mais que mil palavras](https://raw.githubusercontent.com/operandbr/operand-is-cool/master/Docker-basico/images/dockervsvm.png)

[Menu principal](https://github.com/operandbr/operand-is-cool/blob/master/README.md)
# Git básico

[Menu principal](https://github.com/operandbr/operand-is-cool/blob/master/README.md)

Durante a maior parte do período de manutenção do kernel do Linux (1991-2002), as mudanças no software eram repassadas como patches e arquivos compactados.

Em 2002, o projeto do kernel Linux começou a usar um sistema proprietário chamado BitKeeper.

Em 2005, o relacionamento entre a comunidade que desenvolvia o kernel e a empresa que desenvolvia comercialmente o BitKeeper se desfez,
e o status de isento-de-pagamento da ferramenta foi revogado.

Isso levou a comunidade de desenvolvedores do Linux (em particular Linus Torvalds, o criador do Linux) a desenvolver sua própria ferramenta
baseada nas lições que eles aprenderam ao usar o BitKeeper.

### Objetivos da nova ferramenta:

- Velocidade
- Design simples
- Suporte robusto a desenvolvimento não linear (milhares de branches paralelos)
- Totalmente distribuído
- Capaz de lidar eficientemente com grandes projetos como o kernel do Linux (velocidade e volume de dados)

## Comandos básicos

`git clone <url>`

Obter os arquivos de um projeto remoto juntamente com todo o histórico de modificações.

`git status`

Verificar o estado atual do projeto local.
Existem arquivos modificados?

`git add <arquivo>`

Adicionar um arquivo para fazer `commit`.

`git commit`

Criar um commit no repositório local.

`git push`

Enviar os commits do repositório local para o repositório remoto.

`git pull`

Atualizar o repositório local com as atualizações existentes no repositório remoto.

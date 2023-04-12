# Introdução ao Git e ao GitHub

### Comandos básicos para um bom desempenho no terminal

 

#### Comandos básicos para um bom desempenho no terminal:

Windows:

\-cd

\- dir

\- mkdir

\- del / rmdir

 

Linux:      

\- cd                        - Esses são usados no Git também.

\- ls                         - CTRL + L – limpa a tela

\- mkdir                 - pwd – mostra o diretório da pasta em q vc está

\- rm -rf

 

1º Passo: abrir o terminal, na aba pesquisar digite cmd e ENTER para entrar no Prompt de Comando.

Ao usar o dir – mostra o sistema de diretórios na pasta onde estamos situados. No Linux, esse comando é o ls.

\- cd – navegar entre as pastas, se usar cd / - ele vai entrar na pasta de diretório C (C:/). Ele entra na pasta especificada na frente do código.

Exemplo, entrar na pasta Windows: usar o cd Windows, após o cd podemos colocar a primeira letra e apertar o TAB que ele vai listando as pastas existentes que começam com W. Aí aperta ENTER e está dentro desta pasta. 

\- cd .. – Retrocede um passo na navegação, faz o caminho de volta. 

\- cls (clear screen) – vai limpar o terminal, deixar mais clean para visualização.

\- mkdir – criar uma pasta, após mkdir, escrever o nome da nova pasta, ex: mkdir workspace ENTER e a pasta está criada. 

\- del – deleta arquivos dentro da pasta 

\- rmdir (remove directory) – deleta a pasta e todos os arquivos dentro dela. 

Ex: rmdir workspace /S /Q

Se usar a seta para cima no prompt ele lista as funções já feitas, caso vc precise usar uma função novamente e não a precisa escrever, poupa tempo. 

Qualquer comando que vc queira saber o que significa, dê espaço e /? depois ENTER

Ex.: rmdir /?

 

#### Tópicos fundamentais para entender o funcionamento do Git

**\- SHA1**

É um algoritmo de encriptação. Ele pega seu arquivo, pode ser um documento ou uma foto e ele embaralha de uma forma bem específica, que forma um conj. de caracteres de 40 dígitos, que é único e serve de identificação.

Para ver um sha1 de um arquivo: abrir Git Bash na pasta onde está o arquivo e dar, por ex.,  o comando - openssl sha1 text.txt quando o nome do arquivo for text.txt, aí você só muda esse nome.

 

#### Objetos Interno do Git:

**\- Blobs**

Um blob (objeto binário grande) do Git é o tipo de objeto usado para armazenar o conteúdo (tamanho, sha1) de cada arquivo em um repositório. O hash SHA-1 do arquivo é calculado e armazenado no objeto do blob. Esses pontos de extremidade permitem que você leia e grave objetos de blob no banco de dados do Git no GitHub. Os blobs aproveitam estes tipos de mídia personalizados.

 **\- Trees **

Um objeto da árvore do Git cria a hierarquia entre arquivos em um repositório do Git. Você pode usar o objeto da árvore do Git para criar a relação entre diretórios e os arquivos que eles contêm. Esses pontos de extremidade permitem que você leia e grave objetos de árvore no banco de dados do Git no GitHub.

As Trees armazenam os blobs e o nome do arquivo, monta toda a estrutura de onde estão os arquivos. Elas também possuem seu próprio sha1

**\- Commits**

O Commit é o objeto que vai juntar tudo, ele aponta para uma árvore, para um parente (último commit realizado antes dele), para um autor e para uma mensagem. Possuem também um timestamp que é um carimbo de tempo – tem a hora e a data de quando foi criado. Ele também possui um SHA1, portanto se vc mudar algo dentro do arquivo, vc altera o sha1 do blob que consequentemente altera o sha1 da Tree que consequentemente altera o sha1 do commit. 

​                 

 #### Chave SSH e Token:

**Chave SSH** 

É uma forma de estabelecer uma conexão segura e encriptada entre 2 máquinas.

\- Para criar essa chave no Git: Abrir GitBash e colocar 

ssh-keygen -t ed25519 -C   SEU EMAIL

Entrar no diretório criado, usar comando ls, que vai listar a pasta e aí comando 

cat id_ed25519.pub 

para ver o id público, copia-o e passe para o ssh no site do GitHub. 

 

\- Para inicializar o SSH Agent, que vai ficar encarregado de pegar as chaves e lidar com elas:

eval $(ssh-agent -s)

Aí ele dá um nº de processo (Agent pid), que vai rodar por trás. Dá um ssh agent para rodar em plano de fundo.

Agora vamos entregar a chave ssh privada para o agente.

ssh-add id_ed25519

Pronto, esses são os passos para criação da chave.

 

**Para criar Token:**

Vai no Settings do GitHub.com e, a esq, Developer Settings e Personal Acess Token.

 

**Iniciando o Git e criando um commit**

Criar um repositório no git:

git init

E vai aparecer:

Initialized empty Git repository in C:/workspace/livro-receitas/.git/

Pois escrevi git init nessa pasta, aonde fui indo através do cd, ou posso entrar na pasta, dar um clique direito e iniciar GitBash Here. 

ls -a > o menos a mostra os arquivos ocultos 

Para entrar nesse git:      cd .git/

ls



**Configurar o Git para ter o autor no commit:**

$ git config --global user.email   EMAIL    ENTER

$ git config --global user.name USERNAME

 

Agora vamos criar um arquivo Markdown (forma mais ‘humana’ de escrever um arquivo HTML) dentro da pasta. Sua extensão é .md

Você pode ir, no Typora, em Ajuda e Markdown Reference, ele é um guia que mostra todos os tipos de formatação no Markdown. 



**Criar um commit no Git:**

Entrar na pasta livro-receitas e escrever:

$ git add .      



 Enter e aí escreve:

 $ git commit -m "commit inicial"     (Esse nome entre aspas vc que escolhe)

 

Vai aparecer: 

 [master (root-commit) 3ec49b9] commit inicial

 1 file changed, 0 insertions(+), 0 deletions(-)

 create mode 100644 Pizza.md

 

#### Ciclo de vida dos arquivos no Git

GIT INIT – Inicializa o repositório, estamos criando um repositório dentro daquela pasta 

TRACKED E UNTRACKED – Arquivos rastreados e não rastreados (que o git não tem ciência deles) , Os tracked são subdivididos em Unmodified, Modified e Staged – Não modificado, Modificado e os que estão se preparando para fazerem parte de um outro grupo, para a ação, tipo a coxia, o backstage. (que é geralmente do Commit)

Quando vc coloca arquivos modified ou staged em um commit, cria um commit, o git faz tipo um snapshot de como eles estão antes de serem modificados e volta tudo para Unmodified. É cíclico, um ciclo dos arquivos dentro do git.

E quando usamos o git init e criamos um repositório, temos a separação de 2 ambientes: o Servidor (GitHub) e o Ambiente de desenvolvimento (representa tudo que está na nossa máquina). O que a gente criou agora, o livro de receitas está no ambiente de desen., no local repository. 

O seu repositório local pode fazer parte de um repositório remoto (tipo o GitHub).

O git add e o git init movem um arquivo Untracked para Staged. E eles saem do Staged quando vc cria um commit. Portanto, quando vc cria o commit vc modifica duas coisas: vc move o arquivo da área de Staged para Unmodified. 

O seu Repositório Local só é formado por Commits , vc só pode transformar seu repositório local em repositório remoto se ele só for formado por Commits.

Usar o comando “git status” mostra as informações de onde está nosso arquivo.



#### Trabalhando com o GitHub

Vamos criar um repositório remoto, ‘empurrando’ do nosso repositório local para o remoto.

Primeiro precisamos ver se as infos do seu repositório local batem com a do GitHub

Para isso,

$ git config --list

E veja se as infos batem com as suas no GitHub (devem estar iguais)

Aí vamos ao GitHub, clique na bolinha do seu perfil e vá para ‘Your Repositories’ e clique em ‘new’.

Como já criamos um arquivo README.md no Typora, não precisamos marcar a caixa de criar um arquivo READ.ME, daí ele já procura um arquivo MARKDOWN na pasta que, se vc não tiver, marque a caixa para ele criar um. O MARKDOWN é a formatação utilizada pelo GitHub.

Agora vamos ‘empurrar’ o repositório local, copiando a URL passada

$ git remote add origin URL

Com o $ git remote -v , conseguimos ver as listas de repositórios remotos que temos cadastradas.

Aí dê um ‘git status’ para ver se não há nenhuma pendência no repositório 

E vamos ‘’empurrar’’ nosso repositório de origem para o remoto. Usamos o master, que é a branch que a gente está enviando nosso código.
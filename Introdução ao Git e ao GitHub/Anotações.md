## 1. Introdução ao Git

### 1.1. Por que aprender? 

Git é um sistema de versionamento de código distribuído, foi criado em 2005, pelo Linus Torvalds (o criador do sistema Linux), além de ser feito de maneira colaborativa.

O Git é um software que auxilia na criação e na organização das diferentes versões de um código dentro de uma máquina. Já o GitHub é uma plataforma da Microsoft com as mesmas funções do Git.

Vantagens de se aprender sobre esses sistemas:

​	i) controle de versão; 

​	ii) armazenamento em nuvem; 

​	iii) trabalho em equipe; 

​	iv) melhorar seu código e; 

​	v) reconhecimento.

### 1.2. Onde baixar?

Link para download do Git: https://git-scm.com/downloads

* **Git Bash**: é um terminal extendido para se otimizar o uso do Git;
* **SHA1**: significa Secure Hash Algorithm (algoritmo de hash seguro), é um conjunto de funções hash criptográficas, projetadas pela NSA (Agência de Segurança Nacional dos EUA). A encriptação gera um conjunto de caracteres identificadores de 40 dígitos. O SHA1 é uma forma curta de representa um arquivo.

### 1.3. Chave SSH

A chave SSH é uma maneira de se estabelecer uma conexão segura e encriptada entre duas máquinas. Na prática, é uma conexão entre uma máquina local com o servidor GitHub, de modo a marca-la como segura, através de duas chaves, uma pública e outra privada. Ao criar uma conta no GitHub, ir em *Setting* e depois em *SSH and GPG Keys*.

* Abrir o GitBash e digitar: ssh-keygen -t ed25519 -C   *+ email usado no GitHub*

Com isso, o sistema vai gerar uma chave pública e uma privada em um diretório específico do computador. Depois, digitar a seguinte sequência:

* cd /c/Users/NOME DO USUARIO/.ssh/  ➡ ENTER

* ls  ➡ ENTER

* cat id_ed25519.pub ➡ para visualizar a chave pública. Copiar essa chave e inserir no GitHub, no mesmo lugar já citado e clicar em Add SSH key ➡ digitar a senha novamente e findo essa parte

* No GitBash, seguir os seguintes passos: 
  * eval $(ssh-agent -s) ➡ ele retorna Agent pid 1382 (esse número varia), indicativo que um processo foi iniciado;
  * Digitar ls ➡ ENTER;
  * Digitar ssh-add id_ed25519 ➡ ENTER;
  * Por fim, digitar a senha que foi usada (se tiver) ➡ ENTER. Esse passo é para se descriptografar os códigos criptografados

### 1.4. Token

Token de acesso pessoal é uma chave especial que se digita quando for upar um commit. Não é muito recomendável muito porque é uma chave grande e deve ser guardada muito bem, pois ela não aparece novamente.

Para criar um token, é preciso ir no perfil pessoal do GitHub > Developer Setting > Personal access tokens. Colocar um nome, data de expiração e marcar apenas a opção repo e clicar em Generate token. **Guardar esse código porque ele não aparece novamente**. Para clonar o repositório, no caso de token, é preciso copiar o https. Para clonar é só digitar no git: git clone COLAR O HTTPS COPIADO DO GITHUB.

## 2. Comandos básicos do Git

| **Windows<br>(derivado do Shell)** | **Unix<br>(derivados do Bash)** |        **Ações**        |
| :--------------------------------: | :-----------------------------: | :---------------------: |
|                 cd                 |               cd                |   Mudar de diretório    |
|                dir                 |               ls                |    Listar as pastas     |
|               mkdir                |              mkdir              |  Criar pastas/arquivos  |
|             del/rmdir              |             rm -rf              | Deletar pastas/arquivos |

Outros comandos: clear ou cl (limpa o painel)

## 3. Objetos internos do Git

| **Objetos internos <br/>do Git** | **Descrição**                                                | **O que compõe o objeto**                                    |
| :------------------------------: | :----------------------------------------------------------- | :----------------------------------------------------------- |
|              Blobs               | São arquivos que possuem metadados                           | i) Tipo do objeto;<br>ii) Tamanho da string ou arquivo;<br>iii) \0;<br>iv) Conteúdo do arquivo. |
|              Trees               | Também são compostas por metadados. <br>Armazenam blobs.     | i) Tipo do objeto;<br>ii) Tamanho da string ou arquivo;<br>iii) \0;<br>iv) Conteúdo do arquivo;<br>v) Nome do arquivo <br>(blobs não guardam nome do arquivo). |
|             Commit*              | É um objeto que junta tudo e dá sentido <br>para alteração que se está sendo realizada.<br>Pode apontar para: i) uma árvore; <br>ii) um parente (o último commit realizado <br>antes dele); iii) o autor e/ou; <br>iv) uma mensagem. | i) tree;<br>ii) parente;<br>iii) autor;<br>iv) mensagem;<br>v) timestap - é um carimbo que informa<br>a data e hora que o commit foi gerado. |

*Cada commit também possui um SHA1, isso significa que, caso seja feita uma leve modificação numa blob, toda a estrutura dentro da commit será modificada.

## 4. Ciclo de Vida no Git

![image1](https://github.com/luguifal/dio-desafio-github_prim.repositorio/blob/cdd622f0949c884d48e005f4fd9c5200f9822ce6/Introdu%C3%A7%C3%A3o%20ao%20Git%20e%20ao%20GitHub/images/image1.png "Image 1")

## 5. Passos iniciais no Git

* **Criando repositório**: Criar um repositório no Git, deixando marcada a opção Add a README file, pois é possível deixar uma apresentação ao código que seja descrito;
* A extensão do README é **.md**, para mais informações, acessar o link: https://www.markdownguide.org/basic-syntax/#horizontal-rules;
* **Clonando repositório**: copiar o diretório (HTML no caso do exercício) e depois, executar o Git Bash (botão direito do mouse), dentro do diretório no qual se deseja guardar os arquivos. Dentro da janela: digitar: **git clone** + *colar o diretório do repositório*;
* Depois de acrescidas as novas informações, executar, dentro da janela do Git Bash: 
  * git add. *- Esse ponto aqui no final é para colocar, não é ilustrativo não!* 😆
  * git commit -m *"Colocar um nome que denote minimamente as modificações realizadas entre aspas duplas"*
  * git push origin main
  * Outro comando empregado no Git:
    * git status    *(retorna a situação do repositório, se tem modificações ou não)*

## 6. Conflitos entre repositórios no Git

É muito comum que, ao realizarmos atualizações em nossas versões de código, outros dev's estejam trabalhando nele. Caso eles atualizem o repositório antes, no ato da nossa submissão, será acusado um erro. O Git vai demandar que seja executado um **git pull origin main** (download do repositório já submetido) para que o desenvolver faça uma análise dos dois códigos e depois, realize um **git push origin main**.

 
## D3 LIB ✨ </br>
O template facilita a configuração do `enviroment` de nossos projetos, automatizando muita coisa, caso use o template o seu projeto será envolvido por ele, ou seja, seu projeto vai ficar dentro dele </br>
Essa biblioteca é capaz de tornar a experiência no momento da criação de novos projetos mais padronizada, fluída e prática. Utilizando scripts auxiliares, buscamos facilitar o uso das ferramentas e tecnologias presentes no dia a dia dos desenvolvedores, como:
- Clonagem de repositórios
- Build docker compose images
- Start dos containers
- Deploy
- …
- …

Para entender melhor, visite a [documentação] da biblioteca
<br/><br/>

## 🛠️ Tecnologias utilizadas
- `Bash`
</br></br>

## 🔎 Pré-requisitos <br/>
Para executar a maioria dos scripts presentes na biblioteca, você vai precisar de uma máquina que possua:
- `Git`
- `Bash`

💡 Recomendamos o uso do `Docker` para isolar a sua aplicação da máquina
</br></br>

## ▶️ Getting Started
- Entre no [repositorio] e clique em `Use this template` </br>
<i>... Comentar sobre permissões com o repositório da D3</i>

- Você deve setar o Owner com o seu próprio USER, depois defina um nome para o repositório, crie um repo privado de preferencia, selecione `Include all branches`

- Clone o repositório, exemplo:<br/>
`git clone git@github.com:nand0diaz/d3-definitivetemplate.git`</br>
<i>… Verificar se preciso digitar mais coisas”</i>
<br/><br/>
O template contém pastas e arquivos, use o `Bash` para executar os <b>scripts shells</b> do template, por exemplo:
`bash clone.sh`
- Com o terminal, abra o diretório do template
- Agora você pode usar o bash de seu terminal para executar um dos 4 principais scripts `build` `clone` `d3shell` `deploy`
- Vamos comecar clonando um repositório<br/>
Digite `bash clone.sh` no terminal 
“ele irá clonar os repositórios que você digitou no arquivo `.config`”
O script pode:
	- Clonar repositórios (inclusive a `branch` `hash` `path` especificos) <br/>
	- <i>... Build Docker compose images</i>
	- Iniciar os containers
- Será criado uma pasta dentro do template com os repositórios clonados, você pode escolher o nome da pasta pelo arquivo `.config`, dentro dessa pasta vai ter uma outra chamada `d3-dummy` que é exatamente o repositório baixado
- Se você digitar `localhost:80` no navegador você podera ver que já vai estar rodando a imagem de um segundo repositório que foi baixado através do primeiro “um puxou o outro”, esse segundo repositório contém apenas um simples `HTML`<br><br>
💡 Dentro do arquivo `.config` do primeiro repositório contém as informações para baixar o segundo, que é o `d3-dummy2`<br/>
💡 Dentro do arquivo `docker-compose.example.yml` contem as informações do Docker, por exemplo: as portas que irão rodar

<i>... Continuar o step-by-step de como usar o d3shell e o deploy </i>
<br/><br/>

## Estrutura do ambiente:
- 📂 <b>.d3-lib</b>: contém abstrações de scripts que serão usados pelos scripts principais, são scripts prontos para realizarem determinada funcionalidade e 100% aberto para modificações e adição de novas features:
    - 📂 <b>sample</b>: … <br/>
    - 📄 <b>aws_dependencies.sh</b>: … <br/>
    - 📄 <b>aws_module.sh</b>: ...<br/>
    - 📄 <b>checkout_module.sh</b>: ...<br/>
    - 📄 <b>clone_module.sh</b>: ...<br/>
    - 📄 <b>rancher_module.sh</b>: ...<br/>
    - 📄 <b>ssh_dependencies.sh</b>: ...<br/>
    - 📄 <b>ssh-login.sh</b>: … <br/>
    - 📄 <b>ssh-login.md</b>: ...<br/><br/>

- ... 📂 <b>.github/ workflows</b>: contém o `yml` que edita a `pipeline`<br/>

- ⚙️ <b>.config</b>: é o arquivo que você irá inserir as informações dos reposítórios que serão clonados: <br/>
    - SSH da origin do repositório <br/>
    - Branch <br/>
    - Commit Hash <br/>
    - Path <br/><br/>

- ⚙️ <b>.example.env</b>: contém variaveis de ambiente opcionais, renomeie o arquivo<br/>

- 📄 <b>.gitignore</b><br/>

- 💿 <b>clone.sh</b>: contém os scripts que fará a clonagem dos repositórios que você inseriu no `.config`, ele vai procurar em `.d3-lib/clone_module.sh` os scripts que serão executados, o script realiza a clonagem do repositório utilizando `SSH`, então para o uso do mesmo certifique-se de estar com sua chave SSH configurada<br/>
💡 Se o repositório clonado tiver outro arquivo `clone.sh` na raiz ele também será executado, e vai baixar outros repositórios, esses repositórios serão as dependencias “nested dependence”<br/>

- 💿 <b>build.sh</b>:  contém os scripts que:
    - Executa a clonagem dos repositórios `bash clone.sh`
    - Da o build em todas imagens dos repositórios `docker-compose -f docker-compose.example.yml build`
    - Da UP em todas as imagens `docker-compose -f docker-compose.example.yml up -d`
    tanto o build quanto o UP usam o arquivo `docker-compose.example.yml` para o `Docker compose`
    * Os scripts são opcionais, se não quiser usar um em especifico você pode digitar `#` para comenta-lo<br/><br/>

- ... 💿 <b>d3shell.sh</b>: ajuda a configurar o SSH<br/>

- ... 💿 <b>deploy.sh</b>: utilize o script `deploy.sh` para automatizar o deploy de suas aplicações, podendo também fazer o deploy automático apartir de sua maquina<br/>

- ⚙️ <b>.docker-compose.example.yml</b>: configuração do Docker compose:
    - Pasta do projeto
    - Arquivo dockerfile do projeto
    - Imagem
    - Nome do container
    - Portas
    - Networks
<br/><br/>

- ... 🐋 <b>Dockerfile</b>: …<br/>

- 📄 <b>README.md</b>: documentação do nosso template

[documentação]: https://www.notion.so/d3-company/D3-Lib-0a7848f6d60347eab1191e9ba9d5663f
[repositorio]: https://github.com/d3estudio/d3-lib

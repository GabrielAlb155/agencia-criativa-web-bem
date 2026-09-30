Agência Criativa Web — Refatoração com BEM e Sass

Projeto desenvolvido para a atividade de refatoração de CSS legado da disciplina de desenvolvimento web.

O projeto foi reorganizado utilizando a metodologia BEM (Block, Element, Modifier) e Sass/SCSS, buscando melhorar a organização, reutilização, manutenção e responsividade do código.

Objetivos da atividade

A refatoração foi realizada com os seguintes objetivos:

Organizar e padronizar o CSS legado.

Aplicar a metodologia BEM.

Reduzir a especificidade dos seletores.

Eliminar o uso de seletores #id no CSS/SCSS.

Criar componentes reutilizáveis e organizados.

Separar o código SCSS em arquivos parciais.

Manter a responsividade do site.

Corrigir a estrutura da seção de serviços.

Manter apenas o arquivo CSS compilado utilizado pelo HTML.

Utilizar Sass para gerar automaticamente o CSS final.

Tecnologias utilizadas

HTML5

CSS3

Sass/SCSS

Metodologia BEM

JavaScript

Git

GitHub

Visual Studio Code

Live Server

Estrutura do projeto

agencia-criativa-web-bem/
│
├── index.html
├── package.json
├── package-lock.json
├── README.md
│
├── css/
│   ├── estilos.css
│   └── estilos.css.map
│
└── scss/
    ├── _base.scss
    ├── _componentes.scss
    ├── _layout.scss
    ├── _mixins.scss
    ├── _variaveis.scss
    └── estilos.scss

Descrição das pastas

index.html
Arquivo principal da página.

css/estilos.css
CSS compilado a partir dos arquivos SCSS. É o arquivo utilizado pelo HTML.

scss/
Contém os arquivos-fonte utilizados para organizar o estilo do projeto.

_variaveis.scss
Centraliza cores, espaçamentos, tamanhos e outras configurações.

_base.scss
Contém reset, configurações gerais e estilos básicos.

_mixins.scss
Contém mixins reutilizáveis do Sass.

_layout.scss
Contém estilos relacionados à estrutura principal da página, como cabeçalho, menu e Hero.

_componentes.scss
Contém os componentes da interface, como botões, cards, depoimentos e formulário.

estilos.scss
É o arquivo principal do Sass. Ele importa os demais arquivos:

@use 'variaveis';
@use 'base';
@use 'mixins';
@use 'layout';
@use 'componentes';

Metodologia BEM

A metodologia BEM foi aplicada na organização das classes.

Blocos

Exemplos:

.cabecalho
.menu
.hero
.secao
.sobre
.servicos
.servico-card
.depoimento
.formulario
.rodape

Elementos

Exemplos:

.cabecalho__container
.cabecalho__logo
.menu__link
.hero__titulo
.hero__descricao
.sobre__texto
.sobre__destaques
.servicos__lista
.servico-card__titulo
.servico-card__descricao
.formulario__campo
.rodape__texto

Modificadores

Exemplos:

.secao--clara
.botao--primario
.botao--secundario
.formulario__campo--area

A estrutura segue o padrão:

.bloco
.bloco__elemento
.bloco--modificador

Correções realizadas conforme o feedback

1. Correção da seção de serviços

Foi corrigida a diferença entre o nome utilizado no HTML e o nome utilizado no SCSS.

A estrutura agora utiliza:

<div class="servicos">
    <div class="servicos__lista">
        ...
    </div>
</div>

E o SCSS possui:

.servicos__lista {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
}

Dessa forma, os três cards de serviços são organizados corretamente em colunas.

Em telas menores, o layout é adaptado:

@media (max-width: 900px) {
    .servicos__lista {
        grid-template-columns: 1fr;
    }
}

2. Remoção do CSS duplicado

Foi removida a versão antiga/duplicada do estilos.css que ficava na raiz do projeto.

O projeto utiliza somente:

css/estilos.css

O HTML referencia esse arquivo:

<link rel="stylesheet" href="css/estilos.css">

Isso evita confusão sobre qual arquivo deve ser alterado.

3. Organização do Sass

O projeto foi dividido em arquivos parciais:

scss/
├── _base.scss
├── _componentes.scss
├── _layout.scss
├── _mixins.scss
├── _variaveis.scss
└── estilos.scss

Essa organização facilita a manutenção e permite separar responsabilidades.

4. Melhoria da nomenclatura BEM

Na seção Sobre, os parágrafos receberam uma classe própria:

<p class="sobre__texto">

Assim, em vez de depender de um seletor como:

.sobre__conteudo p

é utilizada uma classe BEM específica:

.sobre__texto

Isso mantém a nomenclatura mais consistente e reduz a dependência da estrutura do HTML.

5. Seletores de ID

Os id utilizados no HTML servem para navegação por âncoras e associação dos campos do formulário.

Exemplo:

<section id="sobre">

e:

<a href="#sobre">Sobre</a>

Esses id não são utilizados como seletores no CSS ou SCSS.

A estilização é feita por classes BEM.

Responsividade

O projeto possui media queries para adaptar o conteúdo a diferentes tamanhos de tela.

Foram consideradas principalmente:

Desktop

Tablet

Smartphone

Exemplo:

@media (max-width: 900px) {
    .servicos__lista {
        grid-template-columns: 1fr;
    }
}

Também são adaptados:

Cabeçalho

Menu

Hero

Botões

Cards

Formulário

Espaçamentos

Instalação

Para utilizar o projeto localmente, é necessário ter o Node.js instalado.

Depois de abrir a pasta do projeto no terminal do VS Code, execute:

npm install

Esse comando instala as dependências definidas no package.json.

Compilação do Sass

Para deixar o Sass observando as alterações nos arquivos SCSS, execute:

npm run sass

O comando utilizado é:

sass --watch scss/estilos.scss:css/estilos.css

Enquanto esse comando estiver funcionando, alterações nos arquivos .scss serão compiladas automaticamente para:

css/estilos.css

Para interromper o processo:

Ctrl + C

Compilação única

Também existe o comando:

npm run build

Ele compila o SCSS uma vez e gera o CSS:

css/estilos.css

Visualização do site

Para visualizar o projeto no navegador:

Abra a pasta no Visual Studio Code.

Instale a extensão Live Server, caso ainda não tenha.

Clique com o botão direito no arquivo index.html.

Selecione Open with Live Server.

Git e GitHub

Depois de finalizar e testar o projeto, os arquivos podem ser enviados para o GitHub.

Adicionar as alterações:

git add .

Criar o commit:

git commit -m "Corrige atividade BEM conforme feedback do professor"

Enviar para o GitHub:

git push

Caso o repositório ainda não esteja conectado:

git remote add origin URL_DO_REPOSITORIO

Depois:

git branch -M main
git push -u origin main

Substitua URL_DO_REPOSITORIO pela URL do seu repositório GitHub.

Observação sobre node_modules

A pasta:

node_modules/

é criada pelo comando:

npm install

Ela não precisa ser enviada para o GitHub.

O projeto deve possuir um arquivo .gitignore contendo:

node_modules/

Resultado da refatoração

Após as alterações, o projeto apresenta:

Estrutura BEM organizada.

Classes com nomenclatura consistente.

CSS sem seletores de ID.

SCSS dividido em parciais.

Variáveis e mixins reutilizáveis.

Seção de serviços funcionando corretamente.

Layout responsivo.

Um único CSS compilado utilizado pelo HTML.

README atualizado.

Configuração para compilação automática com Sass.

Autor

Gabriel

Projeto acadêmico — Agência Criativa Web.
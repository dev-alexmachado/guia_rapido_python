# Django

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Instrodução](#introdução)
2. [Estrutura do Django](#estrutura-do-django)<br>
    2.1 [Projeto](#projeto)<br>
    2.2 [Aplicação](#aplicação)<br>
    2.3 [Como esses conceitos se combinam](#como-esses-conceitos-se-combinam)<br>
    2.4 [Em qual conceito ela é baseada](#em-qual-conceito-ela-é-baseada)<br>
    2.5 [Por que esse padrão é útil](#por-que-esse-padrão-é-útil)<br>
3. [Instalação](#instalação)
4. [Novo Projeto](#novo-projeto)<br>
    4.1 [Para testar a aplicação](#para-testar-a-aplicação)
5. [Conectar com o banco de dados](#conectar-com-o-banco-de-dados)<br>
    5.1 [SQLite](#sqlite)<br>
    5.2 [MySQL](#mysql)<br>
    5.3 [Configurando dois bancos diferentes no projeto](#configurando-dois-bancos-diferentes-no-projeto)<br>
    5.4 [Migrações](#migrações)<br>
    5.5 [Estabelecendo conexão com o banco](#estabelecendo-conexão-com-o-banco)<br>
6. [Superuser](#superuser)
7. [Novo app](#novo-app)

## Introdução

> [!NOTE]
> Django é o principal framework web para Python. É usado para a criação de grandes sistemas web. Um único projeto é capaz de comportar várias aplicações diferentes unidas por um gigantesco ecosistema, incluindo Banco de Dados, Segurança e APIs.

## Estrutura do Django

A estrutura de um projeto Django é baseada em dois conceitos principais:

1. **Projeto** ou **Core** (`project`)
2. **Aplicação** (`app`)

### Projeto
O projeto é a configuração global que reúne as aplicações, URLs, configuração de banco de dados, middlewares, templates, etc.

Normalmente ele contém:
- `manage.py` — comando de controle do Django
- pasta do projeto (ex: `nome_do_projeto/`) com:
  - `settings.py` — configurações do projeto
  - `urls.py` — roteamento das URLs principais
  - `wsgi.py` / `asgi.py` — ponto de entrada para servidores web
  - `__init__.py`

### Aplicação
Uma aplicação é uma parte específica do sistema, com responsabilidade clara.

Cada app costuma ter:
- `models.py` — definição dos dados / tabelas
- `views.py` — lógica que responde a requisições
- `urls.py` — rotas internas da app (opcional mas comum)
- `templates/` — arquivos HTML
- `static/` — arquivos CSS, JS, imagens
- `admin.py` — cadastro no painel administrativo
- `apps.py` — configuração da app
- `tests.py` — testes automatizados

### Como esses conceitos se combinam
- um projeto pode ter várias apps
- cada app é reutilizável e independente
- o projeto conecta todas as apps e define o fluxo geral

### Em qual conceito ela é baseada
A estrutura do Django é baseada no padrão:
- **MTV** (Model-Template-View), uma variação do MVC

Onde:
- `Model` = dados e regras de negócio (`models.py`)
- `Template` = apresentação/HTML (`templates/`)
- `View` = lógica que processa a requisição e escolhe o template (`views.py`)

### Por que esse padrão é útil
- separa responsabilidades
- facilita organizar código em partes claras
- torna o projeto escalável
- ajuda a manter apps reutilizáveis

> [!TIP]
> Resumindo: um projeto Django é composto por um “contêiner” de configuração e por várias aplicações pequenas, seguindo uma arquitetura baseada em MTV para separar dados, lógica e apresentação.

## Instalação

Para instalar o Django, certifique-se de que a venv esteja criada e ativada, e então digite no terminal:
~~~
pip install django
~~~

Caso não tenha a venv criada:
~~~
py -m venv .venv
.venv\Scripts\activate
pip install django
~~~

## Novo Projeto

Para criar um novo projeto, seguem as opções:
1. Para criar um projeto na pasta da venv:
~~~
django-admin startproject nome_do_projeto
~~~
2. Ou para transformar a pasta onde se encontra a venv no próprio projeto:
~~~
django-admin startproject .
~~~

Sequencia para quem não criou a venv:
~~~
py -m venv .venv
.venv\Scripts\activate
pip install django
django-admin startproject nome_do_projeto
~~~

### Para testar a aplicação

> [!WARNING]
> Diferentemente dos outros programas Python, aqui a execução da aplicação não acontece ao abrir o arquivo principal e apertar `Ctrl+F5`. Continue lendo para ver como executar uma aplicação Django.

1. Abra o terminal (`Ctrl+J`) e use-o para navegar até a pasta do projeto:
~~~
cd nome-do-projeto
~~~
2. Depois execute o comando abaixo para iniciar o servidor:
~~~
py manage.py runserver
~~~
3. Isso irá startar o servidor local na porta **8000**. Abra o navegador de sua preferência e acesse **http://localhost:8000**.

Se tudo der certo, o navegador irá mostrar uma tela com um foguete e um texto mostrando que o Django está funcionando corretamente.

A sequência de comandos para sair do zero e chegar até a hora de abrir o navegador é:
~~~
py -m venv .venv
.venv\Scripts\activate
pip install django
django-admin startproject nome-do-projeto
cd nome-do-projeto
py manage.py runserver
~~~

## Conectar com o banco de dados

> [!TIP]
> Ao instalar o Python no seu computador, ele também instala junto um SGBD pronto para ser usado por qualquer programa que você criar, seja ele escrito em Python ou não: o **SQLite**.<br>
> O SQLite é um "micro SGBD", que comporta poucos dados em comparação com outros SGBDs, como o MySQL e o PostgreeSQL, sendo mais recomendado para testar sistemas, ou para aplicações de pequeno porte.<br>
> Ele é muito usado no mercado, pois tem a vantagem de criar um arquivo `.db` ou `sqlite3` que funciona como um micro servidor dentro da própria aplicação, diferentemente de outros SGBDs que exigem conexão com um servidor.

Dentro da pasta do projeto, abra o arquivo `settings.py` e procure por `DATABASES` (provável linha 75). Ele é um dicionário com o seguinte código:
~~~python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
~~~

Esta parte do código é o responsável por configurar o banco de dados do seu projeto. Veja como fazer isso logo abaixo:

### SQLite

Caso opte por usar o SQLite no seu projeto, altere a linha 78, de `'NAME': BASE_DIR / 'db.sqlite3',` para `'NAME': BASE_DIR / 'banco_do_projet.db',` ou então para `'NAME': BASE_DIR / 'banco_do_projet.sqlite3',`. O código ficará mais ou menos assim:
~~~python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'banco_do_projeto.db',
    }
}
~~~

### MySQL

Caso opte por usar o MySQL, precisará alterar todo o dicionário do `DATABASES`. Veja o código para usar o MySQL:
~~~python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'nome_do_banco',
        'USER': 'usuario',
        'PASSWORD': 'senha',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
~~~

> [!CAUTION]
> As informações acima consideram o servidor do banco de dados sendo executado localmente com a porta padrão. Altere os dados de acordo com a configuração do seu MySQL.

Além disso, será necessário instalar o ***driver*** do MySQL no seu projeto. Abra o terminal no diretório da venv que seu projeto usa, e execute o comando:
~~~
pip install mysqlclient
~~~

> [!IMPORTANT]
> A configuração do `DATABASES` e o comando de instalação do driver muda dependendo do SGBD escolhido para o seu projeto. Consulte as informações necessárias caso o SGBD que for usar seja diferente dos utilizados neste guia.

### Configurando dois bancos diferentes no projeto

> [!TIP]
> É possível configurar dois bancos diferentes ou mais simultâneamente no mesmo projeto, o que pode ser muito útil para várias ocasiões, como migração de banco, por exemplo.

Para configurar, por exemplo, um banco SQLite e um MySQL no mesmo projeto:
~~~python
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.sqlite3",
        "NAME": BASE_DIR / "banco_do_projeto.db",
    },
    "mysql": {
        "ENGINE": "django.db.backends.mysql",
        "NAME": "nome_do_banco",
        "USER": "usuario",
        "PASSWORD": "senha",
        "HOST": "localhost",
        "PORT": "3306",
    },
}
~~~

> [!IMPORTANT]
> Lembre-se de que para cada SGBD diferente que for usar, será necessário instalar seu driver. Procure saber qual comando específico deverá ser usado para instalá-lo no seu projeto.

### Migrações

> [!CAUTION]
> Quando uma alteração que influencia no banco de dados é feita, é necessário executar a migração para que as alterações sejam aplicadas no banco.

Para migrar as alterações para o banco de dados, execute no terminal dentro da pasta do projeto:
~~~
py manage.py makemigrations
~~~

Em seguida, execute no terminal:
~~~
py manage.py migrate
~~~

A sequencia correta é:
~~~
py manage.py makemigrations
py manage.py migrate
~~~

### Estabelecendo conexão com o banco

Para conectar seu projeto com o banco, basta rodar o servidor do Django, abrindo o terminal no diretório do seu projeto e executando o comando:
~~~
py manage.py runserver
~~~

> [!WARNING]
> Lembre-se de que antes de ligar o servidor do Django, o servidor do banco de dados deverá já estar ligado também.<br>
> A exceção a regra é para o SQLite, em que não há necessidade de ligar outro servidor antes. Ao executar o comando no terminal, ele gerará um arquivo na raíz do projeto com o nome configurado em `DATABASES`.

## Superuser

> [!TIP]
> O Django já vem com um sistema de administração do projeto pronto, com tela de login e gerenciamento das entidades do banco, que permite criar novas entidades, e até mesmo fazer o CRUD completo em todas elas. Para que isso seja possível, é necessário a criação de um usuário administrador, que chamamos de **Superuser**.

Para criar o **superuser**, abra o terminal na pasta do projeto e execute:
~~~
py manage.py createsuperuser
~~~

Ele irá pedir para criar um nome para o **admin**, e uma **senha** (não esqueça a senha). Defina essas informações e confirme com `Y` quando solicitado.

Se tudo tiver dado certo, abra o navegador e acesse o endereço **http://localhost:8000/admin** para ir para uma tela de login e senha. Use o login e senha definidos no passo anterior para ir para a tela de administração do sistema, onde você terá acesso direto e irrestrito às tabelas do banco (você pdoerá criar tabelas diretamente dessa tela, se desejar).

> [!IMPORTANT]
> A criação do **superuser** só dará certo se antes o sistema tiver estabelecido conexão com o banco de dados previamente configurado, e também se tiver sido executado a migração. A ordem correta dos comandos é:
> ~~~
> py manage.py makemigrations
> py manage.py migrate
> py manage.py createsuperuser
> py manage.py runserver
> ~~~

## Novo app

Como dito anteriormente, ao criar um novo projeto Django, você estará apenas criando seu núcleo. Será necessário criar dentro desse projeto um **app**, lembrando que um único projeto pode ter vários apps.

Para criar um novo app dentro do seu projeto, abra o terminal no diretório do projeto, e execute:
~~~
py manage.py startapp nome_do_app
~~~

Ele irá criar um novo diretório dentro do projeto, com novos arquivos e nova estrutura. É nela que iremos definir as **Models** e o Front-End da sua aplicação, caso seu projeto tenha apenas um único app.
# Django

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Instalação](#instalação)
2. [Novo Projeto](#novo-projeto)<br>
    2.1 [Para testar a aplicação](#para-testar-a-aplicação)

## Introdução

> [!NOTE]
> Django é o principal framework web para Python. É usado para a criação de grandes sistemas web. Um único projeto é capaz de comportar várias aplicações diferentes unidas por um gigantesco ecosistema, incluindo Banco de Dados, Segurança e APIs.

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
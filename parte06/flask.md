# Flask

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Introdução](#introdução)
2. [Instalação](#instalação)
3. [Novo Projeto](#novo-projeto)
4. [Hello World em Flask](#hello-world-em-flask)
5. [Execução de um programa Flask](#execução-de-um-programa-flask)<br>
    5.1 [Rodando o servidor e acessando no navegador](#rodando-o-servidor-e-acessando-no-navegador)
6. [Trabalhando com HTML](#trabalhando-com-html)<br>
    6.1 [Para fazer o Flask reconhecer a Home Page da aplicação](#para-fazer-o-flask-reconhecer-a-home-page-da-aplicação)<br>
    6.2 [Linkando páginas](#linkando-páginas)<br>
7. [Jinja](#jinja)
8. [Modularização](#modularização)<br>
    8.1 [Estrutura](#estrutura)
9. [Dados de formulário](#dados-de-formulário)
10. [Static](#static)<br>
    10.1 [CSS](#css)<br>
    10.2 [Chamando o CSS pelo html](#chamando-o-css-pelo-html)

## Introdução

> [!NOTE]
> Flask é um microframework para a criação de pequenas aplicações web.
> Suas principais características são a baixa curva de aprendizagem, o fato de que ele vem o mais puro possível, onde você mesmo vai adicionando o que deseja incluir no seu projeto, e o fato de que é recomendado para quem deseja construir pequenas aplicações.

## Instalação

Para instalar o flask, certifique-se de que a venv esteja criada e ativada, e então digite no terminal:
~~~
pip install flask
~~~

Caso não tenha a venv criada:
~~~
py -m venv .venv
.venv\Scripts\activate
pip install flask
~~~

## Novo Projeto

Para criar um novo projeto, as opções são:
1. Basta criar uma pasta no mesmo diretório onde a venv foi criada, e dentro dele um arquivo chamado `app.py`.
2. Ou então basta criar o arquivo `app.py` diretamente no diretório onde se encontra a venv.

> [!IMPORTANT]
> Para este guia, vamos prosseguir com a 1ª opção.

## Hello World em Flask

Para criar seu primeiro programinha em Flask, abra o arquivo `app.py` e digite o seguinte código:
~~~python
# importa biblioteca flask
from flask import Flask

# ativa o framework
app = Flask(__name__)

# cria uma rota para o conteúdo a ser exibido no navegador
@app.route("/")
def hello_world():
    return "Olá, Mundo!"

# executa a aplicação
if __name__ == "__main__":
    app.run(debug=True)
~~~

## Execução de um programa Flask

A execução de um programa flask ocorre da mesma forma como qualquer outro programa Python: abra o arquivo `app.py` e então:
1. Use a tecla de atalho `Ctrl+F5`.
2. Ou clique no botão **Run** no alto à direita da janela do VSCode.
3. Ou então abra o terminal e digite:
~~~
py app.py
~~~

### Rodando o servidor e acessando no navegador

Ao executar o arquivo `app.py`, ele irá abrir um servidor web no endereço **http://localhost:5000** ou **http://127.0.0.1/5000**. Abra o navegador de sua preferência e acesse esse endereço para abrir a sua aplicação.

> [!TIP]
> O próprio VSCode tem um navegador dentro dele para você testar sua aplicação. Para acessá-lo, digite a tecla de atalho `Shift+Alt+;`. Depois, é só acessar o endereço que quiser. Pode usá-lo para acessar **http://localhost:5000** e testar sua aplicação Flask.

## Trabalhando com HTML

> [!NOTE]
> A primeira coisa que se deve saber sobre o Front-End é entender exatamente o que significa Front-End. Para o Flask, o Front-End engloba:
> - Páginas HTML
> - CSS
> - JavaScript
> - Imagens
> - Fontes
> - Vídeos
> - Áudios<br>
> Digo isso, o Flask trabalha com Front-End em duas pastas:
> - **Templates**: pasta onde ficam **TODOS** os arquivos HTML da aplicação.
> - **Static**: pasta onde ficam tudo o **que não é** HTML, ou seja, todo o resto: CSS, JS, e arquivos.<br>
> As pastas devem ser criadas no mesmo diretório onde se encontra o arquivo `app.py`.

### Para fazer o Flask reconhecer a Home Page da aplicação

Crie dentro da pasta `templates` um arquivo chamado `index.html`. Segue um exemplo de código-fonte de uma página HTML:
~~~html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplicação Flask</title>
</head>
<body>
    <h1>Home Page da aplicação Flask!</h1>
    <!-- Conteúdo da página inicial -->
</body>
</html>
~~~

Então abra o arquivo `app.py` e faça o seguinte código:
~~~python
from flask import Flask, render_template

app = Flask(__name__)

# cria uma rota para a página HTML
@app.route("/")
def index():
    return render_template('index.html')

if __name__ == "__main__":
    app.run(debug=True)
~~~

Depois é só executar o arquivo `app.py` e acessar o servidor pelo navegador através do endereço **http://localhost:5000**.

### Linkando páginas

Para criar links, é preciso criar uma rota em `app.py` antes:
~~~python
from flask import Flask, render_template

app = Flask(__name__)

@app.route("/")
def index():
    return render_template('index.html')

# rota para outra página
@app.route("/outraPagina")
def outra_pagina():
    return render_template('outra-pagina.html')

if __name__ == "__main__":
    app.run(debug=True)
~~~

Depois, é necessário criar um link para o outro arquivo HTML:
~~~html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplicação Flask</title>
</head>
<body>
    <h1>Home Page da aplicação Flask!</h1>

    <!-- link para outra página -->
    <a href="/outraPagina">Clique aqui para ir para outra página</a>

    <!-- conteúdo da página inicial -->
</body>
</html>
~~~

Crie o outro arquivo HTML com um link para a página inicial:

> [!WARNING]
> Neste caso, o nome do outro arquivo HTML é `outra-pagina.html`, e o nome da rota é `/outraPagina`. Adapte a seu sistema conforme necessário.
~~~html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplicação Flask</title>
</head>
<body>
    <h1>Outra página da aplicação Flask!</h1>

    <!-- link para a página inicial -->
    <a href="/">Clique aqui para ir para a Home Page</a>

    <!-- Conteúdo da outra página -->
</body>
</html>
~~~

## Jinja

Jinja é um mecanismo de templates para Python. Ele permite gerar texto (normalmente HTML) a partir de arquivos que misturam conteúdo estático e placeholders.

Como funciona:
- você cria um arquivo de template com marcações como `{{ nome }}` e `{% for item in lista %}`
- o Jinja substitui essas partes pelo valor real quando o template é renderizado
- o resultado final é uma string pronta para enviar ao navegador ou salvar em arquivo

É o que permite criar páginas web dinâmicas com Python.

Exemplo 1:
~~~python
from flask import Flask, render_template

app = Flask(__name__)

@app.route("/")
def index():
    # variável a ser exibida na página
    nome = "Alex Machado"

    # repassa variável para o render_template
    return render_template('index.html'. nome=nome)

if __name__ == "__main__":
    app.run(debug=True)
~~~
~~~html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplicação Flask</title>
</head>
<body>
    <!-- exibe variável Python no HTML usando jinja -->
    <h1>Olá {{ nome }}, seja bem vindo à Home Page da sua aplicação Flask!</h1>

    <!-- conteúdo da página inicial -->
</body>
</html>
~~~

Exemplo 2:
~~~python
from flask import Flask, render_template

app = Flask(__name__)

@app.route("/")
def index():
    # lista a ser exibida na página
    nomes = ["Fulano","Cicrano","Beltrano"]

    # repassa variável para o render_template
    return render_template('index.html'. nomes=nomes)

if __name__ == "__main__":
    app.run(debug=True)
~~~
~~~html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplicação Flask</title>
</head>
<body>
    <!-- exibe variável Python no HTML usando jinja -->
    <h1>Home Page da aplicação Flask!</h1>
    <ul>
        {% for nome in nomes %}
            <li>{{ nome }}</li>
        {% endfor %}
    </ul>

    <!-- conteúdo da página inicial -->
</body>
</html>
~~~

## Modularização

> [!TIP]
> Para não ter que recriar página por página do início, utilizamos o conceito de modularização das págians HTML.
> Consiste em dividir a página por partes, sendo que cada parte corresponde a um arquivo separado, que ao ser renderizado, juntam-se formando uma única página. Isso permite que, ao clicar em um link, por exemplo, somente o conteúdo da página seja mudado ao invés da página inteira.

### Estrutura

Crie dentro da pasta **templates** os seguintes arquivos:
- `base.html`
- `header.html`
- `footer.html`
- `index.html` (caso ainda não tenha)

> [!IMPORTANT]
> O `base.html` servirá de esqueleto padrão para todas as páginas HTML da sua aplicação, e a estrutura de todas as páginas seguirão ela.

Código-fonte de `base.html`:
~~~html
<!doctype html>
<html lang="pt-br">
  <head>
    <meta name="author" content="Alex Machado Ribeiro">
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>{% block title %}Aplicação Flask{% endblock %}</title>
  </head>
  <body>
    {% include 'header.html' %}
    <main>
        {% block content %}{% endblock %}
    </main>
    {% include 'footer.html' %}
  </body>
</html>
~~~
> [!TIP]
> Apenas o `base.html` precisa ter o escopo completo de um arquivo HTML. Os outros arquivos não precisam ter toda a estrutura completa do HTML, já que receberão o código do `base.html` a partir do jinja.

Código-fonte de `header.html`:
~~~html
<header>
    <a href="/">Home page</a> |
    <a href="/outraPagina">Outra Página</a>
</header>
~~~

Código-fonte do `footer.html`:
~~~html
<footer>
    <p>© Copyright - Todos os direitos reservados.</p>
</footer>
~~~

> [!IMPORTANT]
> Os arquivos de conteúdo da página precisarão indicar pelo jinja que estão recebendo a estrutura da página através do arquivo `base.html`.

Código-fonte do `index.html`
~~~html
{% extends 'base.html' %}
{% block title %}Home Page{% endblock %}
{% block content %}
    <h1>Seja bem vindo à Home Page do sistema Flask! 😎</h1>
{% endblock %}
~~~

Agora é só executar o arquivo `app.py` e rodar o servidor no navegador pelo endereço **http://localhost:5000**.

## Dados de formulário

Para pegar os dados de um formulário e transferí-los para outra página, primeiro precisaremos de uma página com o formulário em si.

> [!WARNING]
> Vamos partir do exemplo do código-fonte anterior, visto na seção **Estrutura**, no capítulo de **Modularização**.

Crie o arquivo `form.html` no mesmo diretório de `index.html`:
~~~html
{% extends 'base.html' %}
{% block title %}Home Page{% endblock %}
{% block content %}
    <form action="/dados" method="POST">
        <label for="nome">Nome:</label><br>
        <input type="text" name="nome" required>
        <br><br>
        <button type="submit">Enviar</button>
    </form>
{% endblock %}
~~~

Vá para o arquivo `app.py` e faça o seguinte código-fonte:
~~~python
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route("/")
def index():
    return render_template('index.html')

# rota para página do formulário
@app.route("/form")
def form():
    return render_template('form.html')

# implementa rota para processar o formulário
@app.route("/dados")
def dados():
    nome = request.form.get('nome', '')
    return render_template('index.html',nome=nome)

if __name__ == "__main__":
    app.run(debug=True)
~~~

Abra o arquivo `index.html` e faça o código para receber o dado do formulário quando o mesmo for preenchido:
<!-- REVIEW: verificar se código está correto -->
~~~html
{% extends 'base.html' %}
{% block title %}Home Page{% endblock %}
{% block content %}
    <h1>Seja bem vindo à Home Page do sistema Flask! 😎</h1>
    <h2>Usuário: <span>{{ nome if nome else '' }}</span></h2>
{% endblock %}
~~~

Para navegar entre as páginas, abra o arquivo `header.html` e faça o seguinte código-fonte:
~~~html
<header>
    <a href="/">Home page</a> |
    <a href="/form">Formulário</a>
</header>
~~~

## Static

> [!IMPORTANT]
> **Static** é uma pasta a ser criada pelo usuário que deve estar localizada no mesmo diretório da pasta **templates**. Sua função é guardar todos os outros arquivos relacionados ao Front-End que não sejam HTML. Ou seja, é nela que vão estar o css, js, imagens, etc...

### CSS

> [!WARNING]
> O arquivo CSS deve estar localizado dentro da pasta **css**, que por sua vez deve ser criada dentro da pasta **static**.

Para usar o css:
1. Crie a pasta **static** dentro da pasta do projeto no mesmo diretório da pasta **templates** (se já não tiver criado).
2. Abra a pasta **static**, e dentro dela crie a pasta **css**.
3. Abra a pasta **css**, e dentro dela crie o arquivo `estilo.css`.

Exemplo de código-fonte css:
~~~css
a {
    text-decoration: none;
    font-weight: bolder;
}

body {
    background-color: #16161d;
    color: #ffffff;
    font-family: Arial, Helvetica, sans-serif;
}
~~~

### Chamando o CSS pelo html

Para vincular o arquivo CSS ao HTML da aplicação, abra o arquivo `base.html`, e insira a linha de código indicada no código-fonte abaixo:
~~~html
<!doctype html>
<html lang="pt-br">
  <head>
    <meta name="author" content="Alex Machado Ribeiro">
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>{% block title %}Aplicação Flask{% endblock %}</title>

    <!-- chama o arquivo css -->
    <link href="{{ url_for('static',filename='css/estilo.css') }}" rel="stylsheet" type="text/css" media="all">
  </head>
  <body>
    {% include 'header.html' %}
    <main>
        {% block content %}{% endblock %}
    </main>
    {% include 'footer.html' %}
  </body>
</html>
~~~

---

- [Voltar ao início](#sumário)
- [Voltar ao índice do Guia Rápido de Python](https://github.com/dev-alexmachado/guia_rapido_python)
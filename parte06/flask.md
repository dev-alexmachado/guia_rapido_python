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
8. [Modularização](#modularização)

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

Ao executar o arquivo `app.py`, ele irá abrir um servidor web no endereço **localhost:5000** ou **127.0.0.1/5000**. Abra o navegador de sua preferência e acesse esse endereço para abrir a sua aplicação.

> [!TIP]
> O próprio VSCode tem um navegador dentro dele para você testar sua aplicação. Para acessá-lo, digite a tecla de atalho `Shift+Alt+;`. Depois, é só acessar o endereço que quiser. Pode usá-lo para acessar **localhost:5000** e testar sua aplicação Flask.

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

Depois é só executar o arquivo `app.py` e acessar o servidor pelo navegador através do endereço **localhost:8000**.

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
- você cria um arquivo de template com marcações como {{ nome }} e {% for item in lista %}
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
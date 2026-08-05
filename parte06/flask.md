# Flask

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Introdução](#introdução)
2. [Instalação](#instalação)
3. [Novo Projeto](#novo-projeto)
4. [Hello World em Flask](#hello-world-em-flask)
5. [Execução de um programa Flask](#execução-de-um-programa-flask)<br>
    5.1 [Rodando o servidor e acessando no navegador](#rodando-o-servidor-e-acessando-no-navegador)

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
# Python Orientado a Objetos

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Classe Python](#classe-python)

## Classe Python

> [!NOTE]
> No paradigma da Orientação a Objetos, o programa é dividido em blocos menores chamados **classes**, que por sua vez são subdivididos em atributos (valores) e métodos (ações). A partir delas, são criados os objetos.

> [!IMPORTANT]
> Alguns detalhes importantes sobre classes Python:
> - Em Python, os atributos são declarados dentro do construtor, que por sua vez é obrigatório.
> - Em Python, o construtor é declarado através do comando `__init__`.
> - Em Python, cada classe só pode ter um único construtor.
> - Em Python, cada método tem que receber como parâmetro a palavra `self`.
> - Em Python, o `self` é utilizado para fazer referência aos atributos dentro dos métodos.
> - O nome de uma classe sempre vai começar com letra maiúscula.
> - O padrão de nomemclatura de classes é o **PascalCase**, ou seja, inicial maiúscula e primeira letra de cada palavra maiúscula.

Para criar uma classe Python, usa-se a palavra `class`. Por exemplo, vamos criar uma classe chamada Pessoa:
~~~python
# classe
class Pessoa:
    # construtor
    def __init__(self, nome, idade, altura):
        # atributos
        self.nome = nome
        self.idade = idade
        self.altura = altura

    # método
    def exibir_dados(self):
        print(f"Nome: {self.nome}")
        print(f"Idade: {self.idade} anos")
        print(f"Altura: {self.altura} metros")
~~~

Para instanciar (criar) um objeto de uma classe, como por exemplo, um objeto da classe Pessoa, definir valores dos seus atributos e executar um método:
~~~python
def main():
    # instancia a classe Pessoa
    usuario = Pessoa(nome="",idade=0,altura=0.0)

    # entrada de dados
    usuario.nome = input("Informe o nome: ").strip().title()
    usuario.idade = int(input("Informe a idade: "))
    usuario.altura = float(input("Informe a altura em metros: ").replace(",","."))

    # saída de dados
    usuario.exibir_dados()

# algoritmo principal
if __name__ == "__main__":
    main()
~~~
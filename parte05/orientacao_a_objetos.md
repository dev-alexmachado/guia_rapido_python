# Python Orientado a Objetos

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Classe Python](#classe-python)
2. [Herança ou Generalização / Polimorfismo](#herança-ou-generalização--polimorfismo)
3. [Abstração / Interface](#abstração--interface)
4. [Encapsulamento](#encapsulamento)

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

> [!NOTE]
> A orientação a objetos é baseada em 4 pilares:
> - Herança
> - Polimorfismo
> - Abstração
> - Encapsulamento

## Herança ou Generalização / Polimorfismo

> [!NOTE]
> O conceito de herança ou generalização é usado para evitar repetição de atributos e métodos em classes diferentes.
> Quando exitem duas ou mais classes, e elas possuem alguns atributos e/ou métodos em comum, cria-se uma classe que reúne esses atributos e métodos, que chamamos de **superclasse** ou **classe-pai**, e a partir dela, outras classes que vão "herdar" seus atributos e métodos, das quais chamamos de **subclasse** ou **classe-filha**. Daí o nome.

Para duas ou mais classes herdarem atributos e métodos de uma superclasse, vamos usar como exemplo duas classes chamadas **PessoaFisica** e **PessoaJuridica**, que vão herdar atributos e métodos da superclasse **Pessoa**:
~~~python
# superclasse
class Pessoa:
    # atributos
    def __init__(self, email, telefone):
        self.email = email
        self.telefone = telefone

    def exibir_dados(self):
        print(f"E-mail: {self.email}")
        print(f"Telefone: {self.telefone}")

# subclasses
class PessoaFisica(Pessoa):
    # atributos novos e herança
    def __init__(self, nome, cpf, email, telefone):
        self.nome = nome
        self.cpf = cpf
        super.__init__(email=email,telefone=telefone)

    def exibir_dados(self):
        print(f"Nome: {self.nome}")
        print(f"CPF: {self.cpf}")
        super.exibir_dados()

class PessoaJuridica(Pessoa):
    def __init__(self, nome_fantasia, cnpj, email, telefone):
        self.nome_fantasia = nome_fantasia
        self.cnpj = cnpj
        super.__init__(email=email,telefone=telefone)

    def exibir_dados(self):
        print(f"Nome da empresa: {self.nome_fantasia}")
        print(f"CNPJ: {self.cnpj}")
        super.exibir_dados()

# função principal
def main():
    usuario = PessoaFisica(nome="",cpf="",email="",telefone="")
    empresa = PessoaFisica(nome_fantasia="",cnpj="",email="",telefone="")

    usuario.nome = input("Informe o nome do usuário: ").strip().title()
    usuario.cpf = input("Informe o CPF: ").strip()
    usuario.email = input("Informe o e-mail do usuário: ").strip().lower()
    usuario.telefone = input("Informe o telefone do usuário: ").strip()

    empresa.nome_fantasia = input("Informe o nome da empresa: ").strip()
    empresa.cnpj = input("Informe o CNPJ: ").strip()
    empresa.email = input("Informe o e-mail da empresa: ").strip().lower()
    empresa.telefone = input("Informe o telefone da empresa: ").strip()

    usuario.exibir_dados()
    print("\n")
    empresa.exibir_dados()

# execução do programa
if __name__ == "__main__":
    main()
~~~

> [!NOTE]
> Repare que mesmo herdando o mesmo método `exibir_dados()`, as classes `PessoaFisica` e `PessoaJuriica` exibem comportamentos diferentes neste mesmo método. Isso se chama **Polimorfismo**, que consiste em um mesmo método adotar comportamentos diferentes em classes diferentes.

## Abstração / Interface

> [!NOTE]
> - **Abstração** é esconder os detalhes de algo que consideramos desnecessário. Em orientação a objetos, isso se resume a criar o que chamamos de **classe abstrata**.
> - **Interface**, em orientação a objetos, funciona como uma espécie de "contrato" que uma classe deve obedecer para que possa funcionar dentro do programa. Caso ela não obedeça todas as "cláusulas" desse contrato, ela não poderá ser instanciada, nem herdada. Em outras palavras: perde a utilidade para o algoritmo.
> - Enquanto em outras linguagens de programação, como o Java e o PHP, esses dois conceitos são diferentes, em Python, eles são **exatamente a mesma coisa**, já que a interface é criada a partir de uma classe abstrata.

Para criar uma classe abstrata/interface, vamos usar como exemplo uma classe chamada `Conta`, onde será aplicada uma interface que a obrigará a realizar os métodos: `consultar_dados`, `depositar` e `sacar`:
~~~python
# importa biblioteca ABC e abstract method
from abc import ABC, abstractmethod

# classe abstrata/interface
class IConta(ABC):
    @abstractmethod
    def consultar_dados():
        pass

    @abstractmethod
    def depositar(valor):
        pass

    @abstractmethod
    def sacar(valor):
        pass

# classe onde será aplicada a interface através de herança
class Conta(IConta):
    def __init__(self, titular, agencia, n_conta, saldo):
        self.titular = titular
        self.agencia = agencia
        self.n_conta - n_conta
        self.saldo = saldo

    def consultar_dados():
        print(f"Titular da conta: {self.titular}")
        print(f"Agência: {self.agencia}")
        print(f"Número da conta: {self.n_conta}")
        print(f"Saldo: R$ {self.titular:.2f}")

    def depositar(valor):
        self.saldo += valor
        return self.saldo

    def sacar(valor):
        self.saldo -= valor if self.saldo >= valor else 0
        return self.saldo

# função principal
def main():
    # instancia a classe Conta
    cc = Conta(titular="",agencia="",n_conta="",saldo=0.0)

    # TODO: restante do algoritmo que vai fazer operações com a conta

# execução
if __name__ == "__main__":
    main()
~~~

## Encapsulamento

<!-- TODO -->
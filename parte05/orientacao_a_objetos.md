# Python Orientado a Objetos

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Classe Python](#classe-python)
2. [Herança ou Generalização / Polimorfismo](#herança-ou-generalização--polimorfismo)
3. [Abstração / Interface](#abstração--interface)
4. [Encapsulamento](#encapsulamento)
5. [Herança múltipla](#herança-múltipla)
6. [Relações entre classes](#relações-entre-classes)<br>
    6.1 [Associação](#associação)<br>
    6.2 [Composição](#composição)<br>
    6.3 [Agregação](#agregação)<br>
    6.4 [Depedência](#depedência)<br>
7. [Métodos Especiais](#métodos-especiais)<br>
8. [Dataclasses](#dataclasses)

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

> [!IMPORTANT]
> Em orientação a objetos, **encapsulamento** significa tratar a visibilidade dos elementos da classe, de forma que quem estiver utilizando não tenha que conhecer mais do que o necessário para utilizá-lo.
> Em muitos casos, isso significa tratar os atributos da classe como ***private***, para que o algoritmo principal não consiga acessar diretamente esses elementos, deixando-os dessa forma, protegidos.
> O acesso a eles deve ocorrer de forma indireta, a fim de proteger a integridade dos dados. Esse acesso é feito atráves dos métodos ***get*** e ***set***.

> [!NOTE]
> O encapsulamento pode ser explicado no exemplo abaixo:
> - `self.nome`: atributo ***public*** ou **público**
> - `self._nome`: atributo ***protected*** ou **protegido**, um *underscore* (`_`)
> - `self.__nome`: atributo ***private*** ou **privado**, dois *underscores* (`__`)

Exemplo de classe encapsulada, e como ocorre o acesso a seus atributos:
~~~python
# classe
class Pessoa:
    def __init__(self, nome):
        # atributo private
        self.__nome = nome

    # método get
    @property
    def nome(self):
        return self.__nome

    # método set
    @nome.setter
    def nome(self, nome):
        self.__nome = nome

# função principal
def main():
    # instancia do objeto
    usuario = Pessoa(nome="")

    # setando o valor
    usuario.nome = input("Informe o nome: ").strip().title()

    # exibindo o atributo
    print(f"O nome do usuário é: {usuario.nome}.")

# execução
if __name__ == "__main__":
    main()
~~~

## Herança múltipla

> [!NOTE]
> Herança Múltipla é quando uma classe herda atributos e métodos de duas ou mais superclasses.
> Só existem duas linguagens de programação orientadas a objeto que possuem recurso para herança múltipla: C++ e Python.

Exemplo de herança múltipla:
~~~python
# primeira superclasse
class Pai:
    def __init__(self, nome, cpf, email, profissao):
        self.__nome = nome
        self.__cpf = cpf
        self.__email = email
        self.__profissao = profissao

    @property
    def nome(self):
        return self.__nome

    @nome.setter
    def nome(self, nome):
        self.__nome = nome

    @property
    def cpf(self):
        return self.__cpf

    @cpf.setter
    def cpf(self, cpf):
        self.__cpf = cpf

    @property
    def email(self):
        return self.__email

    @email.setter
    def email(self, email):
        self.__email = email

    @property
    def profissao(self):
        return self.__profissao

    @profissao.setter
    def profissao(self, profissao):
        self.__profissao = profissao

    def cumprimentar(self):
        return f"Sou {self.__nome}, meu CPF é {self.__cpf}, meu e-mail é {self.__email} e trabalho como {self.__profissao}."

# segunda superclasse
class Mae:
    def __init__(self, olhos, peso, altura, tipo_sanguineo):
        self.__olhos = olhos
        self.__peso = peso
        self.__altura = altura
        self.__tipo_sanguineo = tipo_sanguineo

    @property
    def olhos(self):
        return self.__olhos

    @olhos.setter
    def olhos(self, olhos):
        self.__olhos = olhos

    @property
    def peso(self):
        return self.__peso

    @peso.setter
    def peso(self, peso):
        self.__peso = peso

    @property
    def altura(self):
        return self.__altura

    @altura.setter
    def altura(self, altura):
        self.__altura = altura

    @property
    def tipo_sanguineo(self):
        return self.__tipo_sanguineo

    @tipo_sanguineo.setter
    def tipo_sanguineo(self, tipo_sanguineo):
        self.__tipo_sanguineo = tipo_sanguineo

    def mostrar_fisico(self):
        return f"Tenho olhos {self.__olhos}, {self.__peso} kg, {self.__altura} m de altura, sangue é {self.__tipo_sanguineo}."

# subclasse aplicando o conceito de herança múltipla
class Filho(Pai, Mae):
    def __init__(self, nome, cpf, email, profissao, olhos, peso, altura, tipo_sanguineo):
        Pai.__init__(self, nome, cpf, email, profissao)
        Mae.__init__(self, olhos, peso, altura, tipo_sanguineo)

# função principal
def main():
    # instancia o objeto da subclasse
    filho = Filho("", "", "", "", "", 0.0, 0.0, "")

    # setando os valores
    filho.nome = "Júnior"
    filho.cpf = "754.785.470-26"
    filho.email = "junior@gmail.com"
    filho.profissao = "Programador"
    filho.olhos = "Verdes"
    filho.peso = 85.0
    filho.altura = 1.81
    filho.tipo_sanguineo = "A+"

    # executando os métodos
    print(filho.cumprimentar())
    print(filho.mostrar_fisico())

# execução
if __name__ == "__main__":
    main()
~~~

## Relações entre classes

### Associação

> [!NOTE]
> Na associação, as classes possuem relação entre si, mas podem existir de forma independente uma da outra.

Exemplo de associação entre uma classe `Endereco` e `Pessoa`:
~~~python
class Endereco:
    def __init__(self, rua, cidade):
        self.__rua = rua
        self.__cidade = cidade

    def obter_endereco(self):
        return f"{self.__rua}, {self.__cidade}"


class Pessoa:
    def __init__(self, nome, endereco):
        self.__nome = nome
        self.__endereco = endereco   # associação

    def apresentar(self):
        print(f"Nome: {self.__nome}")
        print(f"Endereço: {self.__endereco.obter_endereco()}")

    def trocar_endereco(self, novo_endereco):
        self.__endereco = novo_endereco


# criando os objetos
def main():
    endereco1 = Endereco("Rua das Flores", "Campinas")
    pessoa = Pessoa("Maria", endereco1)

    pessoa.apresentar()

    # mudando o endereço
    novo_endereco = Endereco("Av. Brasil", 100)
    pessoa.trocar_endereco(novo_endereco)

    print("\nDepois da troca:")
    pessoa.apresentar()

if __name__ == "__main__":
    main()
~~~

### Composição

> [!NOTE]
> Na composição, obrigatoriamente um dos atributos de uma classe é um objeto de outra classe. Nesse caso, há uma dependência de uma das classes em relação à outra.
> Uma classe possui outra classe como parte essencial dela. Se o objeto principal for destruído, o objeto da outra classe também perde sentido.

Exemplo de composição entre as classes `Motor` e `Carro`:
~~~python
class Motor:
    def __init__(self, potencia):
        self.__potencia = potencia

    def info(self):
        return f"Motor de {self.__potencia} cv"


class Carro:
    def __init__(self, modelo, potencia):
        self.__modelo = modelo
        self.__motor = Motor(potencia)  # composição

    def detalhes(self):
        return f"Carro: {self.__modelo} | {self.__motor.info()}"

def main():
    carro = Carro("Gol", 120)
    print(carro.detalhes())

if __name__ == "__main__":
    main()
~~~

## Agregação

> [!NOTE]
> Na agregação, uma classe possui outra classe, mas essa outra classe pode existir independentemente.

Exemplo de agregação entre as classes `Departamento` e `Empresa`:
~~~python
class Departamento:
    def __init__(self, nome):
        self.__nome = nome

    def get_nome(self):
        return self.__nome


class Empresa:
    def __init__(self, nome, departamento):
        self.__nome = nome
        self.__departamento = departamento

    def detalhes(self):
        return f"Empresa: {self.__nome} | Departamento: {self.__departamento.get_nome()}"


def main():
    departamento = Departamento("TI")
    empresa = Empresa("Acme", departamento)

    print(empresa.detalhes())

if __main__ == "__main__":
    main()
~~~

### Depedência

> [!NOTE]
> Na dependência, uma classe utiliza outra classe temporariamente, mas não a mantém como atributo principal.

Exemplo de dependência entre as classes `Calculadora` e `Pedido`:
~~~python
class Calculadora:
    def somar(self, a, b):
        return a + b


class Pedido:
    def __init__(self, valor1, valor2):
        self.__valor1 = valor1
        self.__valor2 = valor2

    def calcular_total(self):
        calc = Calculadora()
        return calc.somar(self.__valor1, self.__valor2)

def main():
    pedido = Pedido(10, 20)
    print(pedido.calcular_total())

if __name__ == "__main__":
    main()
~~~

## Métodos Especiais

> [!NOTE]
> Os métodos especiais em Python, também conhecidos como **métodos mágicos** ou ***Dunder***, são métodos que definem o comportamento de classes e objetos, sendo invocados automaticamente sob circunstâncias especiais, o que ajuda a diminuir o tempo de execução do código. Normalmente não são chamados diretamente pelo usuário mas podem ser overloaded (sobrescritos e alterados). Eles são identificados por nomes que começam e terminam com dois sublinhados (`__`).

Exemplos de métodos especiais:
- `__init__`: É o construtor da classe, que declara os atributos da classe.
- `__str__`: Define como o objeto deve ser representado como uma string.
- `__repr__`: Representa o objeto como uma string que pode ser usada para criar um novo objeto com os mesmos valores.
- `__eq__`: Verifica se dois objetos são iguais.
- `__lt__`: Determina se um objeto é menor que outro.
- `__call__`: É invocado quando o objeto é invocado como função.
- `__float__`: Determina o comportamento da classe quando a instância é usada como o tipo *float*.
- `__len__`: permite que a função `len()` seja chamada em objetos da classe. Geralmente, retorna o comprimento do objeto. *Obs:* ela trabalha apenas com valores *int*.
- `__del__`: chamado quando um objeto está prestes a ser destruído (quando não há mais referências a ele). É útil para realizar qualquer limpeza necessária.
- `__add__`: sobrecarrega o operador `+`.
- `__getitem__`: utilizado para indexação.

Exemplo de `__str__`:
~~~python
class Pessoa:
    def __init__(self, nome):
        self.nome = nome

    def __str__(self):
        return self.nome

def main():
    usuario = Pessoa("Alex")
    print(usuario)
~~~

Exemplo de `__len__`:
~~~python
class Pessoa:
    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade

    def __str__(self):
        return self.nome

    def __len__(self):
        return self.idade

def main():
    usuario = Pessoa("Alex", 41)
    print(f"Nome: {usuario}")
    print(f"Idade: {len(usuario)}")
~~~

Exemplo de `__del__`:
~~~python
class Pessoa:
    def __init__(self, nome):
        self.nome = nome

    def __str__(self):
        return self.nome

    def __del__(self):
        print(f"Objeto {self} destruído com sucesso.")

def main():
    usuario = Pessoa("Alex")
    print(usuario)
    del(usuario)

if __name__ == "__main__":
    main()
~~~

> [!NOTE]
> As classes Python possuem mais de 100 métodos especiais. Só estão sendo citadas aqui as mais comuns.

## Dataclasses

As dataclasses são uma forma simplificada de criar classes que armazenam dados, proporcionando uma maneira fácil e rápida de implementar classes com atributos e métodos específicos para manipulação de dados.

Exemplo:
~~~python
# importando o dataclass
from dataclasses import dataclass

# classe Pessoa
@dataclass
class Pessoa:
    # atributos
    nome: str
    idade: int
    altura: float

    def __str__(self):
        return self.nome

    def __len__(self):
        return self.idade

    def __float__(self):
        return float(self.altura)

    def __del__(self):
        print(f"Objeto {self} destruído com sucesso.")

def main():
    usuario = Pessoa(nome="Alex",idade=41,altura=1.72)

    print(f"Nome: {usuario}.")
    print(f"Idade: {len(usuario)}.")
    print(f"Altura: {float(usuario)} metros.")

    del(usuario)

if __name__ == "__main__":
    main()
~~~

---

- [Voltar ao início](#sumário)
- [Voltar ao índice do Guia Rápido de Python](https://github.com/dev-alexmachado/guia_rapido_python)
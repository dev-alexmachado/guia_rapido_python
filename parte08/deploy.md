# Deploy

[Clique aqui para retornar](https://github.com/dev-alexmachado/guia_rapido_python)

## Sumário

1. [Definição de Deploy](#definição-de-deploy)<br>
    1.1 [O Ciclo de Vida de uma Aplicação Web](#o-ciclo-de-vida-de-uma-aplicação-web)<br>
    1.2 [Para uma Aplicação Flask/Django (Python)](#para-uma-aplicação-flaskdjango-python)<br>
2. [Fazendo Deploy](#fazendo-deploy)<br>
    2.1 [Deploy no Render (Gratuito)](#deploy-no-render-gratuito)<br>
    2.2 [Vantagens do Deploy Gratuito no Render](#vantagens-do-deploy-gratuito-no-render)<br>
    2.3 [Desvantagens do Deploy Gratuito no Render](#desvantagens-do-deploy-gratuito-no-render)<br>
3. [Próximos Passos](#próximos-passos)


## Definição de Deploy

> [!NOTE]
> **Deploy** (do inglês "implantação") é o processo de colocar sua aplicação em um servidor público, na internet, para que outras pessoas possam acessá-la.
> Quando faz deploy, você está dizendo: "Meu site está pronto para ser usado por qualquer pessoa no mundo!"

### O Ciclo de Vida de uma Aplicação Web

~~~mermaid
graph TD
    %% Etapas de Desenvolvimento (Linha Superior)
    A[Local Development] --> B[Testing]
    B --> C[Staging]
    C --> D[Production DEPLOY]

    %% Conexões Verticais (Processo -> Ambiente)
    A --> E[Seu Computador]
    B --> F[Ambiente de Teste]
    C --> G[Servidor de Testes]
    D --> H[Servidor Público]

    %% Fluxo dos Ambientes (Linha Inferior)
    E --> F
    F --> G
    G --> H

    %% Estilização para destacar o Deploy final
    style D fill:#00f,stroke:#333,stroke-width:2px
    style H fill:#00f,stroke:#333,stroke-width:2px

~~~

### Para uma Aplicação Flask/Django (Python)

~~~mermaid
graph TD
    A[Seu código] --> B[Repositório Git GitHub]
    B --> C[Servidor]
    C --> D[Deploy automático]

    %% Estilização para destacar o resultado final
    style D fill:#660,stroke:#333,stroke-width:2px

~~~

> [!IMPORTANT]
> **Diferenças Importantes:**<br>
> - **Localhost (Local)**: Só você consegue acessar → **http://localhost:5000**
> - **Deploy (Produção)**: Qualquer pessoa acessa → **https://meusite.com**

## Fazendo Deploy

### Deploy no Render (Gratuito)

O **Render** é uma plataforma moderna de hospedagem que oferece um plano gratuito excelente para iniciantes. Vamos aprender como fazer deploy de aplicações Flask e Django.

#### Pré-requisitos

Antes de começar, certifique-se de ter:

1. **Conta no GitHub** com seu repositório
2. **Conta no Render** (gratuita) → [render.com](https://render.com)
3. **Arquivo `requirements.txt`** com todas as dependências
4. **Arquivo `.venv`** (localmente, não commitado no Git)
5. Instalação da biblioteca `gunicorn` no seu projeto.

> [!IMPORTANT]
> Para instalar o `gunicorn`:
~~~
pip install gunicorn
~~~

#### Deploy de Aplicação Flask

##### Passo 1: Preparar o Projeto Flask

Sua estrutura de projeto deve ser assim:

```
meu_projeto_flask/
├── app.py                 # Arquivo principal (IMPORTANTE!)
├── requirements.txt       # Dependências
├── .gitignore            # Não commitar .env e __pycache__
├── .venv                  # Variáveis de ambiente (local apenas)
└── templates/            # Pasta com HTML (opcional)
```

**Arquivo `app.py` de exemplo:**

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Olá! Meu deploy está funcionando! 🚀'

if __name__ == '__main__':
    # Importante: usar variável de ambiente PORT do Render
    import os
    port = int(os.environ.get('PORT', 5000))
    app.run(host='0.0.0.0', port=port, debug=False)
```

**Arquivo `requirements.txt`:**

```
Flask==2.3.0
gunicorn==21.2.0
python-dotenv==1.0.0
```

##### Passo 2: Criar arquivo `render.yaml`

Na raiz do projeto, crie o arquivo `render.yaml`:

```yaml
services:
  - type: web
    name: meu-app-flask
    runtime: python311
    buildCommand: pip install -r requirements.txt
    startCommand: gunicorn app:app
    envVars:
      - key: PYTHON_VERSION
        value: 3.11
```

##### Passo 3: Fazer Push no GitHub

```bash
git add .
git commit -m "Preparando para deploy no Render"
git push origin main
```

##### Passo 4: Conectar Render ao GitHub

1. Acesse [render.com](https://render.com)
2. Clique em **"New Web Service"**
3. Selecione **"Connect a repository"**
4. Autorize o Render a acessar seus repositórios do GitHub
5. Selecione o repositório com seu projeto Flask
6. Configure:
   - **Name**: Nome da sua aplicação
   - **Runtime**: Python 3.11
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `gunicorn app:app`
   - **Instance Type**: Free (gratuito)
7. Clique em **"Create Web Service"**

##### Passo 5: Esperar Deploy Completar

O Render fará o deploy automaticamente. Você verá um link como: `https://seu-app-flask.onrender.com`

---

#### Deploy de Aplicação Django

##### Passo 1: Preparar o Projeto Django

Sua estrutura de projeto deve ser assim:

```
meu_projeto_django/
├── manage.py
├── meusite/              # Pasta do projeto Django
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── requirements.txt
├── .gitignore
├── .venv                  # Variáveis de ambiente (local apenas)
└── Procfile             # Instruções para Render
```

##### Passo 2: Modificar `settings.py` do Django

No arquivo `meusite/settings.py`, faça as seguintes alterações:

```python
import os
from pathlib import Path
from dotenv import load_dotenv

load_dotenv()

# ... resto do código ...

# Hosts permitidos (importante para produção!)
ALLOWED_HOSTS = ['localhost', '127.0.0.1', '*.onrender.com']

# Desabilitar DEBUG em produção
DEBUG = os.environ.get('DEBUG', 'False') == 'True'

# Key secreta do Django
SECRET_KEY = os.environ.get('SECRET_KEY', 'sua-chave-secreta-temporaria')

# Configuração de banco de dados (exemplo com PostgreSQL gratuito)
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': os.environ.get('DB_NAME'),
        'USER': os.environ.get('DB_USER'),
        'PASSWORD': os.environ.get('DB_PASSWORD'),
        'HOST': os.environ.get('DB_HOST'),
        'PORT': os.environ.get('DB_PORT', '5432'),
    }
}

# Diretório de arquivos estáticos
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')
```

##### Passo 3: Criar arquivo `requirements.txt`

```
Django==4.2.0
gunicorn==21.2.0
psycopg2-binary==2.9.0
python-dotenv==1.0.0
whitenoise==6.4.0
```

##### Passo 4: Criar arquivo `Procfile`

Na raiz do projeto, crie o arquivo `Procfile`:

```
web: gunicorn meusite.wsgi:application
release: python manage.py migrate
```

Este arquivo instrui o Render a:
- Iniciar a aplicação com Gunicorn
- Rodar migrações do banco de dados antes de iniciar

##### Passo 5: Modificar `wsgi.py`

Seu arquivo `meusite/wsgi.py` deve estar assim:

```python
import os
from django.core.wsgi import get_wsgi_application
from whitenoise.django import DjangoWhiteNoise

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'meusite.settings')

application = get_wsgi_application()
application = DjangoWhiteNoise(application)
```

##### Passo 6: Fazer Push no GitHub

```bash
git add .
git commit -m "Preparando Django para deploy no Render"
git push origin main
```

##### Passo 7: Conectar Render ao GitHub

1. Acesse [render.com](https://render.com)
2. Clique em **"New Web Service"**
3. Selecione **"Connect a repository"**
4. Selecione seu repositório Django
5. Configure:
   - **Name**: Nome da sua aplicação
   - **Runtime**: Python 3.11
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `gunicorn meusite.wsgi:application`
6. Clique em **"Advanced"** e adicione variáveis de ambiente:
   - `PYTHON_VERSION`: `3.11`
   - `DEBUG`: `False`
   - `SECRET_KEY`: (gere uma chave forte)
   - Credenciais do banco de dados (se usar PostgreSQL)

7. Clique em **"Create Web Service"**

---

### Vantagens do Deploy Gratuito no Render

✅ **Sem custo financeiro** - Ideal para protótipos e aprendizado

✅ **Deploy automático** - Atualiza automaticamente ao fazer push no GitHub

✅ **HTTPS grátis** - Certificado SSL incluído

✅ **Fácil de usar** - Interface intuitiva, sem necessidade de comandos complexos

✅ **Suporte a PostgreSQL gratuito** - Banco de dados relacional incluído

✅ **Renovação automática** - Horário de renovação gratuita permitido

✅ **Variáveis de ambiente** - Segurança para dados sensíveis

---

### Desvantagens do Deploy Gratuito no Render

❌ **Limitações de performance** - Processador e memória limitados

❌ **Sleep mode** - Se não receber requisições por 15 minutos, a aplicação "dorme" e demora para acordar

❌ **Limite de banda** - Não é adequado para aplicações com muito tráfego

❌ **Sem escalabilidade automática** - Não cresce automaticamente com demanda

❌ **Armazenamento temporário** - Dados salvos no servidor são perdidos a cada deploy

❌ **Sem suporte direto** - Suporte comunitário apenas (não profissional)

❌ **Limite de projetos** - Quantidade limitada de serviços gratuitos por conta

---

### Quando Usar Deploy Gratuito no Render

| Situação | Adequado? |
|----------|-----------|
| **Portfólio/Projetos Pessoais** | ✅ Sim |
| **Aprendizado e Prototipagem** | ✅ Sim |
| **Aplicação em Produção com Muito Tráfego** | ❌ Não |
| **Aplicação Crítica que Não Pode Ficar Offline** | ❌ Não |
| **Projetos Comerciais** | ⚠️ Talvez (comece gratuitamente) |

---

## Próximos Passos

Após fazer seu primeiro deploy no Render:

1. **Teste sua aplicação** → Acesse o link fornecido pelo Render
2. **Configure domínio próprio** → Aponte seu domínio para o Render
3. **Implemente CI/CD** → Automatize testes antes de deploy
4. **Monitore erros** → Use logs do Render para debugging
5. **Escale quando necessário** → Migre para plano pago se crescer

---

- [Voltar ao início](#sumário)
- [Voltar ao índice do Guia Rápido de Python](https://github.com/dev-alexmachado/guia_rapido_python)
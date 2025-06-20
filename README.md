# 🚀 Simulador de Orçamento Pessoal - Vibe 🖤

Um aplicativo desktop moderno e intuitivo para ajudar você a gerenciar suas finanças pessoais e acompanhar suas pequenas metas. Desenvolvido com tecnologias de ponta, oferece uma experiência de usuário fluida e visualmente atraente.

---

## ✨ Funcionalidades

* **Registro Simplificado:** Adicione receitas e despesas com valor, descrição, categoria e tipo.
* **Resumo Financeiro:** Visualize seu saldo atual, receitas e despesas totais de forma clara.
* **Organização por Categoria:** Categorize suas transações para uma análise mais detalhada.
* **Gráficos Interativos:** Entenda a distribuição das suas despesas com gráficos de pizza intuitivos (com mais tipos de gráficos a caminho!).
* **Histórico Detalhado:** Acompanhe todas as suas transações em uma lista rolável e interativa, com opções de exclusão individual.
* **Gerenciamento de Transações:** Remova a última transação ou exclua transações específicas individualmente.
* **Limpeza de Dados:** Opção para zerar todos os seus registros e começar de novo.
* **Multi-Tecnologia:** Desenvolvido com um frontend em React (JavaScript) e um backend em Flask (Python) com banco de dados SQLite, tudo empacotado para desktop.

---

## 📦 Como Usar (Para Usuários Finais - Plug & Play no Windows!)

Se você só quer usar o aplicativo e gerenciar suas finanças sem se preocupar com código ou instalações complexas:

1.  **Baixe o Instalador:**
    * Vá para a seção **[Releases](https://github.com/SeuUsuario/NomeDoSeuRepositorio/releases)** deste repositório no GitHub.
    * Baixe o arquivo de instalação (`Simulador de Orçamento Vibe Setup 0.1.0.exe` ou a versão mais recente disponível).
2.  **Instale o Aplicativo:**
    * Execute o instalador baixado e siga as instruções na tela.
    * **Permissões:** Geralmente, a instalação e o uso em pastas pessoais não exigem permissões de administrador.
3.  **Comece a Gerenciar suas Finanças!**
    * O aplicativo criará automaticamente um arquivo de banco de dados (`dados_orcamento.db`) na pasta onde for instalado para salvar suas informações de forma segura.
    * **Dica:** Se você já testou o app em modo de desenvolvimento, é recomendável usar a opção "Limpar Todos os Dados" dentro do app ou, se for reinstalar, garantir que não há um arquivo `dados_orcamento.db` antigo na pasta de instalação para começar do zero.

---

## 🛠️ Como Desenvolver/Rodar o Código Fonte (Para Desenvolvedores)

Se você é um desenvolvedor e quer explorar o código-fonte, contribuir ou rodar o aplicativo diretamente:

Este projeto é uma aplicação **Full-Stack Desktop**, dividida em:
* **Frontend:** Construído com **React (JavaScript)**
* **Backend:** Construído com **Flask (Python)** e **SQLAlchemy** para interagir com o **SQLite** (banco de dados)
* **Empacotamento Desktop:** Realizado com **Electron** (para a interface desktop) e **PyInstaller** (para empacotar o backend Python).

### **Estrutura do Projeto:**

OrcamentoAppPro/
├── backend/                  # Código Python Flask e ambiente virtual
│   ├── venv_backend/         # Ambiente virtual (IGNORADO pelo Git)
│   ├── app.py                # Servidor Flask e lógica do DB
│   ├── dados_orcamento.db    # Banco de dados SQLite (IGNORADO pelo Git)
│   └── requirements.txt      # Dependências Python do Backend
└── frontend/                 # Código JavaScript React e ambiente Node.js
└── orcamento-frontend-ui/
├── node_modules/     # Módulos Node.js (IGNORADO pelo Git)
├── public/           # Arquivos públicos do React (HTML, etc.)
├── src/              # Seu código fonte React (.js, .jsx, .css)
├── main.js           # Script principal do Electron
├── preload.js        # Script de pré-carregamento do Electron
├── package.json      # Dependências e scripts do React/Electron
├── package-lock.json # Gerenciamento de versões das dependências JS (IGNORADO pelo Git)
└── .gitignore        # Arquivos e pastas a serem ignorados pelo Git no frontend
├── release/                  # Pasta onde o executável final (.exe) é gerado (IGNORADO pelo Git)
└── .gitattributes            # Configurações de atributos do Git
└── .gitignore                # Arquivos e pastas a serem ignorados pelo Git (raiz do projeto)


### **Pré-requisitos:**

Certifique-se de ter instalado em seu sistema:

* [**Python 3.x**](https://www.python.org/downloads/) (versão mais recente e estável)
* [**Node.js (versão LTS)**](https://nodejs.org/en/) (que inclui `npm`)

### **Instalação e Execução (Modo de Desenvolvimento):**

Para rodar o aplicativo em modo de desenvolvimento, você precisará de **três terminais ativos** simultaneamente:

####   **1. Backend (Python/Flask):**

1.  Navegue até a pasta `backend`:
    ```bash
    cd OrcamentoAppPro/backend
    ```
    (Use aspas duplas no caminho se houver espaços: `cd "C:\caminho\para\OrcamentoAppPro\backend"`)
2.  Ative o ambiente virtual:
    ```bash
    .\venv_backend\Scripts\activate   # No Windows (PowerShell/CMD)
    # source venv_backend/bin/activate # No Linux/macOS ou Git Bash
    ```
3.  Instale as dependências Python:
    ```bash
    pip install -r requirements.txt
    ```
4.  Crie as tabelas do banco de dados (rode uma única vez para inicializar o DB):
    * No navegador, acesse: `http://localhost:5000/init_db`
5.  Inicie o servidor Flask:
    ```bash
    flask run
    ```
    Mantenha este terminal ativo.

####   **2. Frontend (JavaScript/React):**

1.  Abra um **NOVO TERMINAL** e navegue até a pasta `frontend/orcamento-frontend-ui`:
    ```bash
    cd OrcamentoAppPro/frontend/orcamento-frontend-ui
    ```
    (Use aspas duplas no caminho se houver espaços)
2.  Instale as dependências JavaScript:
    ```bash
    npm install
    ```
3.  Inicie o servidor de desenvolvimento do React:
    ```bash
    npm start
    ```
    Mantenha este terminal ativo. O app deve abrir no seu navegador em `http://localhost:3000`.

####   **3. Aplicativo Desktop (Electron Dev):**

1.  Abra um **TERCEIRO e NOVO TERMINAL** e navegue até a pasta `frontend/orcamento-frontend-ui`:
    ```bash
    cd OrcamentoAppPro/frontend/orcamento-frontend-ui
    ```
    (Mesma pasta do terminal React)
2.  Inicie o Electron em modo de desenvolvimento:
    ```bash
    npm run electron-dev
    ```
    Uma janela de aplicativo desktop deve se abrir, exibindo sua interface.

### **Como Empacotar para Produção (.exe):**

Para gerar o instalador `.exe` para Windows:

1.  **Certifique-se de que o backend Python está empacotado:**
    * No terminal do `backend` (com `venv_backend` ativo), rode:
        ```bash
        python -m PyInstaller --onedir app.py
        ```
        Isso criará a pasta `dist/app` dentro de `OrcamentoAppPro/backend/`.
2.  **Compile o Frontend React:**
    * No terminal do `frontend` (`orcamento-frontend-ui`), rode:
        ```bash
        npm run build
        ```
        Isso criará a pasta `build` dentro de `OrcamentoAppPro/frontend/orcamento-frontend-ui/`.
3.  **Gere o instalador com Electron Builder:**
    * No terminal do `frontend` (`orcamento-frontend-ui`), rode:
        ```bash
        npm run dist
        ```
    * O instalador `.exe` será criado na pasta `OrcamentoAppPro/release/`.

---

## 📚 Bibliotecas e Tecnologias Utilizadas

* **Frontend:**
    * [**React**](https://react.dev/): Biblioteca JavaScript para construção da interface de usuário.
    * [**Axios**](https://axios-http.com/): Cliente HTTP baseado em Promises para comunicação com a API.
    * [**Chart.js**](https://www.chartjs.org/) & [**react-chartjs-2**](https://react-chartjs-2.js.org/): Para visualização de dados (gráficos interativos).
* **Backend:**
    * [**Flask**](https://flask.palletsprojects.com/): Microframework web em Python para a API REST.
    * [**Flask-SQLAlchemy**](https://flask-sqlalchemy.palletsprojects.com/): Extensão para integrar SQLAlchemy (ORM) com Flask, facilitando a interação com o banco de dados.
    * [**SQLAlchemy**](https://www.sqlalchemy.org/): Toolkit SQL e Mapeador Objeto-Relacional (ORM) para Python.
    * [**SQLite**](https://www.sqlite.org/): Banco de dados leve e autônomo, perfeito para aplicações desktop e pequenas bases de dados.
    * [**Flask-CORS**](https://flask-cors.readthedocs.io/en/latest/): Extensão Flask para habilitar o Cross-Origin Resource Sharing (CORS).
* **Empacotamento Desktop:**
    * [**Electron**](https://www.electronjs.org/): Framework para construir aplicativos de desktop com tecnologias web.
    * [**Electron Builder**](https://www.electron.build/): Ferramenta completa para empacotar e distribuir aplicativos Electron.
    * [**PyInstaller**](https://pyinstaller.org/): Ferramenta para empacotar aplicativos Python em executáveis autônomos.

---

## ⬇️ Download do Projeto Completo (Código e Dependências)

Para ter acesso a todos os arquivos do projeto, incluindo as pastas de dependências (`node_modules`, `venv_backend`, etc.) e os resultados da compilação, você pode baixar o pacote completo aqui:

* **[Download do Projeto Completo](https://drive.google.com/drive/folders/1DSkwakbr97RamUkOjeAS5Z9v7xkTHIju?usp=sharing)**

código por **Meloww**

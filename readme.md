# STRIDE Threat Model Analyzer
Este projeto oferece uma solução completa para análise de ameaças usando a metodologia STRIDE. A aplicação é dividida em um backend em FastAPI e um front-end em HTML/CSS/JS, que visualiza as ameaças de forma interativa com o Cytoscape.js.

Recursos
Análise Automática: Gere modelos de ameaças STRIDE de forma automática usando a Azure OpenAI a partir de uma imagem e descrição da arquitetura do seu sistema.

Visualização Interativa: Explore o modelo de ameaças em um grafo dinâmico e interativo.

Sugestões de Melhoria: Receba sugestões para aprimorar o modelo de ameaças.

Exportação: Exporte a visualização do grafo como uma imagem.

Como Executar o Projeto
Siga estes passos para colocar o projeto no ar.

1. Pré-requisitos
Certifique-se de que você tem o seguinte instalado:

Python 3.10+

Node.js (opcional, apenas para servir o front-end com npx serve)

Uma conta e um deployment configurado na Azure OpenAI. Você precisará da sua chave de API, endpoint e nome do deployment.

2. Configurando o Backend (FastAPI)
Acesse a pasta do backend no terminal:

Bash

cd module-1/01-introducao-backend
Crie e ative um ambiente virtual (recomendado):

Windows: python -m venv .venv e depois .venv\Scripts\activate

Linux/Mac: python3 -m venv .venv e depois source .venv/bin/activate

Instale as dependências:

Bash

pip install -r requirements.txt
Crie um arquivo .env na mesma pasta e preencha-o com suas credenciais da Azure OpenAI:

Snippet de código

AZURE_OPENAI_API_KEY=sua_chave_de_api
AZURE_OPENAI_ENDPOINT=seu_endpoint
AZURE_OPENAI_API_VERSION=2023-05-15
AZURE_OPENAI_DEPLOYMENT_NAME=nome_do_seu_deployment
Inicie o servidor:

Bash

uvicorn main:app --reload --host 0.0.0.0 --port 8001
O backend estará rodando em http://localhost:8001.

3. Configurando o Front-end
Acesse a pasta do front-end:

Bash

cd ../02-front-end
Abra o arquivo index.html diretamente no seu navegador.

Se preferir usar um servidor web local (opcional):

Com Node.js:

Bash

npx serve .
Com Python:

Bash

python -m http.server 8080
O front-end está configurado para se conectar ao backend em http://localhost:8001.

Dicas Importantes
Credenciais: Certifique-se de que as informações no seu arquivo .env estão corretas e que seu deployment na Azure OpenAI está ativo.

CORS: O backend já vem com as configurações de CORS para aceitar requisições de qualquer origem, mas para um ambiente de produção, ajuste-o para permitir apenas origens específicas.

Limites: O modelo da Azure OpenAI tem limites de tokens. Se precisar, ajuste o parâmetro max_tokens na sua aplicação.

Portas: Verifique se as portas 8001 (backend) e 8080 (se usar o servidor do Python) estão livres.

Estrutura do Projeto
stride-demo/
├── module-1/
│ ├── 01-introducao-backend/
│ │ ├── main.py
│ │ ├── requirements.txt
│ │ └── .env (crie este arquivo)
│ └── 02-front-end/
│ └── index.html
└── README.md

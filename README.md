# Guia Turístico Inteligente com IA
## 🚀 Visão Geral do Projeto
Este projeto é um sistema de guia turístico inteligente, construído com Inteligência Artificial. O objetivo é fornecer respostas rápidas e personalizadas para turistas, usando uma arquitetura modular que classifica a intenção de cada pergunta e a direciona para a ferramenta mais adequada.

## 🏗️ Arquitetura e Fluxo
A solução foi desenvolvida com uma arquitetura robusta e escalável, seguindo o padrão RAG (Retrieval-Augmented Generation) orquestrado por um Router Chain.

```shell
    A[Usuário Faz uma Pergunta] --> B(Router Chain);
    B -->|Classifica como 'roteiro'| C[Itinerary Chain];
    B -->|Classifica como 'info-local'| D[Local Info Chain];
    B -->|Classifica como 'logistica'| E[Logistics Chain];
    B -->|Classifica como 'traducao'| F[Translation Chain];
    C --> G(RAG - Pinecone);
    D --> G;
    G --> H[LLM (Groq) com Contexto];
    E --> H;
    F --> H;
    H --> I[Resposta Final ao Usuário];
```

## 🎯 Principais Funcionalidades
- Roteador Inteligente: Classifica a intenção do usuário (roteiro, logistica, informacao local, traducao) com alta precisão.

- Geração Aumentada (RAG): Busca informações específicas sobre as cidades em uma base de dados externa (Pinecone), garantindo respostas precisas e atualizadas.

- Cadeias Especializadas: Cada tipo de pergunta é processado por uma cadeia de IA otimizada para a tarefa.

- Alta Performance: Utiliza o LLM llama-3.1-8b-instant da Groq para respostas rápidas.

## 🛠️ Tecnologias Utilizadas
- 🦜 LangChain: Framework principal para orquestração da lógica e das cadeias de IA.

- ⚡ Groq: LLM de alta performance para inferência e geração de texto (llama-3.1-8b-instant).

- 📊 Pinecone: Banco de dados vetorial para armazenar os dados turísticos e habilitar o RAG.

- 🤗 HuggingFace: Modelo de Embeddings (all-MiniLM-L6-v2) gratuito e de código aberto.

- 🐍 Jupyter Notebooks: Para o desenvolvimento modular e demonstração do projeto.

## 📁 Estrutura do Projeto
```shell
.
├── .env                  # Chaves de API
├── .gitignore
├── requirements.txt      # Dependências do projeto
├── Pinecone.ipynb     # Criação do índice no Pinecone
├── Rag.ipynb          # Popula o Pinecone com os dados
├── Chains.ipynb       # Testes unitários das cadeias
├── Router.ipynb       # Teste da lógica de roteamento
├── GuiaTuristico.ipynb   # Notebook principal e interface de chat
└── data/                 # Base de conhecimento para o RAG
    ├── nova_iorque.txt
    ├── paris.txt
    ├── ... (outras cidades)
```
## 🚀 Instalação e Uso
### 1. Clonar o Repositório
```shell
git clone https://github.com/Amanda-Falcao/Guia_Inteligente_Viagem.git
cd Guia_Inteligente_Viagem
```
### 2. Configurar o Ambiente
Crie um ambiente virtual com Conda e instale as dependências:
```shell
conda create --name guia_viagem python=3.10 -y
conda activate guia_viagem
pip install -r requirements.txt
```
### 3. Configurar Chaves de API
Crie um arquivo chamado .env na raiz do projeto e adicione suas chaves:
```shell
GROQ_API_KEY="SUA_CHAVE_GROQ"
PINECONE_API_KEY="SUA_CHAVE_PINECONE"
```
### 4. Executar os Notebooks
Execute os notebooks em ordem, do Pinecone a GuiaTuristico.ipynb, para configurar o sistema e iniciar a demonstração.
```shell
Pinecone.ipynb: Cria o índice no Pinecone.

Rag.ipynb: Indexa os dados da pasta data/.

Chains.ipynb: Testa as cadeias individualmente.

Router.ipynb: Testa o roteador.

GuiaTuristico.ipynb: Inicia a interface de chat interativo.
```

## 🧪 Exemplos de Consultas
Você pode testar o sistema com perguntas como:

- Roteiro: "Crie um roteiro cultural de 3 dias em Paris."

- Logística: "Qual a melhor forma de transporte em Tóquio?"

- Info Local: "Como chegar ao Coliseu?"

- Tradução: "Traduza a frase 'muito obrigado' para o italiano."

🎉 Divirta-se com seu Guia Turístico Inteligente! 🎉

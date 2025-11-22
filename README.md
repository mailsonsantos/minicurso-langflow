# Minicurso de Langflow

Bem-vindo ao minicurso de Langflow! Este repositório contém todo o material necessário para subir o ambiente e realizar os exercícios práticos.

## 🚀 Como subir o ambiente

Utilizaremos o Docker para facilitar a execução do Langflow. Certifique-se de ter o Docker e o Docker Compose instalados na sua máquina.

1.  Abra o terminal na pasta raiz deste projeto.
2.  Execute o seguinte comando para iniciar o Langflow:

    ```bash
    docker-compose up -d
    ```

3.  Aguarde alguns instantes e acesse o Langflow no seu navegador através do endereço:

    [http://localhost:7860](http://localhost:7860)

## 🔑 Criando sua chave na Groq

Para os exercícios, utilizaremos a Groq como provedor de modelos de linguagem (LLM) devido à sua velocidade e disponibilidade gratuita para testes.

1.  Acesse o console da Groq: [https://console.groq.com/keys](https://console.groq.com/keys)
2.  Faça login com sua conta (Google, GitHub, etc.).
3.  Clique em **"Create API Key"**.
4.  Dê um nome para sua chave (ex: `curso-langflow`).
5.  Copie a chave gerada (começa com `gsk_...`). **Guarde-a em um local seguro**, pois você precisará dela nos exercícios.

## 📚 Exercícios

Os exercícios estão divididos para evoluir seu conhecimento na ferramenta. Os arquivos JSON dos fluxos (quando aplicável) estarão na pasta `exercicios/`.

### 1. Hello World com Groq
*   **Arquivo**: [Exercicio_1.json](exercicios/Exercicio_1.json)
*   **Objetivo**: Criar seu primeiro fluxo simples.
*   **Componentes**: Chat Input -> Prompt -> Groq Model -> Chat Output.
*   **Tarefa**: Configure o modelo Groq com sua API Key e faça o modelo responder a um "Olá".

### 2. Hello World + Memory
*   **Arquivo**: [Exercicio_2.json](exercicios/Exercicio_2.json)
*   **Objetivo**: Adicionar memória ao chat para que o modelo lembre do contexto.
*   **Componentes**: Adicionar componentes de memória (Chat Memory) ao fluxo anterior.
*   **Tarefa**: Converse com o modelo, diga seu nome, e depois pergunte "Qual é o meu nome?" para testar a memória.

### 3. RAG com ChromaDB (Chat com PDF)
*   **Arquivo**: [Exercicio_3.json](exercicios/Exercicio_3.json)
*   **Objetivo**: Fazer o modelo responder perguntas baseadas em um documento PDF.
*   **Recursos**: Utilize os PDFs disponíveis na pasta `exercicios/pdfs/`.
*   **Componentes**:
    *   File Loader (para ler o PDF)
    *   Recursive Character Text Splitter (para dividir o texto)
    *   Ollama Embeddings (ou outro modelo de embedding compatível)
    *   ChromaDB (Vector Store)
    *   RAG Chain ou componentes manuais de busca.
*   **Tarefa**: Carregue um PDF e faça perguntas específicas sobre o conteúdo dele.
*   **Nota**: Este exercício utiliza o **Ollama** e **ChromaDB** que já estão configurados no `docker-compose.yml`.

### 4. Criação de Agente com Tools
*   **Arquivo**: [Exercicio_4.json](exercicios/Exercicio_4.json)
*   **Objetivo**: Criar um agente capaz de decidir quando usar ferramentas externas.
*   **Componentes**: Agent, Groq Model, Tools (ex: Calculator, URL).
*   **Tarefa**: Pergunte ao agente algo que exija cálculo matemático (ex: "Quanto é 25 * 48 + 100?") e veja ele usar a ferramenta de calculadora.

### 5. Chat com Website (Web Loader)
*   **Arquivo**: [Exercicio_5.json](exercicios/Exercicio_5.json)
*   **Objetivo**: Extrair informações de uma página web em tempo real.
*   **Componentes**: URL Loader -> Text Splitter -> Vector Store -> RAG.
*   **Tarefa**: Aponte o URL Loader para um site de notícias ou documentação técnica e faça perguntas sobre o conteúdo da página.

## 🔌 Testando Integrações

Além de usar o Langflow diretamente na interface, você pode integrá-lo em suas aplicações. Deixamos dois arquivos de exemplo para isso:

### 1. Teste via API (`teste_api.py`)
Este script Python mostra como chamar seu fluxo via API REST.
*   **Como usar**:
    1.  No Langflow, clique em "API" no canto direito do seu fluxo.
    2.  Copie a URL e o código de exemplo (ou apenas ajuste a variável `url` no arquivo) e o input_value.
    3.  Execute `python3 teste_api.py` para ver a resposta no terminal.

### 2. Widget HTML (`teste_index.html`)
Este arquivo HTML simula um site real que integra o chat do Langflow.
*   **Como usar**:
    1.  No Langflow, clique em "API" -> "Widget".
    2.  Copie o código `<script>` fornecido.
    3.  Cole o código dentro do arquivo `teste_index.html` onde indicado (`<!-- COLAR AQUI O CÓDIGO DO CHAT -->`).
    4.  Abra o arquivo no navegador para testar o chat embarcado.

---

**Bom curso!**

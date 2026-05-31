# 💻 Código-Fonte (`src/`) - InvestMind AI

Esta pasta contém todo o código executável em Python responsável por orquestrar, instanciar e rodar o ecossistema de agentes do **InvestMind AI**.

## 🏗️ Estrutura e Responsabilidades

Ao invés de deixar arquivos de script soltos na raiz do projeto, mantemos a lógica de programação centralizada aqui. O sistema foi construído utilizando a biblioteca `autogen_agentchat` e consome LLMs locais via servidor local (LM Studio).

O que você vai encontrar aqui (ou o que será adicionado conforme a evolução do projeto):

* **`main.py`**: O script principal que inicia a aplicação. Ele é o responsável por ler as configurações da equipe (no arquivo `.json` da pasta `agents/`), injetar os *System Prompts* (da pasta `prompts/`) e iniciar o chat de grupo em formato *Round Robin*.
* **Integração de Modelos**: Módulos que conectam o sistema ao modelo `gpt-oss-20b` hospedado localmente (no endereço `http://127.0.0.1:1234/v1`).
* **Formatadores e Parsers**: Scripts auxiliares que limpam as saídas dos agentes e as formatam em tabelas Markdown amigáveis para leitura do usuário final.

## ⚙️ Dependências Principais

Para rodar o código desta pasta, você precisará das seguintes bibliotecas principais (listadas também no `requirements.txt` da raiz):

* `autogen-agentchat` (v1)
* `autogen-ext` (modelos da OpenAI adaptados para inferência local)
* `pytest` (apenas para a suíte de testes)

## 🚀 Como iniciar o sistema

Certifique-se de que o seu servidor local (LM Studio, Ollama, etc.) esteja rodando na porta correta com o modelo carregado. Em seguida, a partir da **raiz do repositório**, execute:

```bash
python src/main.py
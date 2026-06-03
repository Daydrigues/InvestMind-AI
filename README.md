# InvestMind AI

*Banca de Consultoria Financeira Multiagente impulsionada por Inteligência Artificial.*

![Python](https://img.shields.io/badge/Python-3776AB?logo=python\&logoColor=white)
![AutoGen](https://img.shields.io/badge/AutoGen-Multi--Agent-blue)
![LM Studio](https://img.shields.io/badge/LM_Studio-Local_Inference-FF6B35)
![Offline](https://img.shields.io/badge/100%25-Offline-success)

---

## 1. Visão Geral

Este repositório contém a solução completa para o **InvestMind AI**.

O sistema consiste em uma arquitetura robusta de agentes autônomos construída através da interface do **AutoGen Studio**. Ao invés de uma resposta única de um chatbot padrão, o sistema simula uma mesa redonda com 8 especialistas financeiros para entregar uma recomendação de carteira de investimentos altamente analítica e consolidada.

Toda a inteligência roda de forma privada e local utilizando o **LM Studio** como provedor do modelo de linguagem.

## 2. Estado do Projeto

A infraestrutura e a engenharia de prompts dos especialistas foram modeladas visualmente:

* [x] **Orquestração Visual:** Fluxo de debate e agentes construídos utilizando o JSON Editor do AutoGen Studio.
* [x] **Privacidade e Backend Local:** Inferência processada 100% offline via LM Studio com o modelo de preferência do usuário.
* [x] **Agentes Especialistas:** Perfis independentes com diretrizes estritas (Conservador, Moderado, Agressivo, Cripto, Macro, Risco, Educador e Orquestrador).
* [x] **Portabilidade:** Toda a configuração da equipe exportada e salva no arquivo `investmind_team.json`.

## 3. Arquitetura

O projeto opera com base em duas frentes que se comunicam no ambiente local:

1. **Backend de Inferência (LM Studio):** Atua como o "cérebro" do sistema. Ele carrega o modelo LLM e expõe uma API local que o AutoGen consome para gerar os textos.
2. **Frontend de Orquestração (AutoGen Studio):** Interface web onde os agentes foram desenhados (via editor JSON) e onde as interações e debates ocorrem.

## 4. Como Executar o Projeto Localmente

**Importante:** O ecossistema exige que o servidor local do LLM (LM Studio) esteja rodando antes de inicializar a interface do AutoGen.

### Pré-requisitos

* Python instalado na máquina.
* LM Studio instalado e rodando localmente.

### Passo 1: Inicializando o Backend (LM Studio)

1. Abra o LM Studio.
2. Pesquise e carregue o modelo LLM de sua preferência.
3. Inicie o Servidor Local (geralmente na porta `1234`).

> Certifique-se de que o log do LM Studio indique que o servidor está ouvindo requisições (ex: `http://127.0.0.1:1234/v1`).

### Passo 2: Configurando e Inicializando o AutoGen Studio

```bash
mkdir ambiente-investmind
cd ambiente-investmind

pip install autogenstudio

autogenstudio ui --port 8081
```

> Abra `http://localhost:8081` no navegador.

### Passo 3: Importando a Equipe

1. Navegue até **Build → Teams**.
2. Importe o arquivo `/agents/investmind_team.json`.
3. Vá para **Playground**, selecione a equipe **InvestMind AI - 8 Agentes** e inicie uma nova sessão.

## 5. Estrutura da Equipe (Agentes)

| Agente           | Perfil de Atuação    | Objetivo Principal                                                                       |
| ---------------- | -------------------- | ---------------------------------------------------------------------------------------- |
| **Orquestrador** | Racional e analítico | Iniciar a reunião e repassar a palavra para o especialista Macro.                        |
| **Macro**        | Técnico e lógico     | Fornecer projeções econômicas (Selic, IPCA, câmbio) para guiar a equipe.                 |
| **Conservador**  | Prudente             | Propor alocações seguras em Renda Fixa e FGC, priorizando proteção de capital.           |
| **Moderado**     | Equilibrado          | Buscar crescimento com controle de volatilidade (FIIs, multimercados).                   |
| **Agressivo**    | Ousado               | Maximizar retornos via Small Caps e ações globais, aceitando volatilidade.               |
| **Cripto**       | Moderno              | Identificar assimetrias e analisar tecnologia blockchain com foco em Bitcoin e Ethereum. |
| **Risco**        | Crítico e rigoroso   | Auditar a carteira, calculando falhas de diversificação e alertando sobre armadilhas.    |
| **Apresentador** | Didático e comercial | Consolidar o debate em um relatório final formatado em Markdown limpo.                   |

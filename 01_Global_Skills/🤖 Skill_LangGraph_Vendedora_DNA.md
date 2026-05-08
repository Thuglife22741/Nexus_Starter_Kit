# 🤖 Skill_LangGraph_Vendedora_DNA.md

Este guia documenta o padrão técnico de engenharia de agentes da Alavanca AI, migrando de fluxos lineares do n8n para grafos de estado cíclicos e inteligentes usando **LangGraph**.

---

## 1. Arquitetura: Do Linear (n8n) ao Cíclico (LangGraph)

No n8n, os fluxos são disparados por Webhooks e seguem uma sequência rígida. No LangGraph, o fluxo é um **StateGraph** onde cada etapa é um **Node** (função) e as decisões são tomadas por **Conditional Edges**.

### Mapeamento de Nodos Principais:
| Nodo n8n | Nodo LangGraph (`src/graphs/main-agent/graph.ts`) | Função |
| :--- | :--- | :--- |
| Webhook Trigger | `enfileirar` / `esperar_debounce` | Recebe a mensagem e aguarda novas mensagens do mesmo usuário para agrupar (evita múltiplas respostas). |
| Switch/IF | `verificar_stale` | Ignora mensagens antigas se houver uma nova na fila (otimização de custos e lógica). |
| PostgreSQL / Redis | `tentar_lock` | Mecanismo de concorrência que impede que duas instâncias respondam ao mesmo usuário simultaneamente. |
| AI Agent Node | `executar_agente` | O "cérebro" (LLM) que utiliza o padrão **ReAct** (Reasoning + Acting). |
| HTTP Request (Bot) | `enviar_texto` / `enviar_audio` | Saída formatada para o Chatwoot/WhatsApp, com suporte a **SSML** e **TTS** (ElevenLabs). |

---

## 2. State Management (A Memória Vital)

O Estado (`MainAgentState`) é o único "ponto de verdade" em cada iteração. Definido em `src/graphs/main-agent/state.ts` usando `Annotation.Root`.

### Estrutura do DNA do Estado:
- **MessagesAnnotation**: Pilha de mensagens `(HumanMessage, AIMessage, ToolMessage)` que mantém o contexto imediato da conversa técnica.
- **Metadata Webhook**: armazena `idMensagem`, `idConversa`, `telefone`, `idConta` para roteamento.
- **Controle de Fluxo**:
    - `locked`: Booleano para controle de concorrência.
    - `stale`: Flaga para descarte de mensagens obsoletas.
    - `novasMensagens`: Monitora se o usuário mandou algo enquanto a IA "pensava".
- **Memória de Longo Prazo**: O histórico total é persistido no DB (`n8n_historico_mensagens`) e recuperado via `buscarHistorico` no início do nodo de execução.

---

## 3. Execução de Ferramentas e Isolamento de Raciocínio

Para garantir que o agente não execute APIs (Calendário, Supabase) de forma impulsiva, utilizamos o isolamento em `src/tools/`.

### O Padrão "Reason-Before-Action":
O agente utiliza a ferramenta **`Refletir`** (`src/tools/refletir.ts`).
- **Função**: Apenas registra o pensamento no log (`thought`).
- **Poder**: Obriga o LLM a planejar o agendamento ou a query de banco de dados no "scratchpad" antes de chamar a ferramenta real.

### Fábrica de Ferramentas (Factory):
As ferramentas são injetadas dinamicamente via `criarToolsAgenteClinica` injetando o contexto necessário (IDs da conta, telefone do cliente) sem que o LLM precise "adivinhar" esses dados.

---

## 4. Sincronização de Kanban (O "Lugar de Verdade")

Diferente do n8n onde o Kanban é atualizado no fim do fluxo, aqui a Maria (IA) é instruída via **System Prompt** a executar `Atualizar_tarefa` **imediatamente após cada descoberta de dado** relevante (Nome, Procedimento, Interest).

- **Vantagem**: Se o script quebrar no meio, o CRM já reflete o estágio atual do lead.
- **Regra de Ouro**: Preservar a descrição original e anexar novos dados (`description += new_data`).

---

## 5. Resumo de Conversão (N8N → LangGraph)

Para converter qualquer fluxo Alavanca AI:
1. **Defina o Estado**: O que a automação precisa "saber" entre um nodo e outro?
2. **Modularize as Ferramentas**: Toda chamada de API vira um arquivo na pasta `/tools` com esquema Zod rigoroso.
3. **Crie o Grafo**: Desenhe o `StateGraph` focando em loops de retry (Lock) e agrupamento (Debounce).
4. **Instrua o DNA**: No System Prompt, defina os SOPs (Procedimentos Operacionais Padrão) como se fosse um treinamento de funcionário real.

---
> *Documento gerado automaticamente pelo Nexus AI para excelência em engenharia de agentes.*

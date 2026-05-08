# 🏥 Agente de Agendamento Clínica (LangGraph)

## 🎯 Objetivo

Sistema autônomo de agendamento médico que utiliza **Grafos de Estado (Stateful Graphs)** para gerenciar consultas em clínicas, garantindo que o fluxo de marcação seja seguido sem perder o contexto.

**## 🗺️ Arquitetura Visual (Nexus V4.0)** **Consulte o  [[Workflow_Camila_LangGraph.canvas]]    para visualizar os nós do LangGraph (`search`, `book`, `cancel`).**


## 🛠️ Stack Técnica (Extraída do Repositório)

- **Engine de Fluxo:** `LangGraph` (Gerencia os nós de decisão: `search`, `book`, `cancel`).
    
- **LLM:** `LangChain` + Modelos de Chat.
    
- **Integração de Dados:** `Google Calendar API` (Fonte única de verdade para horários).
    
- **Lógica de Estado:** Uso de `TypedDict` para manter o histórico da reserva (Data, Especialidade, Nome).
    

## 🔄 Workflow de Execução (Lógica do Grafo)

1. **Nó de Entrada:** O Agente recebe a solicitação (Ex: "Quero marcar clínico para amanhã").
    
2. **Nó de Busca:** O sistema consulta o Calendário do Google para verificar slots livres.
    
3. **Nó de Decisão:** - Se houver conflito: Sugere novo horário.
    
    - Se estiver livre: Solicita confirmação.
        
4. **Nó de Finalização:** Grava o evento via `Calendar` e encerra a thread de estado.
    

## 📂 Estrutura de Arquivos Críticos

- `app.py` ou `main.py`: Ponto de entrada do LangGraph.
    
- `tools.py`: Onde moram as ferramentas de escrita e leitura no Google Calendar.
    
- `graph.py`: Definição dos nós e das arestas (edges) do fluxo.
    

## 🔗 Links Oficiais
[[📉 Monitoramento_de_Custos_Claude]]
[[🔑 Git_Multicontas]]
**GitHub:** [agente-agendamento-clinica-langgraph](https://github.com/Thuglife22741/agente-agendamento-clinica-langgraph)
    


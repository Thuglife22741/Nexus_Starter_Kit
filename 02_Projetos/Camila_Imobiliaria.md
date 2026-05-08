# 🏠 Camila — Assistente Imobiliária

## 🎯 Objetivo

Agente autônomo de alta performance em **LangGraph** para atendimento humanizado, qualificação de leads e busca semântica de imóveis (RAG) integrada ao WhatsApp.

## 🗺️ Arquitetura Visual
Consulte o [[Workflow_Camila_LangGraph.canvas]]  para entender o fluxo de estados e integração com Groq/Supabase.
  

## 🛠️ Stack Técnica

- **Runtime:** Bun — Velocidade máxima de execução.
    
- **Orquestração:** LangGraph & LangChain (StateGraph).
    
- **LLM Principal:** OpenAI GPT-4o-mini.
    
- **RAG & Embeddings:** OpenAI `text-embedding-3-small` + Supabase PGVector.
    
- **Transcrição:** Groq Whisper (Áudio para Texto).
    
- **Infra:** Easypanel / Nixpacks (Deploy contínuo via Git).
    

## 📝 Workflow (StateGraph)

1. **Recepção:** Webhook da Evolution API encaminha a mensagem do cliente.
    
2. **Transcrição:** Áudios convertidos via Groq Whisper no `groq.service.ts`.
    
3. **Qualificação:** Verifica `leads` no Supabase. Se faltar dados, pede Nome + Email.
    
4. **Busca Semântica (RAG):** Consulta `imobiliaria_rag` via RPC `match_documents`.
    
5. **Ação CRM:** Move o lead no Kanban automaticamente via `auto_move_lead_on_agendamento`.
    
6. **Resposta Visual:** Envio de cards ricos (imagem/preço) via Evolution API.
    

## ⚠️ Regras e Restrições

- **Pipeline Kanban:** Seguir rigorosamente a ordem: Novo Lead → Contato Inicial → Visita Marcada → Proposta Enviada → Documentação → Fechado.
    
- **Modelo:** NUNCA utilizar Google Gemini; o modelo padrão é **GPT-4o-mini**.
    
- **Status:** NUNCA alterar status sem confirmação de intenção no log de `webhook_eventos`.
    

## 🔗 Links Relacionados

## 🔗 Links Relacionados
[[🔑 Git_Multicontas.md]]
[[📉 Monitoramento_de_Custos_Claude.md]]
- **GitHub Repository (Agente):** [camila-imobiliaria-langgraph](https://github.com/Thuglife22741/camila-imobiliaria-langgraph)
- **GitHub Repository (Frontend):** [dashboardmobi](https://github.com/fernandocerqueira126-ui/dashboardmobi)


## 🛠️ Stack Técnica & Identificação Dinâmica

- **Core:** Operação unificada entre **Camila (LangGraph/Bun)** e **DashboardMobi (Frontend)**.
    
- **URL do Projeto:** A IA deve localizar a variável `SUPABASE_URL` no arquivo `.env` na raiz do diretório de trabalho atual.
    
- **Chaves de API:** - `SUPABASE_SERVICE_ROLE_KEY`: Uso exclusivo do Agente LangGraph (Backend/Bun) para bypass de RLS e escrita de logs.
    
    - `SUPABASE_ANON_KEY`: Uso do DashboardMobi para escuta de eventos via Realtime.
        
- **Tabelas por Contexto (Ecossistema Unificado):**
    
    - **CRM & Kanban:** `leads` (Onde a Camila qualifica e o Dashboard exibe), `agendamentos`.
        
    - **Sincronia Universal:** `webhook_eventos` — Tabela mestre para espelhamento Realtime entre o que acontece no WhatsApp e o que aparece no painel.
        
    - **Inteligência RAG:** `imobiliaria_rag` (Embeddings de 1536 dims para busca de imóveis).
        

## 📋 Workflow (Sincronia IA ↔ Frontend)

1. **Verificação de Motor:** Validar se o runtime (Bun) carregou corretamente as variáveis de ambiente antes de iniciar o `StateGraph`.
    
2. **Input & Persistência:** Ao receber webhook da Evolution API, o fluxo LangGraph deve consultar/atualizar a tabela `leads` para manter o estado do Kanban atualizado.
    
3. **Bridge Realtime:** Toda alteração crítica feita pela IA (ex: lead qualificado) deve disparar um `insert` em `webhook_eventos`. O Dashboard deve estar em _listen_ constante para atualizar a UI sem refresh.
    
4. **Busca Semântica (RAG):** Executar a RPC `match_documents` para entregar cards de imóveis no WhatsApp baseados no desejo do lead.
    
5. **Automação de Fluxo:** A RPC `auto_move_lead_on_agendamento` é o gatilho que garante que a IA e o Dashboard estejam sempre na mesma fase do funil.
    

## ⚠️ Regras e Restrições

- **Fonte da Verdade:** O banco é universal. NUNCA criar tabelas duplicadas para "Camila" e "Dashboard". Ambos leem a mesma `leads`.
    
- **Segurança:** NUNCA expor chaves reais. Referencie apenas os nomes das variáveis de ambiente.
    
- **Protocolo RAG:** A busca de imóveis deve usar exclusivamente `PGVector` com similaridade de cosseno, ignorando modelos de busca legados.
    
- **Performance:** Manter as consultas otimizadas para não inflar o consumo de tokens durante o loop de pensamento do LangGraph.
    

## 🔗 Links Relacionados
[[📉 Monitoramento_de_Custos_Claude.md]]
[[🔑 Git_Multicontas.md]]
[[DashboardMobi]]
[[Camila_Imobiliaria]]
- **GitHub Repository (Agente):** [camila-imobiliaria-langgraph](https://github.com/Thuglife22741/camila-imobiliaria-langgraph)
- **GitHub Repository (Frontend):** [dashboardmobi](https://github.com/fernandocerqueira126-ui/dashboardmobi)




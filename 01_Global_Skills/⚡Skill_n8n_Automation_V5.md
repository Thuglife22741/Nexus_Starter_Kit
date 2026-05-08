# ⚡ Skill: n8n Automation Mastery V5

Este documento codifica a inteligência extraída do repositório `n8n-skills`, focada em padrões de elite para automação, extração de DNA técnico e aplicações estratégicas.

---

## 🏛️ 1. Catálogo de Automação de Elite

### 🤖 IA Agents (O Futuro da Decisão)
O padrão de ouro para agentes n8n não é apenas um nó, mas uma orquestração de **LLM + Ferramentas + Memória**.
- **Arquitetura Base**: `Trigger → AI Agent (Language Model + Tools + Memory) → Output`.
- **Conexões Críticas**:
    - `ai_languageModel`: Cérebro (OpenAI, Anthropic, Gemini).
    - `ai_tool`: Braços operacionais (Qualquer nó pode ser uma ferramenta via porta `ai_tool`).
    - `ai_memory`: Contexto (Window Buffer Memory para conversas longas).
- **Tooling Intelligence**: Use Descrições Ultra-Específicas. O AI decide usar a ferramenta com base na descrição, não no nome.

### 🔌 Integrações de CRM & API (Sincronização Perfeita)
- **Padrão Webhook**: `Webhook → Validate → Transform → Respond/Notify`.
- **Estratégia API**: Seguir o padrão `Trigger → HTTP Request → Transform → Action`.
- **Nós Baseados em Recursos**: Sempre identifique primeiro o `Resource` (ex: `contact`) e depois a `Operation` (ex: `create`), pois os campos obrigatórios mudam dinamicamente.

### 📊 Processamento de Dados (Alta Performance)
- **Code Node Mastery**: Use o modo **"Run Once for All Items"** para 95% dos casos. É mais rápido e permite agregações (somas, filtros complexos).
- **Looping de Elite**: Use `Split In Batches` para processar grandes volumes de dados sem estourar a memória ou limites de API.

---

## 🧬 2. DNA Técnico: Padrões de Estruturação

### 🔹 JSON & Data Access
- **A Regra de Ouro do Webhook**: Dados de entrada sempre residem em `$json.body`. Esqueça `$json` direto para webhooks.
- **Formato de Retorno (Code Node)**: Deve ser SEMPRE um array de objetos com a chave `json`: `return [{ json: { result: "success" } }];`.
- **Referência Cruzada**: Acesse dados de nós anteriores via `{{$node["Nome do Nó"].json.field}}`.

### 🔹 Chamadas de API (HTTP Request)
- **Progressive Discovery**: Use `detail: "standard"` para descobrir campos necessários. Não tente configurar tudo de uma vez.
- **Dependências de Propriedade**:
    - `method: POST` → Habilita `sendBody`.
    - `sendBody: true` → Exige `body`.
    - `authentication != none` → Exige `credentials`.

### 🔹 Expressões de Elite
- **Sintaxe**: Use sempre `{{ }}` em nós de configuração.
- **Variáveis de Ambiente**: Use `$env` para segredos e configurações globais, evitando hardcoding.

---

## 🎯 3. Fit Estratégico: Aplicações Práticas

### 🩺 Dr. Ana Cristina: Agendamento Inteligente
*   **Fluxo**: `Webhook (WhatsApp/Chat) → AI Agent → Google Calendar Tool → WhatsApp Tool`.
*   **Intelligence**: O Agente de IA interpreta a linguagem natural ("Quero marcar pra terça as 14h"), usa o nó do Calendário como **ai_tool** para checar disponibilidade e o nó de WhatsApp para confirmar.
*   **Vantagem**: Reduz a fricção humana e resolve conflitos de agenda automaticamente.

### 🎩 Mr. Cavalheiros: Fluxo de Pedidos & CRM
*   **Fluxo**: `Shopify Webhook → Code Node (Data Cleanup) → CRM Node (Upsert) → Slack/Email Notification`.
*   **Intelligence**: O `Code Node` limpa e formata os dados do pedido (DNA do Mr. Cavalheiros) antes de enviar para o CRM. Use o padrão `Split In Batches` se um pedido contiver múltiplos itens que precisam de processamento individual.
*   **Vantagem**: Garante integridade de dados no CRM e automação total desde o clique de compra até o rastreio.

---

## 🛠️ 4. Auditoria de Qualidade (Quick Check)
- [ ] O Webhook aponta para `$json.body`?
- [ ] O Code Node retorna `[{json: {}}]`?
- [ ] As ferramentas de IA possuem descrições claras e operacionais?
- [ ] As credenciais estão isoladas em parâmetros de autenticação (não URLs)?

---
**⚡ Gerado por Antigravity - Nexus AI Brain V5.0**

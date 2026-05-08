# 📊 DashboardMobi — Painel de Controle Real Estate

## 🎯 Objetivo
Interface administrativa para monitoramento de leads, visualização de métricas e controle de pipeline imobiliário.

## 🗺️ Arquitetura Visual
Consulte o [[Workflow_Dashboard_Realtime.canvas]] para entender a sincronização Realtime e renderização de componentes.

## 🛠️ Stack Técnica
- **UI:** React + Tailwind CSS + Shadcn/UI
- **Realtime:** Supabase Realtime (webhooks)
- **Framework:** Next.js / Vite

## 📝 Workflow (Sincronização)
1. **Webhook Eventos:** Ouve mudanças na tabela `webhook_eventos` do Supabase.
2. **Visualização:** Atualiza instantaneamente os cards do Kanban no frontend.
3. **Métricas:** Gera gráficos de performance dos corretores e status do funil.

## 🔗 Links Relacionados
[[Camila_Imobiliaria.md]]
[[🔑 Git_Multicontas.md]]
[[📉 Monitoramento_de_Custos_Claude.md]]
**GitHub Repository (Frontend):** [dashboardmobi](https://github.com/fernandocerqueira126-ui/dashboardmobi)


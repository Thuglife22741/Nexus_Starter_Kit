# 🎙️ J.A.R.V.I.S. — Sistema de Voz Futurista (Nexus V4.0)

## 🎯 Objetivo
Interface de voz de ultra-baixa latência com execução de ferramentas reais via MCP nativo, centralizando o processamento no motor de voz para resposta instantânea.

## 📋 Diretrizes de Governança (Nexus V5.0)
- **Segurança**: [[🔒 Skill_Security_V5]] — Bloqueio de scripts e gating de runtime obrigatório para Action Layer.
- **Arquitetura**: [[🧼 Skill_Clean_Code_V5]] — Funções de voz devem seguir responsabilidade única.
- **Performance**: [[🛍️ Skill_Performance_V5]] — Cache de respostas ElevenLabs para ultra-latency.

> ⚠️ **Regra de Execução**: Antes de acionar qualquer ferramenta via MCP, valide se o ambiente cumpre o Node.js Guard (>= 22.6.0).


## 🛠️ Stack Técnica
- **Frontend:** React + TypeScript + Vite (Apenas interface e streaming).
- **Engine de Voz:** ElevenLabs Conversational AI (WebRTC).
- **Protocolo de Ação:** Rube MCP (Model Context Protocol) — **Conectado nativamente ao ElevenLabs**.
- **Visual:** 3D Engine Spline.

## 🔄 Workflow de Execução (Cérebro Centralizado)
1. **Voz Gateway:** Frontend inicia sessão WebRTC direta com ElevenLabs.
2. **Cérebro (ElevenLabs):** O motor de voz processa o áudio e identifica a necessidade de ferramentas.
3. **Action Layer (MCP):** O ElevenLabs invoca o **Rube MCP** diretamente para acessar Calendário, Google Sheets e Contexto de Engenharia.
4. **Feedback:** O Rube retorna os dados; o ElevenLabs sintetiza a resposta já com o dado real integrado em milissegundos.

## 🗺️ Arquitetura Visual (Nexus V4.0)
> [!IMPORTANT]
> A nova topologia de conexão direta (ElevenLabs <-> Rube MCP) está mapeada em:
> ** [[Workflow_Jarvis_Voz.canvas]] **

## 🔗 Links Relacionados
[[📉 Monitoramento_de_Custos_Claude.md]]
[[🔑 Git_Multicontas.md]]
[[📊 Skill_GoogleSheets_Contacts]]
**GitHub Repository:** [jarvis](https://github.com/Thuglife22741/jarvis)










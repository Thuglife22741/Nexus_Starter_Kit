# 🔑 Git Multicontas (HTTPS) — Alavanca AI

## 🎯 Objetivo

Garantir que a IA realize commits com a identidade correta (Thuglife ou UI) sem a necessidade de passar credenciais manualmente no chat em cada sessão.

## 🛠️ Configuração de Identidade Local

A IA deve sempre configurar o usuário localmente logo após clonar ou antes do primeiro commit no diretório:

|**Conta GitHub**|**Usuário Git**|**E-mail Associado**|**Projetos Relacionados**|
|---|---|---|---|
|**Thuglife22741**|`Thuglife22741`|`fernandoborgescerqueira@gmail.com`|[[Jarvis_Voz]], [[Camila_Imobiliaria]]|
|**fernandocerqueira126-ui**|`fernandocerqueira126-ui`|`fernandocerqueira126@gmail.com`|[[DashboardMobi]]|

## 📝 Workflow de Execução (Automático para IA)

1. **Detecção:** A IA deve ler o nome da pasta ou o repositório remoto.
    
2. **Aplicação:** Se a pasta for `DashboardMobi`, aplicar automaticamente a configuração de e-mail `...126@gmail.com`.
    
3. **Autenticação:** Utilizar o Git Credential Manager (pop-up) para validar o acesso ao repositório via HTTPS.
    

## ⚠️ Regras de Ouro

- **NUNCA** realizar commit global (`--global`). Use sempre a configuração local do repositório.
    
- **Validação:** Antes de dar `git push`, a IA deve rodar `git config user.email` para confirmar se está na conta certa.
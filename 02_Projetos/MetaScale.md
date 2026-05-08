# 📈 MetaScale

**Projeto**: Plataforma SaaS de Análise e Escala de Campanhas Meta Ads
**Motor**: Next.js 14 (App Router), Tailwind CSS, Supabase (PostgreSQL), Anthropic API (Claude 3.5 Sonnet).

## 📌 Escopo Executivo (Boil the Lake)
O MetaScale revoluciona a tomada de decisão para gestores de tráfego de e-commerce e dropshipping, automatizando o princípio de funil matemático "80x10x10". Em vez de analisar métricas isoladas, o sistema conecta-se via API Oficial da Meta, absorve os dados diários, traça o funil desde a impressão até a conversão global, e diagnostica a saúde da campanha.

### 🎯 Proposta de Valor Core
1. **Conexão API Nativa**: Importação em tempo real via Meta Marketing API OAuth.
2. **Sistema de Flagging (Status de Escala)**: Classificação matemática e autônoma entre: `ESCALÁVEL`, `OTIMIZAR` e `NÃO ESCALAR`.
3. **Analista de IA Post-hoc**: Um motor Claude que atua como media buyer Sênior, justificando visualmente os gargalos com recomendações priorizadas.
4. **Simulador Híbrido**: Interface slider "what-if" para calcular ROAS e Margem de Lucro projetada antes do aumento de *spend*.

## 🏗️ Arquitetura de Dados (Supabase)
O banco foi desenhado com segurança (RLS) e escalabilidade em mente:
- `profiles`: Hierarquia de permissões (`admin`, `viewer`).
- `meta_ad_accounts`: Cofre de Access Tokens.
- `campaigns`: Catálogo de instâncias operacionais.
- `campaign_metrics`: Snapshots diários (Time-Series) contendo os recortes de impressão, alcance, cliques, conversões e faturamento.
- `ai_diagnostics`: Cache de inferências da Anthropic (evitando requisições de custo alto em campanhas já diagnosticadas).
- `scale_simulations`: Repositório de cenários matemáticos construídos pelos usuários.

## 🛡️ Protocolo de Segurança Adotado
- **Zero hardcoding**: `NEXT_PUBLIC_` para variáveis expostas, e restrição ao máximo em tokens sensíveis.
- **RLS Rigoroso**: Todos os endpoints de banco bloqueados na raiz por auth.uid().

## 📊 Status Atual
- [x] Engine Matemático 80x10x10 Validado.
- [x] Schema SQL e Migrations.
- [x] UI Premium SaaS (Dashboard, Campaign Details, Simulator).
- [ ] Integração real com endpoint Graph API do Meta.
- [ ] Liberação da V1 para Beta Testers.



## 🔗 Links Relacionados
- **Canvas de Arquitetura:** [[MetaScale.canvas]]
- **Skills Globais Injetadas:** 
  - [[🧠 Skill_GStack_Executive_Suite]] (Arquitetura e Segurança)
  - [[🎨 Skill_Frontend_Design_Elite]] (Design UI/UX Premium)
  - [[🛡️Conexao_Supabase]] (DB e Auth)
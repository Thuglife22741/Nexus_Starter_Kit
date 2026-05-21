# 🎯 Estratégias Meta Ads — Framework Refinado

> **Fonte**: Repositório `claude-ads` (mineração completa)
> **Versão**: 2026-05-21
> **Motor de IA Meta**: Andromeda + GEM + Lattice (stack 2025-2026)

---

## 1. ANDROMEDA: O Novo Motor de Entrega Meta (2026)

Meta reconstruiu seu stack de entrega em 3 releases que mudam TUDO:

### 1.1 Os 3 Pilares do Novo Motor

| Componente | Lançamento | O que faz |
|---|---|---|
| **Andromeda** | Out 2025 | Motor de ranking com 10.000× mais capacidade. Filtra criativos antes do leilão |
| **GEM** (Generative Embedding Model) | Final 2025 | O *conteúdo* criativo se embute diretamente no espaço de targeting → **"Criativo É o Novo Targeting"** não é mais slogan, é mecânica real |
| **Lattice** | Final 2025 / Início 2026 | Otimizador baseado em sequência que usa ações do usuário para ranquear anúncios |

### 1.2 A Regra de Ouro da Similaridade

> ⚠️ **REGRA CRÍTICA**: Anúncios com Similarity Score > 60% sofrem **supressão de entrega** pelo Andromeda.
> 100 variações menores NÃO performam melhor que 10 criativos genuinamente distintos.

**Entity-ID Clustering**: Andromeda agrupa criativos quase idênticos e limita silenciosamente sua entrega. Priorize **diversidade de conceito/ângulo/formato** sobre volume de variantes.

---

## 2. FRAMEWORK DE DIVERSIDADE CRIATIVA (Rubrica 0-10)

Score de diversidade para avaliar risco de clustering do Andromeda:

| Eixo | 0 (Risco Alto) | 1 (OK) | 2 (Forte) |
|------|----------------|--------|-----------|
| **Diversidade de conceito** | Mensagem/proposta única em todos os assets | 2 mensagens distintas | 3+ ângulos distintos (problema, prova social, comparação…) |
| **Diversidade de formato** | Um formato apenas (ex: só imagem estática) | 2 formatos | 3+ (imagem, vídeo, carrossel, collection) |
| **Diversidade visual** | Uma paleta / um modelo / uma composição | 2 tratamentos visuais distintos | 3+ tratamentos visualmente distintos |
| **Diversidade de gancho (vídeo)** | Todos os ganchos ≤3s parecem iguais | 2 padrões de gancho | 3+ padrões (UGC POV, pergunta, afirmação, demo…) |
| **Diversidade de headline** | Todas as headlines parafraseiam a mesma frase | 2 estruturas de headline | 3+ estruturas (número, pergunta, afirmação, comparação) |

### Interpretação do Score
- **8-10** = BAIXO risco de clustering → Excelente entrega
- **4-7** = MÉDIO risco → Alguma supressão provável
- **0-3** = ALTO risco → Perda significativa de impressões

---

## 3. PREDITOR DE CLUSTERING PRÉ-LANÇAMENTO

Antes de subir criativos, analise pares para prever clustering:

| Heurística | Resultado |
|---|---|
| Mesmo produto hero, modelo, backdrop, iluminação | **Provável cluster** |
| Mesmos primeiros 4 tokens na headline | **Provável cluster** |
| Mesma frase de abertura no copy + mesmo verbo CTA | **Provável cluster** mesmo com corpo diferente |
| Mesmo shot 0-3s no vídeo + mesmo padrão de narração | **Provável cluster** mesmo se resto diverge |
| Par (estática + vídeo) E visual diferente | **NÃO são cluster** → sinal forte de diversidade |

---

## 4. ESTRUTURA DE CONTA — CBO vs ABO

### 4.1 Decisão CBO vs ABO

| Cenário | Estratégia | Razão |
|---|---|---|
| Budget > $500/dia | **CBO** | Campaigns provados em escala |
| Budget < $100/dia ou fase de teste | **ABO** | Controle granular por ad set |
| $100-$500/dia | **Depende** | CBO se campanhas maduras, ABO se testando |

### 4.2 Estrutura Simplificada (Recomendada 2026)

```
📦 ESTRUTURA IDEAL META ADS 2026
│
├── 1-3 campanhas total (consolidação máxima)
│   ├── Ad sets maiores, menos fragmentados
│   ├── Budget ≥ 5× CPA target por ad set
│   └── Overlap entre ad sets < 30%
│
├── Learning Phase
│   ├── PASS: < 30% ad sets em "Learning Limited"
│   ├── WARNING: 30-50% Learning Limited
│   └── FAIL: > 50% Learning Limited
│
└── Regra: NÃO editar durante Learning Phase (causa reset)
```

### 4.3 Advantage+ Sales Campaigns (ex-ASC)

- Renomeado de ASC em 2025
- Existing customer budget cap eliminado em fev 2025
- **Benchmarks**: 22% maior ROAS, 11.7% melhoria de CPA
- MAPI v25 depreca endpoints ASC/AAC legados → usar Sales/Leads/App + defaults ASC

**Checklist Advantage+:**
- [ ] Catálogo conectado (Sales)
- [ ] Cap de cliente existente setado 10-25%
- [ ] Advantage+ Audience habilitado por default
- [ ] Advantage+ Creative enhancements ON
- [ ] Advantage+ Placements habilitado

---

## 5. PÚBLICOS E TARGETING

### 5.1 Frequência Saudável

| Tipo | Saudável | Warning | Fail |
|---|---|---|---|
| Prospecting (7 dias) | < 3.0 | 3.0-5.0 | > 5.0 |
| Retargeting (7 dias) | < 8.0 | 8.0-12.0 | > 12.0 |

### 5.2 Checklist de Públicos

- [ ] Custom Audiences: visitantes do site, listas de clientes, engajamento
- [ ] Lookalike: múltiplos seeds testados (1%, 3%, 5%) — fonte ≥ 1.000 usuários
- [ ] Advantage+ Audience testado vs targeting manual
- [ ] Interesses broad o suficiente para otimização do algoritmo
- [ ] Exclusões: compradores excluídos de prospecting, overlap gerenciado
- [ ] Overlap entre ad sets < 20% (usar Audience Overlap tool)
- [ ] First-party data: lista de clientes uploaded e atualizada < 180 dias

### 5.3 Mudanças 2025-2026

- **Detailed targeting exclusions removidas** (phased out mar 2025, 100% jan 2026) → usar Custom Audience exclusions ou Advantage+ Audience
- **Financial Products**: nova Special Ad Category (jan 2025) com mesmas restrições de Housing/Employment/Credit
- **Threads**: placement GA jan 2026, 400M+ MAU, CPMs menores que Feed/Stories

---

## 6. ESTRATÉGIA DE BIDDING META

| Estratégia | Quando Usar | Comportamento |
|---|---|---|
| **Lowest Cost** (default) | Volume máximo | Melhor para escalar, pode ter variância de CPA |
| **Cost Cap** | Proteção de margem | Define teto de CPA, pode reduzir volume |
| **Bid Cap** | Controle máximo | Bid máximo por leilão |
| **ROAS Goal** | Revenue tracking ativo | Target de retorno |

---

## 7. ESCALABILIDADE — REGRAS DE OURO

### Regra dos 20%
> Nunca aumente budget mais que 20% de cada vez. Monitore 3-5 dias após cada aumento.

```
Semana 1: $100/dia → $120/dia
Semana 2: $120/dia → $144/dia
Semana 3: $144/dia → $173/dia
```

### 5 Métodos de Escalar
1. **Vertical**: +20% budget em campanhas vencedoras
2. **Horizontal**: duplicar campanhas vencedoras para novos públicos
3. **Plataforma**: expandir para novas plataformas
4. **Geográfico**: testar novos mercados/regiões
5. **Formato**: testar novos formatos na mesma plataforma

### Green Light para Escalar
- [ ] CPA abaixo do target por 2+ semanas
- [ ] ≥ 50 conversões/semana (learning phase saiu)
- [ ] CTR estável ou melhorando
- [ ] ROAS acima do target
- [ ] Sem sinais de creative fatigue

### Kill Rule (Regra dos 3×)
- CPA > 3× target → **PAUSAR imediatamente** (precisa ≥7 dias de dados, ≥20 cliques)
- Sem conversões com ≥ $100 gastos ou ≥ 50 cliques → **PAUSAR e diagnosticar**
- CTR < 50% do benchmark → **Matar criativo, testar novo**
- ROAS < 50% do target com ≥ 14 dias → **Reduzir 50% budget ou pausar**

---

## 8. PIXEL / CAPI — FUNDAÇÃO DE TRACKING

### 8.1 Hierarquia de Prioridade (Checks Críticos)

| ID | Check | Impacto |
|---|---|---|
| M01 | Pixel instalado e disparando em todas as páginas | Sem pixel = sem dados |
| M02 | CAPI ativo (30-40% perda de dados sem ele pós-iOS 14.5) | Fundamental |
| M03 | Event deduplication (event_id matching, ≥90% dedup) | Evita double-counting |
| M04 | EMQ ≥ 8.0 para Purchase | Qualidade do match |

### 8.2 EMQ Optimization Guide

| EMQ Score | Status | Ação |
|---|---|---|
| 8.0-10.0 | Excelente | Manter setup |
| 6.0-7.9 | Bom | Adicionar mais parâmetros customer_information |
| 4.0-5.9 | Regular | Implementar CAPI, melhorar qualidade de dados |
| < 4.0 | Crítico | CAPI + Enhanced Matching obrigatório |

**Parâmetros chave para maximizar EMQ:**
- `em` (email) → maior taxa de match
- `ph` (telefone) → segundo maior sinal
- `fn`, `ln` (nome/sobrenome)
- `ct`, `st`, `zp` (cidade, estado, CEP)
- `external_id` (CRM/user ID para matching cross-device)

**Case study documentado**: EMQ 8.6→9.3 = CPA -18%, match rate +24%, ROAS +22%

---

## 9. BENCHMARKS META ADS 2026

### Por Objetivo
| Objetivo | CTR | CPC | CVR | CPL |
|---|---|---|---|---|
| Traffic | 1.71% | $0.70 | — | — |
| Leads | 2.59% | $1.92 | 7.72% | $27.66 |

### ROAS por Segmento
| Segmento | ROAS |
|---|---|
| Todas indústrias (mediana) | 2.19:1 |
| Retargeting | 3.61:1 |
| Advantage+ Sales | 4.52:1 |

### Creative Fatigue (Lifespan Andromeda)
| Sinal | TOF | BOF |
|---|---|---|
| Lifespan criativo | 2-4 semanas (era 6-8) | 6-7 semanas |
| Exposições antes da queda de 45% conversão | 4 | — |

### Budget Mínimo Viável
- **Meta Ads**: $600-$800/mês
- Budget por ad set: ≥ 5× target CPA
- Mínimo para learning phase: 50 conversões/semana por ad set

---

## 10. FRAMEWORK DE TESTE A/B (META EXPERIMENTS)

### Estrutura de Hipótese

```
SE [ação/mudança]
ENTÃO [métrica] vai [aumentar/diminuir] em [% estimado]
PORQUE [raciocínio baseado em dados ou insight]

Exemplo:
SE substituirmos product shots polidos por vídeos UGC de criadores
ENTÃO o CTR no Meta vai aumentar em 25-40%
PORQUE Andromeda prioriza formatos criativos diversos e UGC
consistentemente supera polido nos benchmarks 2025-2026
```

### Setup Meta Experiments
- Usar Ads Manager > Experiments tab (não duplicação manual)
- Splitting automático de audiência (sem overlap)
- Tipos suportados: A/B (creative, audience, placement), Holdout, Brand Survey
- Budget: split uniforme; mínimo $100/dia por variante
- Duração: 7-14 dias; Meta auto-determina vencedor a 95% confiança

### O Que Testar (Prioridade)
1. **Conceito criativo** (ângulos diferentes, não apenas cores)
2. **Gancho/primeiros 3 segundos** (vídeo)
3. **Estrutura da oferta** (pricing, tipo desconto)
4. **Landing page** (headline, CTA, tamanho form)
5. **Bidding strategy** (tCPA vs tROAS vs Maximize)

---

## 11. SPECS CRIATIVOS META

### Dimensões por Placement

| Placement | Ratio | Dimensões | Prioridade |
|---|---|---|---|
| Feed (preferido) | 4:5 | 1080×1350 | **Target primário** |
| Feed (quadrado) | 1:1 | 1080×1080 | Alto |
| Stories | 9:16 | 1080×1920 | Alto |
| Reels | 9:16 | 1080×1920 | Alto |

### Safe Zones (Reels/Stories)
- **Topo 120px**: barra de status (EVITAR)
- **Zona segura**: Y:120 até Y:1420 (1080×1300px)
- **Bottom 500px**: CTA button, caption, reactions (EVITAR)
- **Regra**: Manter faces, produto e texto crítico na zona central

### Limites de Copy
| Componente | Recomendado | Máximo |
|---|---|---|
| Primary Text | 40-125 chars | 2.200 (truncado em 125 mobile) |
| Headline | 27-40 chars | — |
| Description (carrossel) | 20 chars | — |
| Reels Primary Text | 72 chars visíveis | — |

---

## 12. BUDGET ALLOCATION — REGRA 70/20/10

| Fatia | Alocação | Descrição |
|---|---|---|
| **70%** | Canais provados | ROAS/CPA targets consistentemente atingidos |
| **20%** | Canais em escala | Mostrando promessa, precisam mais dados |
| **10%** | Canais de teste | Novas plataformas, audiências, criativos |

### MER (Marketing Efficiency Ratio)
```
MER = Receita Total / Gasto Total de Marketing
```
- Target MER varia: 3×-10× dependendo das margens
- Usar MER para avaliar saúde geral, não apenas ROAS por plataforma

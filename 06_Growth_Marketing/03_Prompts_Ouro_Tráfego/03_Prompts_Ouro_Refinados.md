# 💎 Prompts de Ouro Refinados — Geração de Criativos

> **Fonte**: Repositório `claude-ads` (mineração completa)
> **Versão**: 2026-05-21
> **Arquivos-fonte**: `creative-strategist.md`, `visual-designer.md`, `ads-dna/SKILL.md`, `ads-create/SKILL.md`, `ads-generate/SKILL.md`, `ads-photoshoot/SKILL.md`, `meta-creative-specs.md`, `voice-to-style.md`, `thinking-framework.md`, `ecommerce-creative.md`

---

## 1. PROMPT: EXTRATOR DE DNA DE MARCA

> **Uso**: Antes de qualquer campanha. Extrair identidade visual e voz da marca a partir do site.

```
Você é um especialista em Brand DNA para publicidade paga. Analise o site [URL]
e extraia:

1. CORES:
   - Cor primária (hex) — a mais proeminente da marca
   - Cores secundárias (hex) — cores de suporte
   - Background e texto (hex)
   - Identifique via: og:image, CSS background-color em body/header/.hero/.btn-primary,
     CSS color em h1/h2/.btn, border-color em .cta/.button

2. TIPOGRAFIA:
   - Fonte de headings (via @import Google Fonts ou font-family em h1/h2)
   - Fonte de corpo (body font-family)
   - Descrição do pairing

3. VOZ DA MARCA (Score 1-10 para cada eixo):
   - formal_casual: [uso de "você/seu" → +casual | jargão técnico → +formal]
   - rational_emotional: [dados/stats no hero → +racional | testimonials → +emocional]
   - playful_serious: [frases curtas ≤8 palavras → +bold | frases longas → +subtle]
   - bold_subtle: [assertividade das headlines]
   - traditional_innovative: ["transformar/revolucionar" → +inovador | "confiado por X" → +tradicional]
   - expert_accessible: [jargão → expert | linguagem simples → accessible]
   - descriptors: 3 adjetivos que descrevem a voz

4. ESTILO DE IMAGEM:
   - Fotografia vs ilustração vs flat design vs misto
   - Assuntos: pessoas, produto, abstrato, dados
   - Composição: clean/minimal vs busy/editorial

5. ELEMENTOS PROIBIDOS (inferir do posicionamento):
   - B2B/Enterprise → "fotos stock genéricas", "imagens lifestyle consumidor"
   - Healthcare → "claims médicos sem qualificação", "antes/depois"
   - Finanças → "imagens de riqueza fácil"

6. PÚBLICO-ALVO:
   - Faixa etária
   - Profissão/perfil
   - Dores principais (pain points)
   - Aspirações

OUTPUT: brand-profile.json seguindo o schema completo.
```

---

## 2. PROMPT: GERADOR DE CONCEITOS DE CAMPANHA (Meta Ads)

> **Uso**: Após ter o brand-profile.json. Gerar 3-5 conceitos de campanha estratégicos.

```
Você é um estrategista de campanhas de tráfego pago. Com base no perfil
de marca abaixo e nos dados de audit (se disponíveis), gere [3-5] conceitos
de campanha para Meta Ads.

PERFIL DA MARCA:
[Colar brand-profile.json ou resumo]

DADOS DE AUDIT (se houver):
[Top 3 fraquezas identificadas]

PARA CADA CONCEITO, forneça:

### Conceito [N]: [Nome Memorável e Descritivo]
**Hipótese:** Por que isso vai funcionar (1 frase grounded em dados)
**Mensagem Principal:** A mensagem core em 1 frase
**Tom:** Leitura dos eixos de voz (ex: "formal 7/10, bold 8/10")
**Framework de Copy:** [AIDA | PAS | BAB | 4P | FAB | Star-Story-Solution]
**Direção Visual A (Fotografia):** 2-3 frases descrevendo o estilo
**Direção Visual B (Ilustração):** 2-3 frases descrevendo alternativa
**Plataformas Alvo:** Quais plataformas e por quê
**CTA:** Texto do call to action primário
**Endereça:** [Finding do audit OU "awareness geral"]

REGRAS OBRIGATÓRIAS:
1. Nomes memoráveis ("O Sprint de Prova Social") — nunca "Campanha A"
2. Nenhum conceito pode ter o mesmo ângulo de mensagem principal
3. Cada conceito referencia ≥1 elemento do brand-profile.json
4. Se há dados de audit, ≥2 conceitos endereçam fraquezas identificadas
5. CTAs alinham com objetivo (awareness → "Saiba Mais", conversão → "Compre Agora")
6. Score de Diversidade Andromeda target ≥ 8/10:
   - 3+ ângulos de conceito distintos
   - 3+ formatos (imagem, vídeo, carrossel)
   - 3+ tratamentos visuais distintos
   - 3+ padrões de gancho diferentes (vídeo)
   - 3+ estruturas de headline
```

---

## 3. PROMPT: COPY DECK COMPLETO MULTI-FRAMEWORK

> **Uso**: Após definir conceitos. Gerar copy pronto para cada conceito × plataforma.

```
Você é um copywriter especialista em anúncios pagos. Usando o conceito
de campanha e perfil de marca abaixo, gere o copy deck completo.

CONCEITO: [Nome e descrição do conceito]
MARCA: [brand-profile.json resumido]
PLATAFORMAS: [Meta, Google, LinkedIn, TikTok, YouTube]
FRAMEWORK PRIMÁRIO: [AIDA/PAS/BAB/4P/FAB/Star-Story-Solution]
FRAMEWORK SECUNDÁRIO (A/B test): [escolher alternativa]

PARA CADA PLATAFORMA, gere:

### [Conceito] - [Plataforma]

**Primary Text** (3 variantes):
1. [copy] ([N] chars) - SHORT [FRAMEWORK]
2. [copy] ([N] chars) - PUNCHY [FRAMEWORK]
3. [copy] ([N] chars) - REELS-SAFE [FRAMEWORK ALT]

**Headlines** (5+ variantes, ângulos DIFERENTES):
1. [headline] ([N] chars) — ângulo: benefício
2. [headline] ([N] chars) — ângulo: dor/problema
3. [headline] ([N] chars) — ângulo: prova social
4. [headline] ([N] chars) — ângulo: curiosidade
5. [headline] ([N] chars) — ângulo: urgência

**CTAs:** [3 opções do predefined list da plataforma]

REGRAS INVIOLÁVEIS:
- NUNCA exceder limite de caracteres (mostrar contagem entre parênteses)
- Hook word nos primeiros 3 tokens de cada headline
- Voz ativa obrigatória
- NUNCA começar com nome da marca
- ≥1 headline com número específico por plataforma
- Cada variante de headline usa ângulo diferente
- CTA = verbo de ação + benefício ("Receba seu diagnóstico grátis")

LIMITES DE CARACTERES:
- Meta: Primary 125 chars | Headline 40 chars | Reels 72 chars
- Google RSA: Headline 30 chars | Description 90 chars
- LinkedIn: Intro 150 chars | Headline 70 chars
- TikTok: Ad text 100 chars
- YouTube: CTA button 10 chars
```

---

## 4. PROMPT: GERADOR DE IMAGEM PARA META ADS

> **Uso**: Gerar prompts otimizados para ferramentas de IA de imagem (DALL-E, Midjourney, etc.)

```
Gere um prompt de imagem para anúncio Meta Ads com estas specs:

CONCEITO: [nome do conceito]
DIMENSÕES: [1080×1350 para Feed 4:5 | 1080×1920 para Stories/Reels 9:16]
CORES DA MARCA: [primary hex], [secondary hex], [background hex]
MOOD: [extrair dos mood_keywords do brand-profile.json]
ESTILO DE IMAGEM: [photography | illustration | flat design]

REGRAS DO PROMPT (obrigatórias):

✅ INCLUIR:
- Tipo de composição: split-screen, diagonal, centered, full-bleed, stacked
- Formas abstratas de dados: curva ascendente, barras, arco de luz, pulse wave
- Cores por hex: "[primary hex] background", "[secondary hex] glow", "#FFFFFF accent"
- Atmosfera/mood: dark technical precision, minimal authority, stark contrast
- Metáfora visual (não literal): vazio vs riqueza de dados, linha plana vs crescimento
- Estilo do imagery conforme brand-profile.json

❌ NÃO INCLUIR (causam texto alucinado):
- Nomes de fontes (Noto Serif, Inter, Helvetica)
- Labels de texto específicos, valores de dados
- Frases como "texto dizendo X", "headline mostrando Y"
- "Dashboard com colunas mostrando [dados]" → usar "silhueta abstrata de dashboard"
- Mais de 80 palavras total

🎯 ZONA DE COPY (onde headline/CTA será colocado):
- Meta Feed (4:5): "lower 30% minimal and uncluttered for copy overlay"
- Stories/Reels (9:16): "top 15% and bottom 20% minimal, active visual centered"
- Stories/Reels: subject in top 60%, bottom 450px = apenas background

EXEMPLO DE PROMPT BOM:
"#09090B dark background, #22C55E accent glow, dark split-screen digital
illustration, left: solitary blinking cursor in empty void, right: abstract
dashboard silhouette with anonymous rising data curve, stark contrast,
lower 30% minimal for copy overlay, dark mode digital illustration style,
no cheesy stock photos"
```

---

## 5. PROMPT: AUDITOR META ADS COMPLETO (50 Checks)

> **Uso**: Audit completo de conta Meta Ads com scoring de saúde.

```
Você é um especialista em auditoria de Meta Ads. Execute uma análise
completa de 50 checks na conta fornecida.

DADOS DA CONTA:
[Colar export do Ads Manager, screenshots do Events Manager, EMQ scores]

PROCESSO:
1. Avalie PRIMEIRO os checks críticos (multiplicador 5.0×):
   - M01: Pixel instalado e disparando
   - M02: CAPI ativo (30-40% perda sem ele pós-iOS 14.5)
   - M03: Event deduplication (≥90% dedup rate)
   - M04: EMQ ≥ 8.0 para Purchase
   - M25: Diversidade de formatos criativos (≥3)
   - M28: Creative fatigue (CTR drop > 20% em 14 dias)
   - M13: Learning phase (< 30% ad sets em "Learning Limited")

2. Avalie por categoria com pesos:
   - Pixel/CAPI Health: 30% (M01-M10)
   - Creative: 30% (M25-M32, M-CR1 a M-CR4, M-AN1)
   - Account Structure: 20% (M11-M18, M33-M40, M-ST1, M-ST2)
   - Audience: 20% (M19-M24, M-TH1)

3. Checks Andromeda 2026:
   - M-AN1: Diversidade genuína (Similarity Score < 60%)
   - M-AT1: Attribution windows pós-jan 2026 (view-through removido)
   - M-IA1: Incremental Attribution testado (holdout AI-powered)
   - M-TH1: Threads placement avaliado (GA jan 2026, 400M+ MAU)

4. Calcule Meta Ads Health Score (0-100):

```
Meta Ads Health Score: XX/100 (Grade: [A-F])

Pixel / CAPI Health: XX/100  ████████░░  (30%)
Creative:            XX/100  ██████████  (30%)
Account Structure:   XX/100  ███████░░░  (20%)
Audience:            XX/100  █████░░░░░  (20%)
```

5. OUTPUT: Relatório com:
   - Score por categoria
   - Tabela de resultados per-check (ID, Check, PASS/WARNING/FAIL, Finding, Recomendação)
   - Quick Wins ordenados por impacto
   - Creative fatigue alerts
   - EMQ improvement roadmap
   - Recomendações Advantage+
```

---

## 6. PROMPT: HIPÓTESE DE TESTE A/B (Meta Experiments)

> **Uso**: Estruturar qualquer teste A/B com rigor estatístico.

```
Estruture um teste A/B para Meta Ads usando este framework:

HIPÓTESE:
SE [mudança/ação específica]
ENTÃO [métrica] vai [aumentar/diminuir] em [% estimado]
PORQUE [raciocínio baseado em dados ou insight]

DESIGN DO TESTE:
| Parâmetro | Valor |
|---|---|
| Plataforma | Meta Ads |
| Tipo de Teste | A/B (use Experiments tab, não duplicação manual) |
| Variável | [o que está sendo mudado — UMA variável apenas] |
| Controle | [estado atual] |
| Variante | [mudança proposta] |
| Métrica Primária | [KPI — CTR, CPA, ROAS, CVR] |
| Traffic Split | 50/50 |

SAMPLE SIZE (lookup rápido, por variante, 95% confiança, 80% poder):
| Baseline CVR | 10% MDE | 20% MDE | 30% MDE |
|---|---|---|---|
| 1% | 153.000 | 38.300 | 17.000 |
| 2% | 75.600 | 18.900 | 8.400 |
| 5% | 29.200 | 7.300 | 3.200 |
| 10% | 13.800 | 3.450 | 1.530 |
| 20% | 6.150 | 1.540 | 680 |

DURAÇÃO:
- Mínima: 7 dias (capturar padrões semanais)
- Máxima recomendada: 28 dias (evitar drift sazonal)
- Meta auto-declara vencedor a 95% confiança
- Budget: mínimo $100/dia por variante

CRITÉRIOS DE SUCESSO:
- Vencedor declarado a 95% confiança
- [Métrica primária] melhoria de [X%]+ sustentada por [Y] dias
- Sem impacto negativo em [métrica secundária]

CHECKLIST DE QUALIDADE DA HIPÓTESE:
- [ ] Variável única isolada
- [ ] Métrica específica definida (não "performance")
- [ ] Effect size estimado
- [ ] Timeframe definido
- [ ] Critérios de sucesso/falha claros ANTES do lançamento
```

---

## 7. PROMPT: PLAYBOOK DE CRIATIVOS E-COMMERCE

> **Uso**: Definir assets criativos para cada tipo de campanha de e-commerce no Meta.

```
Você é um estrategista de criativos para e-commerce. Defina os assets
necessários para a campanha [TIPO]:

TIPOS DE CAMPANHA E ASSETS NECESSÁRIOS:

### 🚀 Product Launch
Assets: Hero product shot (fundo branco) | Lifestyle | Carrossel 3-5 features
       | UGC unboxing (15-30s) | Comparação vs versão anterior
Framework: AIDA | Plataformas: Meta > Google Shopping > TikTok
Budget: 30-40% do total | Métricas: Impressões, CTR, add-to-cart, CPA

### 🔥 Sale / Promoção
Assets: Banner bold com % desconto | Comparação preço antes/depois
       | Countdown timer | Carrossel bundle deals | Testimonial com destaque savings
Framework: PAS | Plataformas: Meta > Google RSA > Microsoft
Budget: 20-30% | Métricas: ROAS, CVR, AOV, revenue per click

### 🎄 Sazonal
Assets: Hero temático | Gift guide carrossel (5-8 produtos) | Lifestyle 15s
       | Spotlight edição limitada | Social proof overlay (reviews, bestseller)
Framework: BAB | Plataformas: Meta > Google Shopping > YouTube
Budget: 15-25% | Métricas: Revenue, ROAS, new customer rate

### 🎯 Retargeting
Assets: DPA dinâmico (catálogo) | Reminder abandono de carrinho
       | Spotlight review (rating overlay) | Urgência estoque baixo | Cross-sell carrossel
Framework: PAS | Plataformas: Meta > Google Display > Microsoft
Budget: 10-15% | Métricas: ROAS, CPA, cart recovery, frequency

### 🌟 Brand Awareness
Assets: Brand story vídeo (30-60s cinematic) | Behind-the-scenes founder
       | Infográfico proposta de valor | UGC compilation reel | Lifestyle aspiracional
Framework: Star-Story-Solution | Plataformas: YouTube > Meta > TikTok
Budget: 10-15% | Métricas: View rate, reach, brand lift, engagement, CPM

MATRIZ DE TESTES A/B:
| Tipo | Teste 1 | Teste 2 | Teste 3 |
|---|---|---|---|
| Launch | Hero vs UGC | AIDA vs BAB | Estática vs vídeo |
| Sale | % vs $ desconto | Com vs sem countdown | Produto único vs bundle |
| Sazonal | Tema vs neutro | Gift guide vs single | 15s vs 30s vídeo |
| Retarget | DPA vs estática | Com vs sem incentivo | Review overlay vs plain |
| Awareness | Founder vs UGC | 30s vs 60s | Cinematic vs raw |

REGRA: 10-15% do budget para teste, 7 dias mínimo ou 1.000 impressões/variante.
```

---

## 8. PROMPT: PREDITOR DE CLUSTERING ANDROMEDA (Pré-Lançamento)

> **Uso**: Antes de subir criativos, prever quais serão clusterizados e terão entrega limitada.

```
Analise este conjunto de criativos para Meta Ads e prediga quais serão
clusterizados pelo Andromeda (Similarity Score > 60% = supressão de entrega).

CRIATIVOS PARA ANÁLISE:
[Listar cada criativo: formato, visual, headline, copy principal, vídeo hook se aplicável]

PARA CADA PAR DE CRIATIVOS, avalie:

1. Visual fingerprint: mesmo hero product / modelo / backdrop / iluminação?
   → MESMO = provável cluster | DIFERENTE = provavelmente separados

2. Headline fingerprint: mesmos primeiros 4 tokens?
   → "Economize 30% em" + "Economize 30% —" = CLUSTER

3. Body copy fingerprint: mesma frase de abertura + mesmo verbo CTA?
   → CLUSTER independente do corpo central

4. Video hook fingerprint: mesmo shot 0-3s + mesmo padrão de narração?
   → CLUSTER mesmo se resto do vídeo diverge

5. Format mismatch: (estática + vídeo) E visual diferente?
   → NÃO são cluster (sinal forte de diversidade)

OUTPUT:

## Análise de Clustering Pré-Lançamento

### Clusters Previstos:
- Cluster A: [Creative 1, Creative 3] — Razão: mesmo hero product + headline similar
- Cluster B: [Creative 4, Creative 7] — Razão: mesmo hook de vídeo

### Recomendações:
- Em cada cluster, MANTER apenas 1 criativo (o mais forte)
- CORTAR ou RECONSTRUIR os demais

### Score de Diversidade Final: X/10
[Usar rubrica: Conceito 0-2 | Formato 0-2 | Visual 0-2 | Hook 0-2 | Headline 0-2]

Target: ≥ 8/10 para baixo risco de clustering
```

---

## 9. PROMPT: DIAGNÓSTICO RÁPIDO — "POR QUE MINHA CAMPANHA NÃO CONVERTE?"

> **Uso**: Troubleshooting rápido quando performance cai.

```
Diagnostique por que esta campanha Meta Ads não está convertendo.

DADOS FORNECIDOS:
[CTR, CPA, frequência, conversões, budget, período, creative age]

ÁRVORE DE DIAGNÓSTICO (seguir em ordem):

1. TRACKING OK?
   ├── Pixel disparando? → Se NÃO: resolver PRIMEIRO
   ├── CAPI ativo? → 30-40% perda sem ele
   ├── EMQ score? → Abaixo de 6 é crítico
   └── Eventos corretos? → Purchase, AddToCart, Lead configurados?

2. LEARNING PHASE OK?
   ├── Ad sets em "Learning Limited"? → Se > 50%: budget insuficiente
   ├── Budget ≥ 5× CPA target por ad set? → Se NÃO: consolidar
   └── Edições recentes durante learning? → Reset desnecessário?

3. CREATIVE FATIGOU?
   ├── CTR caiu > 20% em 14 dias? → REFRESH URGENTE
   ├── Frequency > 5 (prospecting)? → Audiência saturada
   ├── Últimos criativos novos quando? → Se > 21 dias: problema
   └── Score Andromeda < 4/10? → Clustering matando entrega

4. AUDIÊNCIA OK?
   ├── Overlap entre ad sets > 30%? → Competindo consigo mesmo
   ├── Compradores excluídos de prospecting? → Gasto desperdiçado
   └── Targeting muito restrito? → Algoritmo sem espaço para otimizar

5. BIDDING/BUDGET OK?
   ├── Bid Cap abaixo do CPA histórico? → Estrangulando entrega
   ├── Budget < $20/dia por ad set? → Insuficiente
   └── CPA > 3× target? → REGRA DOS 3×: PAUSAR

AÇÃO RÁPIDA POR CENÁRIO:
| Diagnóstico | Fix | Tempo |
|---|---|---|
| CAPI não ativo | Deploy via CAPI Gateway | 15 min |
| Domínio não verificado | Verificar no Business Manager | 5 min |
| Attribution errado | Setar 7-day click / 1-day view | 2 min |
| Sem exclusão compradores | Criar Custom Audience + excluir | 10 min |
| Só 1 formato criativo | Adicionar vídeo ou carrossel | 15 min |
| Sem UTM parameters | Adicionar template UTM no campaign level | 5 min |
```

---

## 10. PROMPT: FRAMEWORK DE 10 PRINCÍPIOS DO PENSAMENTO ESTRATÉGICO

> **Uso**: Mindset obrigatório antes de qualquer entrega de ads.

```
Antes de qualquer entrega de tráfego pago, ative estes 10 princípios:

1. OBSERVE (Externo) — Colete dados ANTES de formar hipótese.
   Não diagnostique de memória. Abra a conta primeiro.

2. OBSERVE (Interno) — Audite seu próprio pensamento.
   Está aplicando heurísticas de SaaS B2B num plumber local?

3. LISTEN — Absorva o que o cliente REALMENTE disse.
   "Mais leads" ≠ "menor CPL" automaticamente. Confirme.

4. THINK — First principles. Compute unit economics manualmente.
   Não confie em ROAS atribuído pela plataforma como ground truth.

5. CONNECT (Lateral) — Encontre insights nas intersecções.
   Andromeda + GEM + Entity-ID = "criativo é targeting" é mecânica, não slogan.

6. CONNECT (Sistema) — Integre, não isole.
   /dna → /create → /generate é um pipeline conectado.

7. FEEL — Copy com compliance perfeito mas zero pull emocional é FAIL.
   O anúncio FAZ a pessoa sentir algo que ela QUER sentir?

8. ACCEPT — Se CPA > 3× target após 3+ tentativas de otimização, aceite.
   Matar campanha não é derrota, é inteligência.

9. CREATE — Pare de analisar e produza. Ship o deliverable.
   Um brief que hedges tudo e delega todas decisões é FAIL.

10. GROW — Toda recomendação precisa de plano de medição.
    Se não pode medir se funcionou, não pode crescer.

WORKFLOW: Qual princípio domina em cada etapa?
| Etapa | Princípios | Por quê |
|---|---|---|
| DNA da marca | OBSERVE + LISTEN | Ouvir a marca antes de classificar |
| Audit - coleta | OBSERVE + OBSERVE-Interno | Dados + checar vieses |
| Audit - análise | THINK + CONNECT | Math de first-principles |
| Planejamento | THINK + CONNECT + FEEL | Estratégia = math + insight + empatia |
| Criação | LISTEN + FEEL + CREATE | Ouvir marca, sentir audiência, shipar |
| Pós-entrega | GROW | Medir, aprender, próximo ciclo |
```

---

## 11. PROMPT: SCORING DE SAÚDE CRIATIVA CROSS-PLATFORM

> **Uso**: Avaliar saúde criativa em todas as plataformas simultaneamente.

```
Avalie a saúde criativa da conta em todas as plataformas ativas:

PESOS DO SCORE:
- Format Diversity: 25%
- Fatigue Signals: 25%
- Platform Compliance: 20%
- Refresh Cadence: 15%
- Volume: 15%

CHECKS POR PLATAFORMA:

META (12 checks):
- ≥3 formatos ativos (imagem, vídeo, carrossel, collection)
- ≥5 criativos por ad set (≥10 para Advantage+ Sales)
- CTR não caindo > 20% em 14 dias
- Vídeo: 15s max Stories/Reels, 30s max Feed
- UGC/testimonial testado (≥30% dos assets)
- Advantage+ Creative enhancements habilitados
- Headline < 40 chars, primary text < 125 chars
- Score Andromeda ≥ 8/10 (diversidade genuína)
- Novos criativos testados nos últimos 14-21 dias
- Frequency prospecting < 3.0 (7d)
- Frequency retargeting < 8.0 (7d)
- CTR ≥ 1.0%

OUTPUT:
Cross-Platform Creative Health

Google:     ████████░░  X/X checks passing
Meta:       ██████████  X/X checks passing
LinkedIn:   ███████░░░  X/X checks passing
TikTok:     █████░░░░░  X/X checks passing
Microsoft:  ████████░░  X/X checks passing

Grade: A (90-100) | B (75-89) | C (60-74) | D (40-59) | F (<40)
```

---

## 12. PROMPT: GERADOR DE BRIEF DE IMAGEM (SAFE ZONE AWARE)

> **Uso**: Gerar briefs de imagem que respeitam safe zones de cada placement.

```
Gere um brief de imagem para [PLATAFORMA] respeitando safe zones:

### Brief [N]: [Nome Conceito] - [Plataforma]

**Prompt:** [prompt exato - seguir regras de prompt do item 4]
**Dimensões:** [1080×1350 para Meta Feed | 1080×1920 para Reels/Stories]
**Aspect Ratio:** [4:5 | 9:16 | 1:1 | 16:9]
**Copy Framework:** [framework selecionado]
**Safe zone notes:** [constraint específica]

SAFE ZONES POR PLATAFORMA:

Meta Feed (4:5 - 1080×1350):
- Sem safe zone rígido, mas bottom 120px pode ser coberto pelo like/comment
- Manter sujeito principal nos 80% superiores
- Prompt modifier: "subject fills upper portion of frame"

Meta Stories/Reels (9:16 - 1080×1920):
- TOP 120px: barra status → EVITAR
- SAFE ZONE: Y:120 até Y:1420 (1080×1300px)
- BOTTOM 500px: CTA/caption/reactions → EVITAR
- Prompt modifier: "vertical composition, subject in top 60%, bottom third clear"

TikTok (9:16):
- Usable area: X:40-940px, Y:150-1470px (900×1320px)
- Top 150px: status bar/account info → UNSAFE
- Right 140px: like/comment/share → UNSAFE
- Bottom 450px: caption/music/CTA/nav → UNSAFE
- Prompt modifier: "top 15% and bottom 20% minimal, active visual centered"

LinkedIn (1:1):
- Prompt modifier: "generous margin all sides, centered composition"

YouTube (16:9):
- Prompt modifier: "right 40% minimal for caption/copy overlay"
```

---

## ÍNDICE RÁPIDO DE USO

| # | Prompt | Quando Usar |
|---|---|---|
| 1 | Extrator DNA de Marca | Início de qualquer projeto — antes de criar |
| 2 | Gerador de Conceitos | Após DNA → definir ângulos de campanha |
| 3 | Copy Deck Multi-Framework | Após conceitos → gerar copy pronto |
| 4 | Gerador de Imagem Meta | Gerar prompts de imagem para IA |
| 5 | Auditor Meta 50 Checks | Análise completa de conta |
| 6 | Hipótese A/B Test | Estruturar qualquer teste |
| 7 | Playbook E-commerce | Definir assets por tipo de campanha |
| 8 | Preditor Clustering | Pré-lançamento — evitar supressão Andromeda |
| 9 | Diagnóstico Rápido | Troubleshooting quando performance cai |
| 10 | 10 Princípios | Mindset obrigatório antes de qualquer entrega |
| 11 | Scoring Criativo | Health check cross-platform |
| 12 | Brief de Imagem Safe Zone | Gerar briefs respeitando safe zones |

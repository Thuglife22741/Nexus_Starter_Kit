# 👔 Mr. Cavalheiros — Loja Shopify Premium

> **Tipo:** E-commerce · Shopify  
> **Segmento:** Moda Masculina de Luxo  
> **Status:** 🏗️ Planejamento Inicial  
> **Data:** 2026-04-12  
> **Responsável:** Nexus

---
## 📋 Diretrizes de Governança
- **Código de Elite**: [[🧼 Skill_Clean_Code_V5]] — Pipelines puros no processamento de pedidos.
- **Blindagem**: [[🔒 Skill_Security_V5]] — Pins de versão exatos em todas as extensões do Shopify.
- **Identidade**: [[💎 Skill_HighEnd_UI_V5]] — Aplicar rigor visual Ferrari/Lamborghini em cada seção Liquid.

--------------------------------------------------------------------------

## 🎯 Visão do Projeto

Loja Shopify premium voltada para moda masculina de alto padrão. O objetivo é criar uma experiência de compra que comunique **luxo, confiança e exclusividade** — onde o produto é o herói e a UI recua para deixá-lo falar. Identidade visual baseada em editorial cinematográfico com sotaque gold.

**Posicionamento:** "O guarda-roupa do homem que sabe o que quer."

---

## 🎨 DIRETRIZES DE DESIGN — High-End UI V5

> **Fonte:** `_SANDBOX_DESIGN/Skill_HighEnd_UI_V5.md` | Auditoria: ⭐ 9.0/10  
> **Stack de Referência:** Ferrari (chiaroscuro) + Lamborghini (gold accent) + Tesla (near-zero UI)

### Paleta de Cores

```css
:root {
  /* Fundo */
  --bg-void:    #000000;   /* Lamborghini — preto absoluto hero */
  --bg-surface: #0A0A0A;   /* Ferrari — preto cinematográfico */
  --bg-card:    #141414;   /* Cards de produto */

  /* Tipografia */
  --text-primary: #F5F5F0;
  --text-muted:   #888888;

  /* Acento Luxo */
  --accent-gold:  #D4AF37;  /* Lamborghini gold — único acento cromático */
  --accent-red:   #CC0000;  /* Ferrari Red — uso pontual (sale badges) */

  /* Bordas */
  --border-luxury: rgba(212,175,55,0.25);
  --border-subtle: rgba(255,255,255,0.06);

  /* Elevação */
  --shadow-gold: 0 0 40px rgba(212,175,55,0.15);
  --shadow-card: 0 20px 60px rgba(0,0,0,0.5);
}
```

### Tipografia

| Uso | Fonte | Peso | Regra |
|-----|-------|------|-------|
| Headlines hero | `Playfair Display` | 700 | **UPPERCASE** + `letter-spacing: 0.12em` |
| Subtítulos | `Inter` | 300 | Ultralight — elegância por leveza |
| Preços / Dados | `Inter` | 600 | Destaque em `--accent-gold` |
| Body / Descrição | `Inter` | 400 | `line-height: 1.7` |

### Padrões de Componente

**Hero Section** — Arquétipo Cinematográfico (Tesla/Ferrari):
- `100vh` full-viewport com foto do produto
- Overlay `rgba(0,0,0,0.55)` sobre a imagem
- Headline flutuando no `bottom: 8vh; left: 6vw`
- Dois CTAs: `[Explorar Coleção]` + `[Ver Lookbook]`
- Micro-animação: fade-in `opacity: 0→1` em `0.8s ease`

**Cards de Produto** — Airbnb adaptado dark:
```css
.product-card {
  background: var(--bg-card);
  border: 1px solid var(--border-subtle);
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.3s ease, border-color 0.3s ease;
}
.product-card:hover {
  transform: translateY(-4px);
  border-color: var(--border-luxury);
}
```

**Navbar** — SpaceX/Tesla sticky:
- `backdrop-filter: blur(20px)` + fundo `rgba(0,0,0,0.7)`
- Logo centrado ou à esquerda em branco puro
- Links com tracking wide `0.08em` uppercase

---

## 📈 DIRETRIZES DE SEO — Skill_SEO_OnPage_V5

> **Fonte:** `01_Global_Skills/ [[✅ Skill_SEO_OnPage_V5]] 
> **Integração:** Shopify Liquid + metafields + JSON-LD

### Mapeamento de Páginas → Intenção

| Página Shopify | Intenção | Estratégia |
|---|---|---|
| Home | Navigational | Brand story + coleções hero |
| /collections/ternos | Commercial | Hub page — arquitetura Hub & Spoke |
| /products/[produto] | Transactional | PDP com schema Product + FAQ |
| /pages/guia-de-estilo | Informational | Spoke — link interno para coleções |
| /pages/sobre | Navigational | Trust + brand authority |
| /blogs/moda | Informational | Silos topicais para orgânico |

### Regras Críticas de SEO para Shopify

- ✅ **1 único H1** por template (`product.title` ou `page.title` — nunca repetir em snippets)
- ✅ **Title tag** `< 60 chars` com keyword natural (`"Terno Slim Preto Premium | Mr. Cavalheiros"`)
- ✅ **Meta description** `< 155 chars` — entity names + value proposition, nunca keyword verbatim
- ✅ **AI Summary Nugget** (200 chars) acima do H1 em PDPs e páginas editoriais
- ✅ **JSON-LD** obrigatório: `Product` + `FAQPage` + `BreadcrumbList`
- ✅ **Alt text** descritivo nas imagens de produto (não keyword-stuffed)
- ❌ Nunca keyword exata no H2/H3
- ❌ Nunca bullet lists fingindo ser tabelas — usar `<table>` HTML real

### Metafields SEO Recomendados

```
namespace: seo
keys:
  - ai_summary_nugget  (single_line_text, max 200 chars)
  - page_intent        (transactional|commercial|informational)
  - not_for_you_block  (rich_text — para páginas editoriais)
  - emq_required       (boolean)
  - information_gain   (multi_line_text)
```

### Arquitetura de Conteúdo (Hub & Spoke)

```
Hub: /collections/ternos  ("Ternos Masculinos Premium")
├── Spoke 1: /pages/como-escolher-terno  (informational)
├── Spoke 2: /pages/guia-de-medidas      (informational)
├── Spoke 3: /collections/ternos-slim    (commercial)
├── Spoke 4: /collections/ternos-social  (commercial)
└── Spoke 5: /blogs/moda/terno-casamento (informational)
```

---

## ⚡ DIRETRIZES DE PERFORMANCE — Skill_Performance_V5

> **Fonte:** `01_Global_Skills/⚡ Skill_Performance_V5.md`

### Checklist de Performance Shopify

| Item | Regra | Meta |
|---|---|---|
| **Imagens** | WebP + `loading="lazy"` em cards; `eager` apenas no hero | < 200KB hero |
| **CSS** | Crítico inline no `<head>`; resto deferido | < 14KB crítico |
| **JS** | `defer` em todos os scripts de terceiros | LCP < 2.5s |
| **Fontes** | `font-display: swap` + preload das 2 fontes principais | FOUT aceitável |
| **Liquid** | Cache de queries pesadas via `{% cache %}` (Shopify Plus) | -90% re-renders |
| **Apps** | Auditar apps instalados — cada app adiciona ~200ms | < 4 apps ativos |

### Targets de Core Web Vitals

```
LCP (Largest Contentful Paint): < 2.5s
INP (Interaction to Next Paint): < 200ms
CLS (Cumulative Layout Shift):   < 0.1
```

### Otimizações Prioritárias

1. **Imagem hero** — usar `srcset` responsivo com `sizes="100vw"` 
2. **Fontes** — preload Playfair Display 700 + Inter 400 no `<head>`
3. **Below the fold** — lazy load de seções de coleção e reviews
4. **Checkout** — otimizar Shop Pay / acelerators

---

## 🛠️ STACK TÉCNICO

| Camada     | Tecnologia              | Observação                       |
| ---------- | ----------------------- | -------------------------------- |
| Plataforma | **Shopify**             | Tema customizado ou headless     |
| Tema       | **Liquid custom**       | [[🛍️ Skill_Liquid_Mastery_V5]]   |
| Frontend   | HTML + CSS + JS vanilla | Sem framework pesado             |
| GraphQL    | Storefront API          | [[🛍️ Skill_Shopify_GraphQL_V5]] |
| Checkout   | Shopify Functions       | [[🛍️ Skill_Shopify_Functions_V5]]  |
| Analytics  | GA4 + Meta Pixel        | Via Shopify app ou GTM           |
| SEO        | Metafields + JSON-LD    | [[✅ Skill_SEO_OnPage_V5]]        |

---

## 🗺️ ROADMAP INICIAL

### Fase 1 — Fundação Visual (Semana 1–2)
- [ ] Configurar tema base (custom ou fork de tema existente)
- [ ] Implementar design system: tokens CSS, tipografia, paleta
- [ ] Criar header/navbar cinematográfico com backdrop-blur
- [ ] Hero section full-viewport com animação fade-in
- [ ] Grid de coleções com hover luxury

### Fase 2 — Páginas de Produto (Semana 3–4)
- [ ] PDP com imagem dominante + especificações técnicas
- [ ] Galeria de imagens com zoom cinematográfico
- [ ] Seção de reviews (confiança) com rating gold
- [ ] Adicionar ao carrinho com feedback visual imediato
- [ ] JSON-LD Product schema + metafields SEO

### Fase 3 — Conteúdo & SEO (Semana 5–6)
- [ ] Criar páginas hub (Ternos, Camisas, Acessórios)
- [ ] Produzir 5 spokes editoriais por coleção
- [ ] Configurar metafields `seo.*` em todos os produtos
- [ ] Implementar FAQ sections com FAQPage schema
- [ ] Auditoria Quality Checklist 38 itens

### Fase 4 — Performance & Conversão (Semana 7–8)
- [ ] Core Web Vitals audit e otimização
- [ ] A/B test: 1 CTA vs 2 CTAs no hero
- [ ] Implementar Shop Pay + acelerators de checkout
- [ ] Integrar Google Analytics 4 + Meta Pixel
- [ ] Teste de carga e stress em imagens de produto

---

## 🔗 LINKS & REFERÊNCIAS

### Skills Nexus Aplicadas
- [[🛍️ Skill_Performance_V5]] — Cache I/O, lazy loading, worker pool
- [[✅ Skill_SEO_OnPage_V5]] — Pipeline de pesquisa, chunk 500-token, Quality Checklist
- [[🎨 Skill_Frontend_Design_Elite]] — Hierarquia 60-30-10, padrões de componente
- [[🛍️ Skill_Liquid_Mastery_V5]] — Templates, seções dinâmicas, snippets
- [[🛍️ Skill_Shopify_GraphQL_V5]]   — Queries de produto, paginação, mutations
- [[🛍️ Skill_Shopify_Functions_V5]] — Desconto, entrega, lógica de checkout

### Design Sandbox
- `awesome-design-md/_SANDBOX_DESIGN/Skill_HighEnd_UI_V5.md`
  - Pilar 1: Visual Luxo (Ferrari · Lamborghini · BMW · SpaceX · Tesla)
  - Pilar 3: UX de Engajamento (Airbnb cards adaptados)


---

*Nota criada por Nexus · 2026-04-12 · Skills: Performance V5 + SEO OnPage V5 + High-End UI V5*

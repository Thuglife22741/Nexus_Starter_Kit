---
name: Skill_Supabase_Sync
description: Engine de Sincronização Meta Ads -> Supabase Upserts
type: skill
---

# 🌀 Skill_Supabase_Sync

**Objetivo:** Estabelecer o fluxo de ingestão de dados (Upsert) entre a Graph API do Facebook (Webhooks/Fetch) e o PostgreSQL do Supabase, substituindo o consumo under-the-hood.

### ⚙️ Arquitetura de Sincronização

A lógica deve acontecer no **Backend** (Node.js/Edge Functions), não no Frontend React, por 2 motivos cruciais:
1. **App Secret Proof:** O Facebook confia no `META_APP_SECRET` que nunca pode ir pro front.
2. **Bulk DB Operations:** Muito mais seguro usar a `SERVICE_ROLE_KEY` do Supabase pra ignorar o RLS e escrever os insights.

### 📝 Algoritmo de Upsert (Upsert = Update or Insert)

As métricas do Facebook são retroativas (compras caem em até 7 dias). Portanto, você não pode apenas dar "INSERT" no banco, precisa ser **UPSERT** batendo as Chaves Únicas.

1. **Composite Unique Key na Tabela `daily_insights`:**
   Configure as restrições exclusivas (UNIQUE) na sua tabela do Supabase. Um insight é único por dia, por ad/adset/campaign:
   `UNIQUE(date_start, ad_id)` ou `UNIQUE(date_start, campaign_id)` se os dados forem em nível de campanha.

2. **O fluxo da chamada (Exemplo Node/Edge Function):**
   ```javascript
   import { createClient } from '@supabase/supabase-js'
   
   const supabaseUrl = process.env.VITE_SUPABASE_URL
   const supabaseServiceKey = process.env.SUPABASE_SERVICE_ROLE_KEY
   const supabase = createClient(supabaseUrl, supabaseServiceKey)

   export async function syncDailyInsights(facebookDataArray) {
      // facebookDataArray = array bruto vindo do fetch do GraphAPI
      const payload = facebookDataArray.map(item => ({
         account_id: item.account_id,
         campaign_id: item.campaign_id,
         adset_id: item.adset_id,
         ad_id: item.ad_id,
         date_start: item.date_start,
         spend: item.spend,
         impressions: item.impressions,
         reach: item.reach,
         frequency: item.frequency,
         clicks: item.clicks,
         ctr: item.ctr,
         cpc: item.cpc,
         cpm: item.cpm,
         actions: item.actions || [],
         action_values: item.action_values || [],
         cost_per_action_type: item.cost_per_action_type || [],
         purchase_roas: item.purchase_roas || [],
      }))

      // UPSERT Mágico
      const { data, error } = await supabase
         .from('daily_insights')
         .upsert(payload, { 
             onConflict: 'date_start, ad_id' // Se a chave já existir, ele autaliza os valores!
         })
         
      if (error) throw error
      return data
   }
   ```

### 🔁 Gatilhos de Atualização

Você tem três opções para ativar esse motor:
1. **CRON JOB Diário:** Bater na Meta API 1 vez por dia pra dados históricos completos.
2. **Webhook em Tempo Real:** O Facebook chama sua URL toda vez que algum Lead/Compra cai. *(Menos preciso pra Custos/AdSpend)*.
3. **On-Demand (Ao abrir a tela):** Antes da página renderizar, o Backend faz um Fetch, dá o Upsert, e então o Realtime DB mostra na tela. *(Mais caro/Oneroso na graph api).*

**Caveman Advice:** Use Edge functions rodando via **CRON**. Atualize de hora em hora. É a forma mais barata e estável garantindo paridade.
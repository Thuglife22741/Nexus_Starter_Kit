---
type: blueprint
status: finalizado
created: 2026-05-19
tags:
  - landing-page
  - ecommerce
  - blueprint
---

# ArmorGlass - Landing Page Blueprint

Este projeto atua como o novo modelo padrão (Blueprint) para futuras landing pages de alta conversão, focado em capas de alumínio aeronáutico para iPhone.

## 🛠 Stack Técnica
- **Core**: Vanilla HTML5, CSS3, JavaScript.
- **Otimizações**: Zero dependências de frameworks pesados (sem Tailwind ou Next.js) para máxima velocidade de carregamento.
- **Assets**: Ícones em SVG inline (evitando dependências de CDN de terceiros), carrosséis nativos com temporizador JS leve e CSS puro.

## 📐 Arquitetura da Página (Seções)
1. **Hero**: Vídeo/GIF de alto impacto (`iphone.gif`) com sub-headline premium.
2. **Galeria / Veja Cada Ângulo**: Exibição de ângulos com imagens locais e carrossel dinâmico automático (2s de intervalo, `object-fit: cover`).
3. **Anatomia / Specs do Alumínio Aeronáutico**: Infográfico (`funcoes.png`) explicando os 5 pilares da engenharia aeroespacial.
4. **Oferta (Conversão Agressiva)**:
   - Foco puramente no valor parcelado (ex: 6x de R$ 19,98).
   - Ausência de menções a desconto para PIX para maximizar o ticket percebido.
   - Ordem Otimizada: Botão CTA Principal -> Bandeiras de Cartões (SVG) -> Selos de Confiança (Compra 100% Segura, 7 Dias, Frete Grátis) centralizados no mobile.
5. **FAQ (Dúvidas Frequentes)**: Seção em formato sanfona para contornar objeções finais.

## 🔗 Habilidades Relacionadas e Integrações
- [[UI_Elite]]: Micro-animações (hover), padding harmônico e design dark-mode alinhado ao ecossistema Apple.
- [[Shopify]]: Layout frontend pronto para ser quebrado em snippets/seções no Liquid para temas Shopify futuros.

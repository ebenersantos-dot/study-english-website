# CONVO — Contexto do Projeto

> Este arquivo é lido automaticamente pelo Claude Code ao iniciar uma sessão nesta pasta. Ele carrega o contexto da marca, as decisões de design e as convenções do código. **Sempre consulte-o antes de propor mudanças visuais ou de estrutura.**

---

## 1. O que é a CONVO

Plataforma de aprendizado de inglês focada exclusivamente na prática da conversação. Substitui o modelo passivo de gramática e livros por uma metodologia dinâmica onde o aluno aprende falando em cenários reais.

**Essência da marca:** _"Inglês não se aprende. Se conversa."_

**Posicionamento:** premium-tech humanizada. A CONVO deve ler como produto digital sofisticado (território Notion, Linear, Gemini) — nunca como "curso de inglês online".

---

## 2. O que a CONVO NÃO é (restrições duras)

Ao escrever código, estilos ou copy, **nunca** traga elementos que remetam a:

- Escola tradicional (quadro-negro, cadernos, professor apontando).
- Curso genérico de inglês (bandeiras americana/britânica, livros abertos).
- Marca infantil (cores primárias saturadas, ilustrações cartoon).
- Infoproduto comum (CTAs agressivos em vermelho/amarelo, "GARANTA JÁ").
- Visual barulhento (muitos elementos competindo, gradiente em tudo).
- Estética emocional apelativa (sobreposição de texto em foto, excesso de exclamação).

Símbolos a **evitar**: bandeiras, livros como protagonistas, fones de ouvido como ícone principal, ícones óbvios de ensino, balões de fala com "Hello!" literal.

---

## 3. Sistema de cor (TOKENS — use variáveis CSS, nunca hex hardcoded)

```css
:root {
  /* Primárias — roxo (assinatura da marca) */
  --convo-purple-700: #5A189A;
  --convo-purple-600: #6A1FB0;
  --convo-purple-500: #7B2CBF; /* primary default */
  --convo-purple-400: #9D4EDD;
  --convo-purple-300: #C77DFF;
  --convo-purple-100: #F3E8FF;

  /* Neutros — grafite (estrutura e texto) */
  --convo-graphite-900: #18181B; /* texto principal, nunca usar #000 puro */
  --convo-graphite-800: #27272A;
  --convo-graphite-700: #3F3F46;
  --convo-graphite-500: #71717A;
  --convo-graphite-300: #D4D4D8;
  --convo-graphite-100: #F4F4F5;

  /* Base */
  --convo-white: #FFFFFF;
  --convo-ice: #FAFAFA; /* canvas padrão de fundo */

  /* Suporte */
  --convo-accent-blue: #DCEBFF;
  --convo-success-500: #10B981;
  --convo-success-100: #D1FAE5;

  /* Gradiente de assinatura — USO RESTRITO */
  --convo-gradient-signature: linear-gradient(135deg, #5A189A 0%, #9D4EDD 100%);
}
```

### Regras rígidas de uso de cor

| Regra | Proporção |
|---|---|
| Neutros claros (ice, white, graphite-100) | ~65% da tela |
| Grafite (texto, estrutura) | ~25% |
| Roxo e acentos | ~10% — apenas ação, destaque, memória |

- **Roxo é assinatura, não preenchimento.** Usar em CTAs, links, ícones de ação, hover states, destaque de palavra-chave em título. Nunca em fundos de seção inteiros.
- **Grafite 900 (#18181B), nunca preto puro (#000).** O grafite é mais quente e sofisticado.
- **Gradiente de assinatura:** reservado para momentos-âncora (hero da landing, capa de slide, CTA final de página). Nunca em botões de UI funcional, cards secundários ou fundos de texto corrido.

---

## 4. Sistema tipográfico

```css
:root {
  --font-display: 'Sora', 'Plus Jakarta Sans', -apple-system, system-ui, sans-serif;
  --font-ui: 'Inter', -apple-system, system-ui, sans-serif;
}
```

**Hierarquia** (cole no CSS global):

```css
/* Display / Headings — usa Sora */
.h1 { font-family: var(--font-display); font-weight: 600; font-size: 72px; letter-spacing: -0.03em; line-height: 1.0; }
.h2 { font-family: var(--font-display); font-weight: 600; font-size: 48px; letter-spacing: -0.02em; line-height: 1.1; }
.h3 { font-family: var(--font-display); font-weight: 500; font-size: 32px; letter-spacing: -0.015em; line-height: 1.2; }

/* Subtítulos e labels fortes — Inter SemiBold */
.h4 { font-family: var(--font-ui); font-weight: 600; font-size: 22px; letter-spacing: -0.01em; line-height: 1.3; }

/* Corpo */
.body-l  { font-family: var(--font-ui); font-weight: 400; font-size: 18px; letter-spacing: -0.005em; line-height: 1.5; }
.body-m  { font-family: var(--font-ui); font-weight: 400; font-size: 15px; line-height: 1.5; }

/* UI */
.button  { font-family: var(--font-ui); font-weight: 500; font-size: 15px; }
.caption { font-family: var(--font-ui); font-weight: 600; font-size: 12px; letter-spacing: 0.2em; text-transform: uppercase; }
```

**Regras tipográficas:**
- Títulos H1/H2 com letter-spacing negativo (tracking tight) — dá presença editorial.
- Caption/kicker sempre em caixa alta com letter-spacing 0.2em (20%).
- Nunca misturar mais de duas famílias. Nunca usar serifa, script ou decorativa.
- Para importar Sora e Inter no HTML:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@400;500;600;700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
```

---

## 5. Sistema de espaçamento e forma

- **Radius padrão:** 16px (cards pequenos), 20px (cards médios), 24px (containers grandes), 999px (pills/chips).
- **Nunca cantos retos** (passa sensação corporativa antiquada) **nem ultra-arredondados** (infantil).
- **Respiro extremo:** padding interno de cards começa em 32px. Seção de landing: padding vertical mínimo de 96px.
- **Grid:** max-width de conteúdo 1280px centralizado, com gutters de 24–32px.

---

## 6. Elementos gráficos proprietários

- O **speech bubble** (balão de fala roxo que substitui o "O" em CONVO) é o **DNA visual**. Deve aparecer como ativo — não apenas no logo.
- Derivados do bubble: patterns de fundo em baixa opacidade (3–8%), molduras, containers com cauda, ícones arredondados.
- Ao criar SVGs de ícones: outline ou semi-solid, stroke de 1.5–2px, cantos arredondados, família visualmente coerente com o bubble.

---

## 7. Princípios de código (convenções do projeto)

> _Preencher com o time_. Enquanto estiver vazio, siga os padrões do arquivo existente.

- Estrutura de pastas: `[a documentar]`
- Framework: `[a documentar — ex: React, Next.js, HTML puro]`
- Estilo: `[a documentar — CSS puro, Tailwind, CSS Modules, styled-components]`
- Nomenclatura de classes: `[a documentar — BEM, utility-first, etc.]`

---

## 8. Princípios de decisão (quando houver dúvida)

Quando houver mais de um caminho possível, escolha o que:

1. Reforça **fluidez** (movimento suave, transições curtas, sem fricção).
2. Aumenta **respiro** (mais espaço negativo, não mais elementos).
3. Comunica **clareza** antes de personalidade.
4. Usa **sistema** antes de improviso (tokens existentes, não valores novos).
5. Sugere **conversa** de forma abstrata (fluxos, sobreposição, ritmo), não literal (balões com texto, bandeiras).

> _Se uma decisão não reforça pelo menos um desses cinco, provavelmente é a decisão errada._

---

## 9. Contexto do desenvolvedor

Quem mantém este projeto está aprendendo programação — JavaScript, começando Java, futuramente SQL para backend. Ao sugerir mudanças:

- **Explique o porquê**, não só o como.
- Prefira soluções simples e legíveis a soluções "clevers".
- Quando usar um conceito novo (hook, padrão, API), comente brevemente o que é.
- Ao refatorar, mostre antes e depois lado a lado quando ajudar.

---

## 11. Tom de voz CONVO

### Princípios
1. Confiante e silenciosa — sem exclamação, sem promessas grandiosas
2. Cortante e editorial — frases curtas, cada palavra paga aluguel
3. Técnica sem ser fria — precisa, mas com humanidade
4. Concreta, nunca decorativa — em vez de prometer, descrever

### Banimentos absolutos (nunca usar no copy do site)
- "transforme", "potencialize", "desbloqueie", "revolucione", "alavancar"
- "única no mercado", "metodologia exclusiva", "diferencial competitivo"
- Urgência falsa: "GARANTA JÁ", "ÚLTIMAS VAGAS", caixa alta dramática
- Apelo emocional: "sua vida nunca mais será a mesma"

### Público
- Foco principal: profissional individual (B2C) — gerentes, devs,
  médicos, executivos que precisam do inglês para trabalho real.
- Secundário: empresas (B2B) que querem desenvolver equipes.
- Vocabulário: "você", "sua reunião", "seu cliente".
  Nunca "vocês" ou "alunos".

### Posicionamento de negócio
- Marca construída para escalar (plataforma), não dependente de
  uma pessoa.
- Ebener aparece como fundador, não como protagonista.
- Trate a CONVO sempre como produto/plataforma, nunca como
  "escola do Ebener".

---

## 10. Status do projeto

- ✅ Brand foundation, color system e typography system definidos (Figma: `aQnydcR3u9Kxh7izjQfcpT`).
- 🔜 Graphic elements (speech bubble system).
- 🔜 Aplicação da identidade no site existente.
- 🔜 Templates de social, apresentação.

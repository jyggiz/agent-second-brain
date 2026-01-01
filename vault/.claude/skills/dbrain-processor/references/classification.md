# Entry Classification

## Work Domains → Categories

Based on user's work context (see [ABOUT.md](ABOUT.md)):

### Infoland Work
Внутренние проекты компании: Step2Travel, Aura, будущие продукты

**Keywords:** Step2Travel, Aura, Infoland, команда (Erniaz, Adil), спринт, релиз, презентация руководству, дедлайн проекта

**→ Category:** task (p1) → Todoist → Project: Infoland

### Freelance Work
Фриланс-проекты: партнёрство с Thijs (MediaMonks), клиенты на Upwork

**Keywords:** Thijs, Upwork, клиент, фриланс, CMS (AEM, Contentful, Strapi), freelance project

**→ Category:** task (p3, если дедлайн → p1-p2) → Todoist → Project: Freelance

### Learning & Certifications
Курсы, сертификации, обучение новым технологиям

**Keywords:** NestJS, AWS, AEM, Software Essentialist, курс, сертификация, обучение, документация, туториал

**→ Category:** learning → thoughts/learnings/ или task если с дедлайном → Project: Learning

### AI & Tech
Инструменты, модели, промпты, AI-first разработка, автоматизация

**Keywords:** GPT, Claude, Claude Code, модель, агент, API, пайплайн, автоматизация, интеграция, AI-first, TDD

**→ Category:** learning или project → thoughts/

### Product & SaaS
Идеи, гипотезы, MVP, юнит-экономика, собственные продукты

**Keywords:** продукт, SaaS, MVP, гипотеза, монетизация, юнит-экономика, стартап, business model

**→ Category:** idea или project → thoughts/

### Personal & Family
Семья, здоровье, личное развитие, хобби

**Keywords:** сын, жена, семья, здоровье, медитация, сон, спорт, баня, настольный теннис, личный журнал

**→ Category:** task (p1) → Todoist → Project: Personal

### Blog & Content
Технический блог в Notion, статьи, посты

**Keywords:** блог, статья, пост, Notion, технический контент, tutorial

**→ Category:** idea → thoughts/ideas/ или task если с дедлайном → Project: Blog

---

## Decision Tree

```
Entry text contains...
│
├─ Family/Personal urgent? ──────────────────────> TASK (p1)
│  (сын, жена, семья, здоровье, срочно личное)
│
├─ Infoland projects? ───────────────────────────> TASK (p1)
│  (Step2Travel, Aura, команда, дедлайн проекта)
│
├─ Freelance with deadline? ─────────────────────> TASK (p1-p2)
│  (Thijs, Upwork, дедлайн клиента, срочно)
│
├─ Freelance regular? ───────────────────────────> TASK (p3)
│  (Thijs, Upwork, без дедлайна)
│
├─ Learning/Course work? ────────────────────────> LEARNING или TASK (p3)
│  (NestJS, AWS, AEM, курс, сертификация)
│
├─ AI/tech insight? ─────────────────────────────> LEARNING или PROJECT
│  (Claude Code, агент, автоматизация, AI-first)
│
├─ Product/SaaS idea? ───────────────────────────> IDEA или PROJECT
│  (продукт, MVP, гипотеза, SaaS)
│
├─ Strategic thinking? ──────────────────────────> PROJECT
│  (стратегия, план, R&D, долгосрочно)
│
├─ Personal insight? ────────────────────────────> REFLECTION
│  (понял, осознал, философия, личное развитие)
│
└─ Blog/Content idea? ───────────────────────────> IDEA или TASK (p3)
   (блог, статья, пост, Notion)
```

## Apply Decision Filters

Перед сохранением спроси:

1. **Можно ли это делегировать?**
   - Если да → задача бесполезна для роста, делегируй

2. **Приближает ли это к финансовой независимости?**
   - Влияет на доход, инвестиции, недвижимость?

3. **Помогает ли это стать Lead Solution Engineer?**
   - Развивает экспертизу в full-stack, AI-first, Cloud/DevOps?

4. **Это можно автоматизировать?**
   - Есть ли способ через Claude Code, Codex, CI/CD?

5. **Это масштабируется?**
   - Можно ли применить к нескольким проектам/клиентам?

6. **Отнимает ли это время от семьи?**
   - Если да → обговорено ли с женой? Стоит ли оно того?

Если да на 2+ вопроса (кроме #6) → повысить приоритет.

---

## Photo Entries

For `[photo]` entries:

1. Analyze image content via vision
2. Determine domain:
   - Screenshot клиентского материала → Client Work
   - Схема/диаграмма → AI & Tech или Product
   - Текст/статья → Learning
3. Add description to daily file

---

## Output Locations

| Category | Destination | Priority | Project |
|----------|-------------|----------|---------|
| task (family/personal) | Todoist | p1 | Personal |
| task (Infoland) | Todoist | p1 | Infoland |
| task (freelance deadline) | Todoist | p1-p2 | Freelance |
| task (freelance) | Todoist | p3 | Freelance |
| task (learning deadline) | Todoist | p3 | Learning |
| task (blog deadline) | Todoist | p3 | Blog |
| idea | thoughts/ideas/ | — | — |
| reflection | thoughts/reflections/ | — | — |
| project | thoughts/projects/ | — | — |
| learning | thoughts/learnings/ | — | — |

---

## File Naming

```
thoughts/{category}/{YYYY-MM-DD}-short-title.md
```

Examples:
```
thoughts/ideas/2024-12-16-saas-pricing-model.md
thoughts/projects/2024-12-16-ai-agents-pipeline.md
thoughts/learnings/2024-12-16-claude-mcp-setup.md
```

---

## Thought Structure

Use preferred format:

```markdown
---
date: {YYYY-MM-DD}
type: {category}
domain: {Infoland|Freelance|AI & Tech|Product|Personal|Blog}
tags: [tag1, tag2]
---

## Context
[Что привело к мысли]

## Insight
[Ключевая идея]

## Implication
[Что это значит для карьеры/продукта/финансовой независимости/семьи]

## Next Action
[Конкретный шаг — не абстрактный]
```

---

## Anti-Patterns (ИЗБЕГАТЬ)

При создании мыслей НЕ делать:
- Абстрактные рассуждения без Next Action
- Академическая теория без применения к вашему проекту/продукту
- Повторы без синтеза (кластеризуй похожие!)
- Хаотичные списки без приоритетов
- Задачи типа "подумать о..." (конкретизируй!)

---

## MOC Updates

After creating thought file, add link to:
```
MOC/MOC-{category}s.md
```

Group by domain when relevant:
```markdown
## AI & Tech
- [[2024-12-16-claude-mcp-setup]] - MCP integration

## Product
- [[2024-12-16-saas-pricing-model]] - Pricing research
```

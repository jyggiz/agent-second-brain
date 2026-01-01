# Todoist Integration

## Available MCP Tools

### Reading Tasks
- `get-overview` — all projects with hierarchy
- `find-tasks` — search by text, project, section
- `find-tasks-by-date` — tasks by date range

### Writing Tasks
- `add-tasks` — create new tasks
- `complete-tasks` — mark as done
- `update-tasks` — modify existing

---

## Pre-Creation Checklist

### 1. Check Workload (REQUIRED)

```
find-tasks-by-date:
  startDate: "today"
  daysCount: 7
  limit: 50
```

Build workload map:
```
Mon: 2 tasks
Tue: 4 tasks  ← overloaded
Wed: 1 task
Thu: 3 tasks  ← at limit
Fri: 2 tasks
Sat: 0 tasks
Sun: 0 tasks
```

### 2. Check Duplicates (REQUIRED)

```
find-tasks:
  searchText: "key words from new task"
```

If similar exists → mark as duplicate, don't create.

---

## Priority by Domain

Based on user's work context (see [ABOUT.md](ABOUT.md)):

| Domain | Default Priority | Override |
|--------|-----------------|----------|
| Personal/Family | p1 | — |
| Infoland (Step2Travel, Aura) | p1 | — |
| Freelance (with deadline) | p1-p2 | — |
| Freelance (regular) | p3 | дедлайн → p1-p2 |
| Learning (with deadline) | p3 | срочность → p2 |
| Learning (regular) | p4 | автоматизация/масштаб → p3 |
| Blog/Content (with deadline) | p3 | — |
| AI & Tech / Product | p4 | Decision Filters → p3 |

### Priority Keywords

| Keywords in text | Priority |
|-----------------|----------|
| семья, сын, жена, здоровье (срочно) | p1 |
| Step2Travel, Aura, Infoland, дедлайн проекта | p1 |
| Thijs, Upwork, дедлайн клиента, срочно фриланс | p1-p2 |
| важно, приоритет, до конца недели | p2 |
| нужно, надо, не забыть, фриланс (обычное) | p3 |
| обучение, курс, исследование, долгосрочно | p4 |

### Apply Decision Filters for Priority Boost

If entry matches 2+ filters → boost priority by 1 level:

1. Можно ли это делегировать? (если да → не бустим, делегируем)
2. Приближает ли это к финансовой независимости?
3. Помогает ли это стать Lead Solution Engineer?
4. Это можно автоматизировать?
5. Это масштабируется?
6. Отнимает ли это время от семьи? (если да → проверяем согласование)

---

## Date Mapping

| Context | dueString |
|---------|-----------|
| **Family urgent** | today / tomorrow |
| **Infoland deadline** | exact date |
| **Freelance deadline** | exact date |
| **This week** | friday |
| **Next week** | next monday |
| **Learning/Strategic** | in 7 days |
| **Not specified** | in 3 days |

### Russian → dueString

| Russian | dueString |
|---------|-----------|
| сегодня | today |
| завтра | tomorrow |
| послезавтра | in 2 days |
| в понедельник | monday |
| в пятницу | friday |
| на этой неделе | friday |
| на следующей неделе | next monday |
| через неделю | in 7 days |
| 15 января | January 15 |

---

## Task Creation

```
add-tasks:
  tasks:
    - content: "Task title"
      dueString: "friday"  # MANDATORY
      priority: "p4"       # based on domain
      projectId: "..."     # if known
```

### Task Title Style

User prefers: прямота, ясность, конкретика

✅ Good:
- "Завершить модуль Authentication для Step2Travel"
- "Созвон с Thijs по AEM проекту"
- "Пройти 2 урока NestJS Fundamentals"
- "Еженедельный чек-ин с женой"

❌ Bad:
- "Подумать о Step2Travel"
- "Что-то с Thijs"
- "Разобраться с NestJS"
- "Поговорить с женой"

### Workload Balancing

If target day has 3+ tasks:
1. Find next day with < 3 tasks
2. Use that day instead
3. Mention in report: "сдвинуто на {day} (перегрузка)"

---

## Project Detection

| Keywords | Project |
|----------|---------|
| Step2Travel, Aura, Infoland, команда (Erniaz, Adil) | Infoland |
| Thijs, Upwork, фриланс, клиент, AEM, Contentful, Strapi | Freelance |
| NestJS, курс, AWS, AEM сертификация, обучение, Software Essentialist | Learning |
| сын, жена, семья, здоровье, медитация, сон, баня, теннис | Personal |
| блог, статья, пост, Notion, технический контент | Blog |

If unclear → use Inbox (no projectId).

---

## Anti-Patterns (НЕ СОЗДАВАТЬ)

Based on user preferences:

- ❌ "Подумать о..." → конкретизируй действие
- ❌ "Разобраться с..." → что именно сделать?
- ❌ Абстрактные задачи без Next Action
- ❌ Дубликаты существующих задач
- ❌ Задачи без дат

---

## Error Handling

CRITICAL: Никогда не предлагай "добавить вручную".

If `add-tasks` fails:
1. Include EXACT error message in report
2. Continue with next entry
3. Don't mark as processed
4. User will see error and can debug

WRONG output:
  "Не удалось добавить (MCP недоступен). Добавь вручную: Task title"

CORRECT output:
  "Ошибка создания задачи: [exact error from MCP tool]"

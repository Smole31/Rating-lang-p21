# Рейтинг мов програмування — Варіант 18

## Структура проекту

```
project/
├── server/
│   ├── package.json
│   └── index.js        <- Express API (GET + POST + валідація + CORS)
│
└── client/
    ├── index.html
    ├── vite.config.js
    ├── package.json
    └── src/
        ├── main.jsx    <- точка входу React
        ├── App.jsx     <- компонент з useState, useEffect, форма
        └── index.css   <- стилізація
```

---

## Як запустити

Відкрийте два термінали.

**Термінал 1 — сервер:**
```bash
cd server
npm install
node index.js
```
Сервер працює на http://localhost:3001

**Термінал 2 — клієнт:**
```bash
cd client
npm install
npm run dev
```
Відкрийте http://localhost:5173 у браузері.

---

## API сервера

| Метод | URL        | Що робить                              |
|-------|------------|----------------------------------------|
| GET   | /api/votes | Повертає голоси, відсотки та журнал    |
| POST  | /api/votes | Приймає голос та зберігає його         |

**Тіло POST-запиту:**
```json
{
  "language": "JavaScript",
  "voter": "Іван"
}
```

**Правила валідації:**
- `language` — обов'язкове, рядок, мін. 2 символи, лише: JavaScript / Python / C++
- `voter` — необов'язкове, рядок, мін. 2 символи або порожнє

---

## Що реалізовано

**Сервер (Node.js + Express):**
- GET /api/votes — повертає список мов з кількістю голосів та відсотками
- POST /api/votes — зберігає голос після перевірки
- Валідація: тип даних, мінімальна довжина, дозволені значення
- CORS дозволяє запити з http://localhost:5173
- Синтаксис ESM (import/export)

**Клієнт (React + Vite):**
- useState — зберігає дані, стан форми, повідомлення
- useEffect — викликає fetchData при завантаженні сторінки
- Контрольовані інпути (value + onChange)
- Після голосування список і журнал оновлюються без перезавантаження

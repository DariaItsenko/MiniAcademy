# 🚀 Інструкція з розгортання сайту

## Метод 1: Vercel (РЕКОМЕНДОВАНО) ✨

**Vercel** - це безкоштовний хостинг для веб-додатків. Найпростіший спосіб!

### Крок 1: Створіть акаунт на Vercel

1. Перейдіть на https://vercel.com
2. Натисніть "Sign Up" (Зареєструватися)
3. Виберіть "Continue with GitHub" (або Email)

### Крок 2: Завантажте ваш проект на GitHub

1. Створіть акаунт на https://github.com (якщо ще немає)
2. Натисніть "+" → "New repository"
3. Дайте назву проекту (наприклад, "education-app")
4. Натисніть "Create repository"

### Крок 3: Завантажте файли проекту

У терміналі (або Git Bash) виконайте:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/ВАШ_ЮЗЕРНЕЙМ/education-app.git
git push -u origin main
```

### Крок 4: Розгорніть на Vercel

1. Увійдіть на https://vercel.com
2. Натисніть "Add New..." → "Project"
3. Виберіть ваш репозиторій з GitHub
4. Натисніть "Import"
5. **ВАЖЛИВО:** Додайте змінні оточення (Environment Variables):
   - `SUPABASE_URL` = ваш Supabase URL
   - `SUPABASE_ANON_KEY` = ваш Supabase Anon Key
   - `SUPABASE_SERVICE_ROLE_KEY` = ваш Supabase Service Role Key
6. Натисніть "Deploy"

### ✅ Готово!

Через 1-2 хвилини ваш сайт буде доступний за посиланням типу:
`https://education-app.vercel.app`

---

## Метод 2: Netlify 🌐

### Крок 1: Створіть акаунт

1. Перейдіть на https://netlify.com
2. Натисніть "Sign up"
3. Виберіть "Continue with GitHub"

### Крок 2: Завантажте проект (якщо ще не зробили)

Виконайте кроки з Методу 1 для завантаження на GitHub.

### Крок 3: Розгорніть на Netlify

1. Увійдіть на https://app.netlify.com
2. Натисніть "Add new site" → "Import an existing project"
3. Виберіть "Deploy with GitHub"
4. Виберіть ваш репозиторій
5. Налаштування збірки:
   - Build command: `npm run build`
   - Publish directory: `dist`
6. Додайте змінні оточення (як у Vercel)
7. Натисніть "Deploy site"

### ✅ Готово!

Ваш сайт буде доступний за посиlanням типу:
`https://your-site-name.netlify.app`

---

## Метод 3: Швидкий деплой через Vercel CLI 🚀

### Встановіть Vercel CLI

```bash
npm install -g vercel
```

### Розгорніть сайт

```bash
vercel
```

Відповідайте на запитання:
- Set up and deploy: `Y`
- Which scope: виберіть ваш акаунт
- Link to existing project: `N`
- What's your project's name: `education-app`
- In which directory: `./`
- Want to override: `N`

### Додайте змінні оточення

```bash
vercel env add SUPABASE_URL
vercel env add SUPABASE_ANON_KEY
vercel env add SUPABASE_SERVICE_ROLE_KEY
vercel env add RESEND_API_KEY
```

### Фінальний деплой

```bash
vercel --prod
```

---

## ⚙️ Налаштування Supabase для продакшну

Після розгортання вам потрібно оновити налаштування Supabase:

1. Перейдіть на https://supabase.com
2. Відкрийте ваш проект
3. Йдіть в "Settings" → "API"
4. Скопіюйте:
   - Project URL (SUPABASE_URL)
   - Project API keys → anon public (SUPABASE_ANON_KEY)
   - Project API keys → service_role (SUPABASE_SERVICE_ROLE_KEY)

### Оновіть CORS налаштування

1. В Supabase йдіть в "Settings" → "API"
2. Додайте URL вашого сайту (наприклад, `https://education-app.vercel.app`) до списку дозволених Origins

---

## 🔧 Важливі налаштування

### Оновіть файл `/utils/supabase/info.tsx`

Після розгортання переконайтеся, що ваш файл `info.tsx` містить правильні дані:

```typescript
export const projectId = 'akvkqgxbckbygzcfcuoy';
export const publicAnonKey = 'ваш_anon_key';
```

---

## 📝 Checklist перед деплоєм

- [ ] Всі змінні оточення додані
- [ ] Supabase налаштований
- [ ] Email API ключ доданий (якщо використовується)
- [ ] Build команда працює локально: `npm run build`
- [ ] Всі файли закомічені в Git

---

## 🆘 Вирішення проблем

### Помилка "Module not found"

```bash
npm install
npm run build
```

### Помилка з Supabase

Перевірте, що всі змінні оточення правильно додані в налаштуваннях Vercel/Netlify.

### Сайт не завантажується

1. Перевірте логи на Vercel/Netlify
2. Переконайтеся, що build пройшов успішно
3. Перевірте Console в браузері (F12) для помилок

---

## 🎉 Готово!

Ваш освітній додаток тепер доступний онлайн! Поділіться посиланням з учнями та батьками.

**Корисні посилання:**
- Vercel документація: https://vercel.com/docs
- Netlify документація: https://docs.netlify.com
- Supabase документація: https://supabase.com/docs

---

## 📱 Оновлення сайту

Після кожного оновлення коду:

```bash
git add .
git commit -m "Опис змін"
git push
```

Vercel/Netlify автоматично розгорне нову версію!

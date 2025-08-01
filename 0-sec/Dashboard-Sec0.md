---
created: 2025-07-30T22:02
updated: 2025-07-30T23:18
---
# 🚨 Dashboard Sec-0 - کارهای جزئی و بدون طبقه‌بندی

## 📊 خلاصه وضعیت
```dataview
TABLE 
  file.name as "پروژه",
  choice(contains(file.content, "📅 2025.07.30"), "⏰ امروز", "📅 بدون ددلاین") as "ددلاین",
  choice(contains(file.content, "- [ ]"), "🔴 فعال", "✅ تکمیل") as "وضعیت"
FROM "sec-0"
SORT file.name ASC
```

## 🎯 تسک‌های WHNN در Sec-0
```datacards
path includes sec-0
tags include #whnn
not done
sort by due date
```

## ⏰ تسک‌های امروز (ددلاین)
```tasks
path includes sec-0
due today
not done
sort by priority
```

## 📋 همه تسک‌های Sec-0
```tasks
path includes sec-0
not done
group by filename
```

## 📈 آمار کلی
```dataview
TABLE 
  length(filter(file.tasks, (t) => !t.completed)) as "تسک‌های فعال",
  length(filter(file.tasks, (t) => t.completed)) as "تسک‌های تکمیل شده",
  choice(length(filter(file.tasks, (t) => t.due = date(today) AND !t.completed)) > 0, "🔴 ددلاین امروز!", "🟢 بدون ددلاین فوری") as "وضعیت ددلاین"
FROM "sec-0"
WHERE file.tasks
```

---
*آخرین به‌روزرسانی: 2025.07.30*
*مسیر: Dashboard برای نمایش تسک‌های Sec-0 با تگ WHNN*
# Video darslik sotish boti

Node.js ([grammY](https://grammy.dev)) va SQLite asosidagi Telegram bot. Node.js 22.13 yoki undan yuqori versiya kerak.

## Ishga tushirish

1. [@BotFather](https://t.me/BotFather) orqali bot yarating va tokenni oling.
2. Botni majburiy obuna kanaliga **admin** qilib qo'shing (aks holda bot obunani tekshira olmaydi va ishga tushmaydi).
3. O'z Telegram ID raqamingizni [@userinfobot](https://t.me/userinfobot) orqali bilib oling.
4. `.env` faylini to'ldiring (namuna: `.env.example`):

   | O'zgaruvchi | Tavsif |
   |---|---|
   | `BOT_TOKEN` | BotFather bergan token |
   | `ADMIN_IDS` | Admin ID raqamlari, vergul bilan |
   | `CHANNEL_ID` | Kanal: `@username` yoki `-100...` |
   | `CHANNEL_URL` | Faqat yopiq kanal uchun: taklif havolasi |
   | `DB_PATH` | Baza fayli (standart: `./data/bot.db`) |

5. Ishga tushiring:

   ```
   npm install
   npm start
   ```

6. Telegram'da botga `/start` yuboring. Admin so'rovlarni olishi uchun ham botni bir marta start qilishi kerak.

## Birinchi sozlash (admin)

`⚙️ Admin panel` tugmasi yoki `/admin` buyrug'i orqali:

1. **💳 To'lov sozlamalari**: karta raqami, karta egasi va skrinshot qabul qiladigan admin username'i.
2. **➕ Kurs qo'shish**: nom → ma'lumot → narx → video darslar.

Videolarni botga to'g'ridan-to'g'ri yuborasiz. Ular Telegram serverlarida saqlanadi va baza faqat ularning `file_id` sini eslab qoladi.

## Ish jarayoni

1. Foydalanuvchi `/start` bosadi: xush kelibsiz xabari va majburiy obuna so'rovi chiqadi.
2. Obunadan so'ng `📚 Kurslar` → kurs → `💳 Sotib olish`: karta raqami, summa va admin username'i ko'rsatiladi.
3. Foydalanuvchi to'lov qilib, `✅ To'ladim` tugmasini bosadi va skrinshotni admin username'iga yuboradi.
4. Adminga `✅ Tasdiqlash` / `❌ Bekor qilish` tugmali so'rov keladi. Javob yo'qolgan bo'lsa, so'rov `⏳ Kutilayotgan to'lovlar` bo'limida turadi.
5. Tasdiqlansa, videolar foydalanuvchiga himoyalangan holda (uzatib bo'lmaydigan) yuboriladi va `🎓 Mening kurslarim` bo'limida qoladi. Bekor qilinsa, foydalanuvchiga xabar boradi.

Bot to'lovni o'zi tekshirmaydi: `To'ladim` tugmasi faqat so'rov yuboradi. Tasdiqlashdan oldin pul kartaga tushganini tekshiring.

## Test

```
npm test
```

## Muhim

- `.env` va `data/` papkasini hech kimga bermang va git'ga qo'shmang.
- `data/bot.db` faylida xaridlar saqlanadi, undan muntazam zaxira nusxa oling.
- Bot doimiy ishlashi uchun uni server (VPS) yoki doimiy yoniq kompyuterda ishga tushiring.

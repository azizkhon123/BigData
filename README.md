# 📘 LOYIHA: O‘zbekiston ta’lim tizimi statistikasi tahlili
# 🎯 Maqsad: O‘zbekiston ta’lim tizimi bo‘yicha statistik ma’lumotlarni tahlil qilish,
#           turli ta’lim bosqichlari (boshlang‘ich, o‘rta, oliy) o‘quvchi/ta’lim oluvchilar sonini solishtirish
#           va umumiy tendensiyalarni aniqlash.

# 10️⃣ Ma'lumotlarni saqlash va yakuniy hisobot tayyorlash

import pandas as pd
from google.colab import files

# 10.1 Tozalangan va tayyorlangan ma'lumotlarni CSV faylga saqlash
output_csv = "education_statistics_cleaned.csv"
df.to_csv(output_csv, index=False)
print(f"✅ Ma'lumotlar '{output_csv}' fayliga saqlandi.")

# 10.2 Excel formatida ham saqlash
output_excel = "education_statistics_cleaned.xlsx"
df.to_excel(output_excel, index=False)
print(f"✅ Ma'lumotlar '{output_excel}' fayliga saqlandi.")

# 10.3 Hisobot tayyorlash (asosiy statistika)
report = {
    "📚 Loyiha nomi": "O‘zbekiston ta’lim tizimi statistikasi tahlili",
    "🎯 Maqsad": "O‘zbekiston ta’lim tizimi bo‘yicha turli darajadagi ta’lim oluvchilar sonini tahlil qilish.",
    "Jami qatorlar soni": len(df),
    "Ustunlar soni": len(df.columns),
    "Raqamli ustunlar": list(df.select_dtypes(include='number').columns),
    "O'rtacha Primary_Students": round(df['Primary_Students'].mean(), 2),
    "O'rtacha Secondary_Students": round(df['Secondary_Students'].mean(), 2),
    "O'rtacha Higher_Students": round(df['Higher_Students'].mean(), 2),
}

print("\n📊 HISOBOT:")
for k, v in report.items():
    print(f"{k}: {v}")

# 10.4 Colab uchun fayllarni yuklab olish
files.download(output_csv)
files.download(output_excel)

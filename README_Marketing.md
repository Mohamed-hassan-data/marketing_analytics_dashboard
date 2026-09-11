# Marketing Campaign Analysis Dashboard

تحليل بيانات الحملات الإعلانية باستخدام **Power BI**، بيهدف لتحويل بيانات خام (CSV) لتقرير تفاعلي بيساعد في تقييم أداء الحملات عبر المنصات المختلفة واتخاذ قرارات تسويقية مبنية على بيانات.

---

## 📊 نظرة عامة

المشروع بيحلل بيانات حملات إعلانية شغالة على منصات مختلفة (Facebook, Google, Instagram, X)، وبيقيس أداءها من حيث الظهور، الضغط، التحويلات، والقيمة المالية الناتجة.

---

## 🗂️ Data Model (Star Schema)

**Fact Table — Marketing:**
| العمود | النوع |
|---|---|
| Impressions, Clicks, Conversions, ConversionValue | Measures |

**Dimension Tables:**
| الجدول | الأعمدة |
|---|---|
| Dim_Customer | CustomerID, AgeGroup, Gender, Country |
| Dim_Product | ProductCategory |
| Dim_Campaign | CampaignID, AdPlatform |
| Dim_Date | DateTime |

---

## 🧮 أهم DAX Measures

```dax
Total Impressions = SUM(DataMarketing[Impressions])
Total Clicks = SUM(DataMarketing[Clicks])
Total Conversions = SUM(DataMarketing[Conversions])
Total Conversion Value = SUM(DataMarketing[ConversionValue])

CTR (Click Rate) = 
DIVIDE([Total Clicks], [Total Impressions])

Conversion Rate = 
DIVIDE([Total Conversions], [Total Clicks])

Total Customers = DISTINCTCOUNT(DataMarketing[CustomerID])
Total Campaigns = DISTINCTCOUNT(DataMarketing[CampaignID])
```

---

## 📈 الـ Visuals في الداشبورد

- **KPI Cards:** Total Clicks, Conversion Rate, Total Campaigns, Click Rate, Total Conversion Value
- **Table:** أداء كل AdPlatform تفصيليًا (Clicks, Conversion Rate, Total Customers)
- **Line Chart:** Conversion Value Over Time
- **Pie Chart:** Number of Campaigns by Platform
- **Bar Chart:** Total Conversion Value by ProductCategory
- **Bar Chart:** Total Conversion Value by Country
- **Slicers:** Platform, Country, Category, Age Group

---

## 🛠️ الأدوات المستخدمة

- Power BI Desktop (Data Modeling, DAX, Visualization)
- Power Query (Data Cleaning & Transformation)

---

## 📁 محتويات الريبو

```
├── data/                  # ملف CSV الخام (DataMarketing)
├── PowerBI/               # ملف .pbix
├── screenshots/           # صور الداشبورد
└── README.md
```

---

## ✨ أبرز الـ Insights

- **جوجل وفيسبوك** حققوا أعلى معدلات تفاعل وتحويل (Conversion Rate) مقارنة بتويتر وانستجرام.
- **Smartphones** هي الفئة الأعلى في Conversion Value (128K).
- **ألمانيا وأستراليا** من أعلى الدول في قيمة التحويلات.
- معدل التحويل الإجمالي (Overall Conversion Rate) وصل لـ 30.97%.

---

## 🔍 Interactivity Features

- **Tooltips:** عند عمل Hover على أي عمود في الشارتس، بيظهر Card بتفاصيل إضافية عن القيمة (زي Platform والـ Total Clicks/Conversion Value الخاصة بيه).
- **Drill Through:** من جدول أداء المنصات، تقدر تعمل Right-click على أي صف (مثلاً Facebook) وتختار **Drill Through → Page 3** للانتقال مباشرة لصفحة تفاصيل خاصة بالمنصة دي.

---

## 💡 التوصيات (Recommendations)

بناءً على تحليل الأداء عبر المنصات، النتائج بتوضح إن **Google وFacebook** حققوا أعلى معدلات تحويل (Conversion Rate) وأعلى قيمة تحويلات (Conversion Value) مقارنة بـ Twitter/X وInstagram.

**التوصية:** إعادة توزيع الميزانية الإعلانية بزيادة الإنفاق على حملات Google وFacebook، مع تقليل الاعتماد النسبي على المنصات الأقل أداءً، وده بناءً على:

- **Google:** أعلى Conversion Value (164,874) وأعلى Click Rate (10.16%)
- **Facebook:** ثاني أعلى Conversion Value (96,297) بعدد Clicks كبير (1,162)

كمان على مستوى الدول، **ألمانيا وأستراليا** حققوا أعلى قيمة تحويلات (75K و72K على التوالي)، فيُنصح بتوجيه جزء أكبر من الميزانية الإعلانية للسوقين دول أيضًا، خصوصًا لو الحملات على Google وFacebook.

**قبل التنفيذ الكامل، يُنصح بـ:**
- تجربة زيادة تدريجية في الميزانية (A/B Testing) بدل تحويل كامل ومفاجئ.
- مراقبة الأداء على مدار فترة زمنية أطول للتأكد إن الاتجاه ثابت مش مؤقت.
- الأخذ في الاعتبار حجم الـ Impressions لكل منصة، عشان نتأكد إن المعدلات العالية ممثلة إحصائيًا وليست نتيجة عينة صغيرة.

---

## 👤 إعداد

تم بناء وتحليل المشروع باستخدام Power BI بالكامل (Data Modeling + DAX + Visualization).

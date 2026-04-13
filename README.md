# 🧠 Analyzing Students' Mental Health — SQL Analysis

## Project Overview
A SQL analysis project investigating how length of stay at a Japanese
university affects the mental health of international students.
Written using 12 MySQL queries across 286 student survey records — from
basic aggregations to subqueries and JOINs. The project answers one
central question: does staying longer actually help?

**Tool:** MySQL / SQLite  
**Dataset:** International student survey · Japanese university ·
286 students · 50 variables  
**Author:** Neel Shah | [LinkedIn](https://linkedin.com/in/neel-shah-654a1b27b)

---

## 📊 Dataset
| Column | Description | Scale |
|--------|-------------|-------|
| inter_dom | International or Domestic student | Inter / Dom |
| Stay | Years at the university | 1 – 10 |
| ToDep | Depression score | 0–25 (higher = worse) |
| ToSC | Social connectedness score | 0–48 (higher = better) |
| ToAS | Acculturative stress score | 0–145 (higher = worse) |
| Gender | Male / Female | — |
| Academic | Undergraduate / Graduate | Under / Grad |
| Japanese_cate | Japanese language proficiency | Low / Average / High |
| English_cate | English language proficiency | Low / Average / High |
| Region | World region of origin | SEA / EA / SA / Others |

---

## 🔍 Key Findings

| Finding | Insight |
|---------|---------|
| 📈 Year 3 = crisis point | Depression rises 21% from Year 1 (7.48) to Year 3 (9.09) |
| 😊 Year 1 is healthiest | New students arrive optimistic — struggle sets in after Year 2 |
| 📉 Social bonds weaken | Connectedness drops from 38.11 (Year 1) to 33.93 (Year 4) |
| 😰 Stress peaks at Year 4 | Acculturative stress hits 87.71 — the highest in the dataset |
| 🗣️ Language protects | Higher Japanese & English proficiency = lower depression |
| 🎓 Graduates cope better | Grad students show 41% lower depression (4.95 vs 8.39) |
| 🚨 Help gap | Professional help scores LOWEST of all support sources (2.89/5) |

---

## 🗃️ SQL Skills Demonstrated

```sql
-- Example: Subquery — students above average depression
SELECT Gender, Stay, ToDep
FROM students
WHERE inter_dom = 'Inter'
  AND ToDep > (
    SELECT AVG(ToDep)
    FROM students
    WHERE inter_dom = 'Inter'
  )
ORDER BY ToDep DESC;
```

**Full skill list:**
SELECT · FROM · WHERE · GROUP BY · ORDER BY · HAVING ·
AVG() · COUNT() · ROUND() · MIN() · MAX() · Subqueries ·
JOIN · IN · BETWEEN · DISTINCT · LIKE

---

## 📈 Query Progression

| Query | Question | Skills |
|-------|----------|--------|
| 1 | How long do students stay? | COUNT(), GROUP BY, ORDER BY |
| 2 | What are the overall mental health averages? | AVG(), ROUND() |
| 3 | How does stay length affect all 3 scores? | GROUP BY, multi-AVG() |
| 4 | Which students have severe depression? | WHERE, IN, ORDER BY |
| 5 | Does gender affect mental health? | GROUP BY gender, AVG() |
| 6 | Do graduates cope better than undergrads? | GROUP BY academic level |
| 7 | Does language proficiency help? | IN, GROUP BY, AVG() |
| 8 | Which regions struggle most? | HAVING, GROUP BY region |
| 9 | Who scores above average depression? | Subquery |
| 10 | Where do students seek help? | AVG() on support columns |
| 11 | International vs Domestic comparison | GROUP BY, JOIN logic |
| 12 | What year is the actual crisis point? | Subquery + HAVING |

---

## 📊 Presentation
Two presentation versions included:
- **Dark Navy version** — SQL-focused with syntax-highlighted code blocks
- **White Editorial version** — Research paper style, Georgia serif font

Both are 9 slides covering: Dataset overview → Core analysis →
Severity levels → Gender → Academic level → Language → Regional →
Help-seeking behaviour → Executive conclusions

---

## 💼 Business / Policy Recommendations
1. **Target Year 3 students** — run mental health check-ins at the start of Year 3
2. **Language integration programs** — language skills directly reduce depression
3. **Graduate support models** — study what makes graduates more resilient
4. **Lower barriers to professional help** — it scores lowest despite being most needed
5. **Region-specific support** — SEA and EA students show the highest depression rates

---

## 📁 Files in This Repository

├── mental_health_SQL_project.sql        # 12 queries with full comments

├── mental_health_presentation.pptx      # Dark navy 9-slide version

├── mental_health_white_editorial.pptx   # White editorial 9-slide version

└── README.md

---

## 🚀 How to Run
1. Create a `students` table using the schema at the top of the `.sql` file
2. Load the dataset CSV using your database tool's import function
3. Run queries from top to bottom — each is self-contained with
   expected results in comments

**Dataset source:** Available on DataCamp and Kaggle — search
"International Students Mental Health Japanese University"

---

## 📌 Note on the Data
18 rows had missing values across all key columns and were excluded.
The final analysis uses **201 international students** (of 286 total).
Domestic students (67) are included in comparative queries only.

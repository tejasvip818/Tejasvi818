# Python for Data Engineering — Step by Step

**Kaise use karna hai:** Har din pehle concept padhiye, example khud type kariye (copy-paste nahi), phir practice problems solve kariye. Concept yahin diya hua hai — bahar kuch dhoondhne ki zaroorat nahi.

**Roz ka time:** 20-30 min
**Rule:** Solution 20 min khud try karne ke baad hi dekhna hai.

---

# PART 1 — BUNIYAD (Day 1-8)

---

## Day 1: Variables aur Data Types

### Concept

Python mein variable banane ke liye type likhne ki zaroorat nahi.

```python
name = "Tejasvi"        # str  — text
age = 30                # int  — poora number
salary = 55000.50       # float — decimal wala number
is_active = True        # bool — True / False
```

Type check karna:
```python
print(type(name))       # <class 'str'>
```

Type badalna (ye DE mein roz kaam aata hai, kyunki file se sab kuch string aata hai):
```python
x = "100"
y = int(x)              # string se int
z = float("55.5")       # string se float
s = str(100)            # int se string
```

Print karne ka aasan tareeka (f-string):
```python
print(f"{name} ki salary {salary} hai")
```

### Practice
1. Apna naam, umar, salary teen variables mein rakhiye aur f-string se print kariye.
2. `"250"` string ko int mein badal kar usme 50 jodiye.
3. `type()` se chaaron variables ka type print kariye.
4. Ek float `55.99` ko int mein badliye — dekhiye kya hota hai (decimal kat jaata hai).

---

## Day 2: Strings

### Concept

String ke andar ke characters position se milte hain (0 se shuru):

```python
s = "DataEngineer"
print(s[0])       # D
print(s[-1])      # r  (aakhri)
print(s[0:4])     # Data  (0 se 3 tak, 4 nahi)
print(s[4:])      # Engineer
```

Kaam ke functions:
```python
s.upper()             # DATAENGINEER
s.lower()             # dataengineer
s.strip()             # aage-peeche ke spaces hatata hai
s.replace("Data","Big")
s.split(",")          # string ko list mein todta hai
len(s)                # length
"gineer" in s         # True/False
```

`split()` DE mein bahut kaam aata hai — CSV ki line todne ke liye:
```python
line = "101,Tejasvi,Bengaluru"
parts = line.split(",")     # ['101', 'Tejasvi', 'Bengaluru']
```

### Practice
5. `"  hello world  "` se spaces hata kar uppercase mein print kariye.
6. `"tejasvi@gmail.com"` se username aur domain alag kariye (`split("@")` se).
7. Ek string ko reverse kariye — `s[::-1]` use karke.
8. `"101,Tejasvi,55000"` ko todkar teen alag variables mein daaliye.
9. Ek sentence mein kitne words hain, count kariye.
10. Ek string mein kitne vowels hain, count kariye (loop se).

---

## Day 3: Lists

### Concept

List = ek se zyada cheezein, ek jagah. Order hota hai, badal sakte hain.

```python
nums = [10, 25, 3, 47, 8]
names = ["Amit", "Riya", "Sanjay"]

nums[0]           # 10
nums[-1]          # 8
nums[1:3]         # [25, 3]
```

Kaam ke operations:
```python
nums.append(99)         # end mein add
nums.insert(0, 5)       # position pe add
nums.remove(3)          # value hataye
nums.pop()              # aakhri hataye
len(nums)               # kitne items
sorted(nums)            # naya sorted list
nums.sort()             # usi list ko sort
nums.sort(reverse=True) # descending
sum(nums), max(nums), min(nums)
```

### Practice
11. `[10, 25, 3, 47, 8]` ka sum, max, min, average nikaliye.
12. Wahi list ascending aur descending sort kariye.
13. List mein 100 add kariye aur 3 hata dijiye.
14. `[1,2,2,3,3,3,4]` se duplicates hata dijiye (hint: `set()` use kar sakte hain).
15. Do lists ke common elements nikaliye.
16. Ek list ka second highest number nikaliye (bina `sort()` ke, loop se try kariye).

---

## Day 4: Dictionary (DE mein sabse zyada use hoti hai)

### Concept

Dictionary = key aur value ka jodaa. Ek row ko represent karne ka best tareeka.

```python
emp = {
    "emp_id": 101,
    "name": "Tejasvi",
    "dept": "QA",
    "salary": 55000
}

emp["name"]              # Tejasvi
emp["salary"] = 60000    # update
emp["city"] = "Bengaluru"  # naya key add
del emp["dept"]          # delete
```

Safe access — agar key na ho toh error nahi aayega:
```python
emp.get("bonus")           # None
emp.get("bonus", 0)        # 0  (default value)
"name" in emp              # True
```

Loop chalana:
```python
for key, value in emp.items():
    print(key, "->", value)

emp.keys()      # saare keys
emp.values()    # saari values
```

### Practice
17. Ek employee dict banaiye (id, name, dept, salary) aur `items()` se poora print kariye.
18. Salary 10% badha dijiye.
19. `get()` se ek aisa key access kariye jo exist nahi karta — default 0 dijiye.
20. Dict mein ek naya key add kariye aur ek delete kariye.
21. Sirf un keys ko print kariye jinki value number hai (`isinstance(v, int)` use kar sakte hain).

---

## Day 5: List of Dictionaries (ye ek "table" hai)

### Concept

DE mein data aise hi aata hai — har row ek dict, saari rows ek list.

```python
employees = [
    {"id": 1, "name": "Amit",   "dept": "QA",  "salary": 50000},
    {"id": 2, "name": "Riya",   "dept": "DE",  "salary": 80000},
    {"id": 3, "name": "Sanjay", "dept": "QA",  "salary": 60000},
]

for e in employees:
    print(e["name"], e["salary"])
```

Filter (SQL ka `WHERE`):
```python
high_earners = []
for e in employees:
    if e["salary"] > 55000:
        high_earners.append(e)
```

Group by (SQL ka `GROUP BY`):
```python
dept_total = {}
for e in employees:
    d = e["dept"]
    dept_total[d] = dept_total.get(d, 0) + e["salary"]
# {'QA': 110000, 'DE': 80000}
```

Ye `get(d, 0)` wala pattern DE mein baar-baar aayega — yaad rakhiye.

### Practice
22. 5 employees ki list banaiye.
23. Sabke naam print kariye.
24. Salary > 55000 wale filter kariye.
25. Department-wise total salary nikaliye.
26. Department-wise employee count nikaliye.
27. Sabse zyada salary wale employee ka naam nikaliye.
28. Salary ke hisaab se list sort kariye (hint: `sorted(employees, key=lambda x: x["salary"])`).

---

## Day 6: Conditions aur Loops

### Concept

```python
salary = 60000

if salary > 70000:
    grade = "High"
elif salary > 50000:
    grade = "Medium"
else:
    grade = "Low"
```

Loop:
```python
for n in [1,2,3,4,5]:
    print(n)

for i in range(5):        # 0,1,2,3,4
    print(i)

for i in range(1, 11):    # 1 se 10
    print(i)
```

`break` loop todta hai, `continue` us chakkar ko skip karta hai:
```python
for n in nums:
    if n < 0:
        continue          # negative skip
    if n > 100:
        break             # loop band
```

### Practice
29. 1 se 100 tak wo numbers print kariye jo 3 aur 5 dono se divisible hain.
30. Ek list mein har element kitni baar aaya, dict mein count kariye.
31. Ek list of salaries ko loop se grade dijiye (High/Medium/Low).
32. Ek list se pehla negative number milte hi loop tod dijiye.
33. Ek string mein har character ki frequency nikaliye.

---

## Day 7: Functions

### Concept

Function = code ka ek tukda jise baar-baar use kar sakein.

```python
def get_average(numbers):
    if len(numbers) == 0:
        return 0
    return sum(numbers) / len(numbers)

avg = get_average([10, 20, 30])
```

Default value:
```python
def give_hike(salary, percent=10):
    return salary + (salary * percent / 100)

give_hike(50000)        # 10% default
give_hike(50000, 20)    # 20%
```

`*args` (kitne bhi arguments) aur `**kwargs` (named arguments):
```python
def total(*nums):
    return sum(nums)

total(1, 2, 3, 4)       # 10
```

Lambda — ek line ka chhota function:
```python
square = lambda x: x * x
sorted(employees, key=lambda e: e["salary"])
```

### Practice
34. Ek function likhiye jo list le aur average return kare.
35. Ek function jo string le aur palindrome hai ya nahi bataye.
36. Ek function jo employees list aur dept le, aur us dept ke employees return kare.
37. Ek function jo employees list le aur dept-wise average salary ka dict return kare.
38. Ek function jo `*args` le aur sabka sum kare.
39. Lambda se employees ko salary ke hisaab se descending sort kariye.

---

## Day 8: Comprehensions

### Concept

Loop ka chhota roop — DE aur PySpark mein bahut milega.

```python
# Purana tarika
squares = []
for n in range(1, 6):
    squares.append(n * n)

# Comprehension
squares = [n * n for n in range(1, 6)]      # [1,4,9,16,25]
```

Condition ke saath:
```python
evens = [n for n in nums if n % 2 == 0]
names = [e["name"] for e in employees]
high  = [e["name"] for e in employees if e["salary"] > 55000]
```

Dict comprehension:
```python
sal_map = {e["name"]: e["salary"] for e in employees}
```

### Practice
40. 1-20 tak ke squares ki list banaiye (one line).
41. Ek list se sirf even numbers nikaliye.
42. Employees se sirf naamon ki list banaiye.
43. Employees se `{name: salary}` ka dict banaiye.
44. Sirf QA department wale naam nikaliye.

---

# PART 2 — FILE AUR DATA HANDLING (Day 9-14)

---

## Day 9: File Handling — Text

### Concept

```python
# Likhna
with open("data.txt", "w") as f:
    f.write("line 1\n")
    f.write("line 2\n")

# Padhna
with open("data.txt", "r") as f:
    content = f.read()          # poora content ek string

with open("data.txt", "r") as f:
    for line in f:              # line by line (bade file ke liye better)
        print(line.strip())

# Add karna (purana mitega nahi)
with open("data.txt", "a") as f:
    f.write("line 3\n")
```

`with` isliye use karte hain kyunki wo file apne aap band kar deta hai.

### Practice
45. Ek file banaiye aur usme 5 lines likhiye.
46. File padh kar line by line print kariye.
47. File mein kitni lines hain, count kariye.
48. File mein ek particular word kitni baar aaya, count kariye.
49. File ke end mein 2 nayi lines append kariye.

---

## Day 10: CSV Padhna aur Likhna

### Concept

CSV DE ka sabse common format hai.

```python
import csv

# Likhna
rows = [
    ["id", "name", "salary"],
    [1, "Amit", 50000],
    [2, "Riya", 80000],
]
with open("emp.csv", "w", newline="") as f:
    writer = csv.writer(f)
    writer.writerows(rows)

# Padhna — list ke roop mein
with open("emp.csv", "r") as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)          # ['1', 'Amit', '50000']  — sab string hote hain!

# Padhna — dict ke roop mein (ye zyada useful hai)
with open("emp.csv", "r") as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(row["name"], row["salary"])
```

**Zaroori baat:** CSV se sab kuch **string** aata hai. Number chahiye toh `int()` ya `float()` karna padega. Ye ETL ka sabse common bug hai.

### Practice
50. 5 employees ka CSV likhiye.
51. `csv.reader` se padh kar print kariye.
52. `csv.DictReader` se padhiye aur sirf naam print kariye.
53. Salary ko `int()` mein convert karke total nikaliye.
54. Sirf salary > 55000 wali rows naye CSV mein likhiye.
55. CSV padh kar department-wise count nikaliye.

---

## Day 11: JSON

### Concept

```python
import json

emp = {"id": 1, "name": "Amit", "skills": ["SQL", "Python"]}

# Dict se JSON file
with open("emp.json", "w") as f:
    json.dump(emp, f, indent=2)

# JSON file se dict
with open("emp.json", "r") as f:
    data = json.load(f)

# String se dict aur ulta
s = json.dumps(emp)     # dict -> string
d = json.loads(s)       # string -> dict
```

Nested data access:
```python
data = {"emp": {"name": "Amit", "address": {"city": "Bengaluru"}}}
print(data["emp"]["address"]["city"])
```

### Practice
56. Ek dict ko JSON file mein save kariye.
57. JSON file padh kar dict mein laiye aur ek value print kariye.
58. Nested JSON banaiye aur andar wali value access kariye.
59. List of dicts ko JSON mein save kariye, phir wapas padhiye.

---

## Day 12: Exception Handling

### Concept

Pipeline mein ek galat row poora job fail na kar de — iske liye ye zaroori hai.

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Zero se divide nahi kar sakte")

try:
    x = int("abc")
except ValueError as e:
    print("Convert nahi hua:", e)

# Multiple
try:
    ...
except (ValueError, TypeError) as e:
    print("Error:", e)
except Exception as e:
    print("Kuch aur error:", e)
finally:
    print("Ye hamesha chalega")
```

DE ka असली pattern — galat row skip karke baaki process karo:
```python
valid, rejected = [], []
for row in rows:
    try:
        row["salary"] = int(row["salary"])
        valid.append(row)
    except ValueError:
        rejected.append(row)
```

### Practice
60. Division function likhiye jo zero handle kare.
61. Aisi file kholiye jo exist nahi karti — `FileNotFoundError` handle kariye.
62. `"abc"` ko int banane ki koshish kariye aur error handle kariye.
63. Ek list of strings mein kuch number kuch text hain — sirf numbers ka sum nikaliye, baaki skip.
64. Upar wala valid/rejected pattern khud likhiye aur dono ka count print kariye.

---

## Day 13: Modules aur Dates

### Concept

```python
from datetime import datetime, timedelta

today = datetime.now()
print(today.strftime("%Y-%m-%d"))        # date ko string

d = datetime.strptime("2026-09-03", "%Y-%m-%d")   # string ko date

kal = today + timedelta(days=1)
purana = today - timedelta(days=30)

diff = (today - d).days                  # kitne din ka farak
```

Apna module banana:
```python
# utils.py
def get_average(nums):
    return sum(nums) / len(nums)

# main.py
from utils import get_average
```

### Practice
65. Aaj ki date `YYYY-MM-DD` format mein print kariye.
66. `"2020-05-15"` string ko date banaiye aur aaj tak ke din count kariye.
67. 30 din baad ki date print kariye.
68. Ek `utils.py` banaiye 3 functions ke saath, doosri file se import karke use kariye.

---

## Day 14: PROJECT 1 — CSV Data Cleaner

Ek CSV banaiye jisme jaan-boojh kar problems hon: duplicate rows, blank values, extra spaces, salary column mein `"abc"` jaisi galat value.

Ek script likhiye jo:
1. CSV padhe (`DictReader`), input row count print kare
2. Duplicate rows hataye
3. Blank values ko default se bhare
4. Strings se extra spaces hataye
5. Salary ko `int()` kare — galat row ko reject list mein daale (try/except)
6. Clean data naye CSV mein likhe
7. Summary print kare: input rows, rejected rows, output rows

**Ye poori tarah aapke ETL testing background wala kaam hai. Isko GitHub pe daaliye.**

---

# PART 3 — PANDAS (Day 15-24)

---

## Day 15: DataFrame Basics

### Concept

Pandas = Python ka Excel/SQL. DataFrame = table.

```python
import pandas as pd

df = pd.read_csv("emp.csv")

df.head()          # pehli 5 rows
df.tail(3)
df.shape           # (rows, columns)
df.columns         # column names
df.dtypes          # har column ka type
df.info()          # summary
df.describe()      # numeric columns ke stats
```

Column select:
```python
df["name"]                    # ek column
df[["name", "salary"]]        # multiple columns
```

Naya column:
```python
df["annual"] = df["salary"] * 12
df = df.drop(columns=["annual"])
df = df.rename(columns={"name": "emp_name"})
```

### Practice
69. Dict se DataFrame banaiye.
70. Apna CSV padhiye aur `head()`, `shape`, `info()` dekhiye.
71. `annual_salary` column add kariye.
72. Ek column drop kariye aur ek rename kariye.

---

## Day 16: Filtering aur Sorting

### Concept

SQL ka `WHERE`:
```python
df[df["salary"] > 55000]

# Do conditions — & aur | use hota hai, and/or nahi
df[(df["salary"] > 55000) & (df["dept"] == "QA")]
df[(df["dept"] == "QA") | (df["dept"] == "DE")]

df[df["dept"].isin(["QA", "DE"])]
df[df["salary"].between(50000, 70000)]
df[df["name"].str.startswith("A")]
```

Sort:
```python
df.sort_values("salary")
df.sort_values("salary", ascending=False)
df.sort_values(["dept", "salary"])
df.nlargest(5, "salary")        # top 5
```

### Practice
73. Salary > 55000 filter kariye.
74. QA department aur salary > 50000 — dono condition.
75. `isin()` se do departments filter kariye.
76. Top 5 earners nikaliye.
77. Dept aur salary dono pe sort kariye.

---

## Day 17: Missing Values aur Duplicates

### Concept

```python
df.isnull().sum()               # har column mein kitne missing
df["salary"].fillna(0)
df["salary"].fillna(df["salary"].mean())
df.dropna()                     # missing wali rows hatao
df.dropna(subset=["salary"])    # sirf is column ke basis pe

df.duplicated().sum()           # kitne duplicate
df.drop_duplicates()
df.drop_duplicates(subset=["emp_id"])   # ek column ke basis pe
```

### Practice
78. Har column ke missing values count kariye.
79. Missing salary ko mean se bhariye.
80. Duplicate rows count karke hata dijiye.
81. `emp_id` ke basis pe duplicates hataiye.
82. Before/after row count print kariye (ye reconciliation hai).

---

## Day 18: GroupBy

### Concept

SQL ka `GROUP BY`:
```python
df.groupby("dept")["salary"].mean()
df.groupby("dept")["salary"].sum()
df.groupby("dept").size()                  # count

# Ek saath multiple
df.groupby("dept")["salary"].agg(["count", "sum", "mean", "max"])

# Do columns pe
df.groupby(["dept", "job"])["salary"].mean()

df["dept"].value_counts()
```

### Practice
83. Dept-wise average salary.
84. Dept-wise count, sum, min, max ek saath.
85. Dept + job dono pe groupby.
86. Har dept mein highest paid employee nikaliye.
87. `value_counts()` se dept-wise count.

---

## Day 19: Merge / Join

### Concept

SQL ka JOIN:
```python
merged = pd.merge(emp_df, dept_df, on="dept_id", how="inner")

# how = "inner" / "left" / "right" / "outer"
merged = pd.merge(emp_df, dept_df, on="dept_id", how="left")

# Upar-neeche jodna (UNION ALL)
combined = pd.concat([df1, df2])
```

**Reconciliation ki aadat daaliye** — join ke baad hamesha row count check kariye:
```python
print("before:", len(emp_df), "after:", len(merged))
```

### Practice
88. Do DataFrames banaiye — emp aur dept. Inner join kariye.
89. Left join kariye aur farak dekhiye.
90. Join ke pehle aur baad ka row count compare kariye.
91. Outer join karke missing values dekhiye.
92. `concat()` se do DataFrames jodiye.

---

## Day 20: Apply, Map, Dates

### Concept

```python
# Column pe function lagana
df["hiked"] = df["salary"].apply(lambda x: x * 1.1)

def get_grade(sal):
    if sal > 70000: return "High"
    elif sal > 50000: return "Medium"
    return "Low"

df["grade"] = df["salary"].apply(get_grade)

# Value replace
df["dept_full"] = df["dept"].map({"QA": "Quality", "DE": "Data Eng"})

# Dates
df["join_date"] = pd.to_datetime(df["join_date"])
df["year"] = df["join_date"].dt.year
df["month"] = df["join_date"].dt.month

# String operations
df["name"] = df["name"].str.strip().str.upper()
```

### Practice
93. Salary pe 10% hike lagaiye.
94. `get_grade` se grade column banaiye.
95. Dept codes ko full names mein map kariye.
96. Date column convert karke year aur month nikaliye.
97. Name column se spaces hata kar uppercase kariye.

---

## Day 21: Output aur Pivot

### Concept

```python
df.to_csv("output.csv", index=False)
df.to_excel("output.xlsx", index=False)
df.to_json("output.json", orient="records")

pd.pivot_table(df, values="salary", index="dept",
               columns="job", aggfunc="mean")
```

### Practice
98. Clean DataFrame ko CSV mein export kariye.
99. Excel mein export kariye.
100. Dept vs job ka pivot table banaiye.

---

## Day 22-24: PROJECT 2 — Sales Data Pipeline

Kaggle se koi sales/retail dataset lijiye (ya khud banaiye, 200+ rows).

Script ye structure follow kare:

```
1. INGESTION
   - CSV padhna
   - Input row count log karna

2. VALIDATION
   - Missing values check
   - Duplicate check
   - Data type check
   - Negative / invalid values check

3. TRANSFORMATION
   - Duplicates hatana
   - Missing values handle karna
   - Date columns convert karna
   - Derived column: total_amount = qty * price

4. AGGREGATION
   - Region-wise total sales
   - Month-wise trend
   - Top 10 products

5. OUTPUT
   - Clean data CSV mein
   - Summary report: input rows / rejected rows / output rows
```

Ye exactly wahi structure hai jo aap PySpark mein banayenge. Isliye ye aapka bridge project hai.

GitHub pe daaliye, README likhiye.

---

# PYTHON "KHATAM" KAB

Ye 3 test — bina Google ke:

1. List of dicts se dept-wise average salary (pure Python, bina Pandas)
2. CSV padh kar, duplicates hata kar, missing bhar kar, naye CSV mein likhna
3. Ek function jisme try/except ho aur galat row skip karke baaki process kare

Teeno aa gaye → **PySpark start.**

---

# KYA NAHI KARNA

Ye topics DE ke liye abhi zaroori nahi — skip kariye:
- OOP deep (inheritance, polymorphism, abstract classes)
- Decorators, generators, metaclasses
- DSA / competitive programming
- Django, Flask, FastAPI
- Multithreading, async

---

# TRACKER

```
Part 1:  D1[ ] D2[ ] D3[ ] D4[ ] D5[ ] D6[ ] D7[ ] D8[ ]
Part 2:  D9[ ] D10[ ] D11[ ] D12[ ] D13[ ] D14[ ]
Part 3:  D15[ ] D16[ ] D17[ ] D18[ ] D19[ ] D20[ ] D21[ ] D22[ ] D23[ ] D24[ ]
```

Din miss ho jaye toh agle din double mat kariye — bas aage badhiye.

---

**Aaj: Day 1. Concept padhiye, examples type kariye, problems 1-4. Timer 20 min.**

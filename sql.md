## مقدمة عن SQL:

- اختصار SQL هو "Structured Query Language" أو "لغة الاستعلامات الهيكلية".

- هي اللغة المستخدمة للتفاعل مع قواعد البيانات العلائقية (Relational Databases) مثل Oracle, MySQL, MS SQL, SQLite, SQL Server وغيرها.

-  تمكّنك من الوصول إلى البيانات في قواعد البيانات وإدارتها والتعديل عليها.


## ما هي MySQL :

- MySQL هو نظام إدارة قواعد البيانات (Database Management System) يسمح لك بإدارة قواعد البيانات العلائقية.
- هو برنامج مفتوح المصدر (Open Source) ومجاني ومدعوم من Oracle.


# أكواد SQL :

✔️ باش نبين معلومات محددة كاينين في الجدول 
```sql
SELECT id , email FROM Users
```
### ملاحظات⚠️:
* ال Users: هو اسم الجدول
* الفاصلة تعني 'و'
* ال id و email: هي اسماء الخانات الموجودة


✔️ باش نبين جميع المعلومات لي كاينين في الجدول 
```sql
SELECT * FROM Users
```

✔️ هاد الكود كايجيب ليك معلومات فالجدول (email , age) وكيرتبهم تصاعديا (من الصغر الى الاكبر) حسب age
```sql
SELECT email , age FROM users ORDER BY age ASC;
```

✔️ هاد الكود كايجيب ليك معلومات فالجدول (email , age) وكيرتبهم تنازليا (من الاكبر الى الاصغر) حسب age
```sql
SELECT email , age FROM users ORDER BY age DESC;
```

✔️ هاد الكود كيعطيك اول 2 معلومات لي كاينين في الجدول من الاكبر الى الاصغر حسب age
```sql
SELECT * FROM `users` ORDER BY age DESC LIMIT 2;
```


✔️ هاد الكود كيعطيك اول 3 معلومات لي كاينين في الجدول من الاصغر الى الاكبر حسب email
```sql
SELECT * FROM `users` ORDER BY email ASC LIMIT 3;
```


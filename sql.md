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
* ال id و email: هي اسماء الخانات الموجودة


✔️ باش نبين جميع المعلومات لي كاينين في الجدول 
```sql
SELECT * FROM Users
```

✔️ هاد الكود كايجيب ليك معلومات فالجدول (email , age) وكيرتبهم تصاعديا (من الصغر الى الاكبر) حسب age
```sql
SELECT email , age FROM users ORDER BY age ASC
```

✔️ هاد الكود كايجيب ليك معلومات فالجدول (email , age) وكيرتبهم تنازليا (من الاكبر الى الاصغر) حسب age
```sql
SELECT email , age FROM users ORDER BY age DESC
```

✔️ هاد الكود كيعطيك اول 2 معلومات لي كاينين في الجدول من الاكبر الى الاصغر حسب age
```sql
SELECT * FROM `users` ORDER BY age DESC LIMIT 2
```


✔️ هاد الكود كيعطيك اول 3 معلومات لي كاينين في الجدول من الاصغر الى الاكبر حسب email
```sql
SELECT * FROM `users` ORDER BY email ASC LIMIT 3
```


✔️ هاد الكود كيقول ليك جيب ليا الصفوف لي كاينين فالجدول وفيهوم age = 30
```sql
SELECT * FROM users WHERE age = 30
```


✔️ هاد الكود كيقول ليك جيب ليا الصفوف لي كاينين فالجدول وفيهوم age اصغر من 40
```sql
SELECT * FROM users WHERE age < 30
```


✔️ هاد الكود كيقول ليك جيب ليا الصفوف لي كاينين فالجدول وفيهوم age اصغر من 25 **و** email كيساوي 'mouatassim@gmail.com'
```sql
SELECT * FROM `users` WHERE age < 25 AND email = 'mouatassim@gmail.com'
```

✔️ هاد الكود كيقول ليك جيب ليا الصفوف لي كاينين فالجدول وفيهوم age اكبر من 25 **او** email كيساوي 'mouatassim@gmail.com'
```sql
SELECT * FROM `users` WHERE age > 25 OR email = 'mouatassim@gmail.com'
```

✔️ هاد الكود كيقول ليك جيب ليا الصفوف لي كاينين فالجدول وفيهوم age اصغر من 25 **او** age اكبر من 40
```sql
SELECT * FROM `users` WHERE age < 25 OR age > 40
```
### ملاحظة⚠️:
    OR = ||
    AND = &&
    NOT = !

✔️ هاد الكود كيقول ليك جيب ليا الصفوف لي كاينين فالجدول ومافيهومش age اصغر من 25
```sql
SELECT * FROM `users` WHERE not age < 25
```

✔️ لإدراج مستخدم جديد
```sql
INSERT INTO `users` (`email`, `password`, `age`) VALUES ('basel@gmail.com', 'basel', 33)
```

✔️ لإدراج عدة مستخدمين جدد
```sql
INSERT INTO `users` (`email`, `password`, `age`)
VALUES
    ('yasin@gmail.com', 'uuuu', 33),
    ('ttt@gmail.com', '324', 33);
```


✔️ هاد الكود كايخليك تبدل القيمة ديال age في الجدول من 30 الى 25
```sql
UPDATE users SET age = 25 WHERE age = 30
```

✔️ هاد الكود كايخليك تبدل القيمة ديال age في المصفوفة لي فيها id كيساوي 3
```sql
UPDATE users SET age = 15 WHERE id = 3
```


✔️ هاد الكود كايخليك تبدل القيمة ديال age في المصفوفة لي فيها email كيساوي 'simolkhal55@gmail.com'
```sql
UPDATE users SET age = 35 WHERE email = 'simolkhal55@gmail.com'
```


✔️ هاد الكود كايخليك تبدل القيمة ديال age و password في المصفوفة لي فيها id كيساوي 6
```sql
UPDATE `users` SET `age` = 34 , `Password` = 'eeeeee' WHERE id = 6
```


✔️ هاد الكود كايجيب ليك معلومات country لي كاينين فالجدول 
```sql
SELECT DISTINCT `country` FROM `users`
```
### ملاحظة⚠️:
تقوم DISTINCT  بإزالة الصفوف المكررة بناءً على الحقل (أو الحقول) المحددة

(بدون تكرار)

✔️ هاد الكود كايخليك تمسح الصفوف لي فيها age اكبر من 40
```sql
DELETE FROM users WHERE age > 40
```

✔️ هاد الكود كايخليك تمسح الصفوف لي فيها country كيساوي 'canada'
```sql
DELETE FROM users WHERE country = 'canada'
```
✔️ تُستخدم لإيجاد أكبر قيمة في عمود معين
```sql
SELECT MAX(age) FROM users
```
✔️ تُستخدم لإيجاد اصغر قيمة في عمود معين
```sql
SELECT MIN(age) FROM users
```
✔️ تُستخدم لحساب المتوسط الحسابي للقيم في عمود رقمي
```sql
SELECT AVG(age) FROM users
```
✔️ تُستخدم لحساب عدد الصفوف الموجودة في جدول معين
```sql
SELECT COUNT(age) FROM users
```
✔️ لحساب عدد الدول الفريدة التي ينتمي إليها المستخدمون (لتجنب عد نفس الدولة عدة مرات إذا كانت مكررة)
```sql
SELECT COUNT(DISTINCT country) FROM users
```

✔️ تُستخدم لحساب مجموع القيم في عمود رقمي
```sql
SELECT SUM(age) FROM users
```

✔️ هاد الكود كيقول ليك جيب ليا الصفوف لي فيها email يبدأ بحرف a
```sql
SELECT * FROM `users` WHERE email LIKE 'a%'
```

✔️ هاد الكود كيقول ليك جيب ليا الصفوف لي فيها name ينتهي ب ed
```sql
SELECT * FROM `users` WHERE name LIKE '%ed'
```

✔️ هاد الكود كيقول ليك جيب ليا الصفوف لي فيها username يحتوي على حرف m
```sql
SELECT * FROM `users` WHERE username LIKE '%m%'
```

✔️ هاد الكود كيقول ليك جيب ليا الصفوف لي فيها country والحرف الثاني يساوي t
```sql
SELECT * FROM `users` WHERE country LIKE '_t%'
```
✔️ هاد الكود كيقول ليك جيب ليا الصفوف لي فيها country والحرف الثالث يساوي s
```sql
SELECT * FROM `users` WHERE country LIKE '__s%'
```
✔️ هاد الكود كيقول ليك جيب ليا الصفوف لي فيها name يبدأ بحرف a وينتهي بحرف d
```sql
SELECT * FROM `users` WHERE name LIKE 'a%d'
```
✔️ هاد الاكواد كيقول ليك جيب ليا الصفوف لي فيها country كيساوي 'Maroc' **او** 'Égypte' 
```sql
SELECT * FROM users WHERE country = 'Maroc' or country = 'Égypte'
```
```sql
SELECT * FROM users WHERE country IN ('Maroc' , 'Égypte')
```
✔️ هاد الاكواد كيقول ليك جيب ليا الصفوف لي فيها age بين 20 و 40
```sql
SELECT * FROM `users` WHERE age > 20 AND age < 40
```
```sql
SELECT * FROM `users` WHERE age BETWEEN 20 AND 40
```
✔️ هاد الكود كيخليك تعطي اسم مستعار للعمود
```sql
SELECT name as username FROM `users`
```
```sql
SELECT count(id) as countusers FROM `users`
```
✔️ هاد الكود كيقول ليك جيب ليا مجموع العلامات على حساب كل طالب
```sql
SELECT name , sum(mark) as summark FROM student GROUP BY name
```
✔️ هاد الكود كيقول ليك جيب ليا مجموع العلامات على حساب كل طالب  وخاص المجموع يكون اكبر من 60
```sql
SELECT name , sum(mark) as summark FROM student GROUP BY name HAVING summark >= 60
```
### ملاحظات⚠️:
ميمكنش لينا نديرو where حيت ماكاتخدمش معا الدوال (functions)

تُستخدم HAVING لتطبيق شروط على المجموعات بعد أن يتم تجميعها بواسطة GROUP BY.

✔️ هاد الاكواد كتقول ليك جيب ليا كل المنتجات واسم الفئة اللي فيهم
```sql
SELECT items.*, categories.c_name FROM categories, items WHERE categories.c_id = items.I_categories
```

```sql
SELECT items.*, categories.c_name FROM items
INNER JOIN categories ON items.I_categories = categories.c_id
```
✔️ هاد الكود كيقول ليك جيب ليا اسماء الفئات **(categories)** اللي فيها منتجات بسعر اكبر من 700
```sql
SELECT categories.c_name FROM categories 
WHERE EXISTS(SELECT items.* FROM items WHERE categories.c_id = items.I_categories AND items.I_price < 700)
```
✔️ هاد الكود كيقول ليك جيب ليا اسماء المنتجات (items) اللي فيهم 2 طلبات
```sql
SELECT items.I_name FROM items 
WHERE items.I_id = any (SELECT ordersdetails_items FROM ordersdetails WHERE ordersdetails_quantity = 2)
```
✔️ هاد الكود كيقول ليك جيب ليا اسماء المنتجات (items) واسماء الفئات (categories)
```sql
SELECT items.I_name FROM items 
UNION
SELECT categories.c_name FROM categories
```
### ملاحظات⚠️:
تستخدم UNION لدمج نتائج عدة استعلامات SQL في نتائج واحدة، ولكنها تزيل الصفوف المكررة تلقائيًا.

✔️ هاد الكود كيقول ليك جيب ليا اسماء المنتجات (items) واسماء الفئات (categories)
```sql
SELECT items.I_name FROM items 
UNION ALL
SELECT categories.c_name FROM categories
```
### ملاحظات⚠️:
تستخدم UNION ALL لدمج نتائج عدة استعلامات SQL في نتائج واحدة، ولكنها لا تزيل الصفوف المكررة تلقائيًا.


✔️ هاد الكود كيقول ليك جيب ليا اسماء المنتجات (items) وسعرهم, ولكن الا كان السعر NULL عطيع قيمة 0
```sql
SELECT items.I_name , IFNULL(items.I_price , 0) FROM items
```


بالتأكيد، إليك ملخص للفيديو بتنسيق Markdown باللغة العربية:

ملخص فيديو: الدوال التجميعية في SQL (Min, Max, Count, Avg, Sum)

يشرح هذا الفيديو كيفية استخدام الدوال التجميعية (Aggregate Functions) الأساسية في لغة SQL لاستخلاص معلومات ملخصة من البيانات الموجودة في جدول users باستخدام phpMyAdmin. الجدول يحتوي على أعمدة مثل id, email, name, age, و country.

1. دالة MAX() (القيمة القصوى)

الغرض: تُستخدم لإيجاد أكبر قيمة في عمود معين.

مثال: لإيجاد أكبر عمر للمستخدمين:

SELECT MAX(age) FROM users;


في الفيديو، كانت النتيجة 43.

يمكن استخدامها أيضًا مع أعمدة أخرى مثل id لإيجاد أكبر id.

2. دالة MIN() (القيمة الدنيا)

الغرض: تُستخدم لإيجاد أصغر قيمة في عمود معين.

مثال: لإيجاد أصغر عمر للمستخدمين:

SELECT MIN(age) FROM users;
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
SQL
IGNORE_WHEN_COPYING_END

في الفيديو، كانت النتيجة 20.

3. دالة AVG() (المتوسط الحسابي)

الغرض: تُستخدم لحساب المتوسط الحسابي للقيم في عمود رقمي.

مثال: لحساب متوسط أعمار المستخدمين:

SELECT AVG(age) FROM users;
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
SQL
IGNORE_WHEN_COPYING_END

يقوم بجمع كل الأعمار ثم يقسمها على عددها. في الفيديو، كانت النتيجة 32.0000.

4. دالة COUNT() (عدد الصفوف/القيم)

الغرض: تُستخدم لحساب عدد الصفوف التي تطابق شرطًا معينًا، أو عدد القيم غير الفارغة في عمود.

مثال: لحساب عدد المستخدمين الإجمالي:

SELECT COUNT(id) FROM users; -- أو COUNT(name) أو COUNT(*)
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
SQL
IGNORE_WHEN_COPYING_END

في الفيديو، كانت النتيجة 5.

COUNT(DISTINCT ...): لحساب عدد القيم الفريدة (بدون تكرار) في عمود.

مثال: لحساب عدد الدول الفريدة التي ينتمي إليها المستخدمون (لتجنب عد نفس الدولة عدة مرات إذا كانت مكررة):

SELECT COUNT(DISTINCT country) FROM users;
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
SQL
IGNORE_WHEN_COPYING_END

في الفيديو، كانت النتيجة الأولية 4 ثم بعد تعديل البيانات لتكرار بلد آخر أصبحت 3.

5. دالة SUM() (المجموع)

الغرض: تُستخدم لحساب مجموع القيم في عمود رقمي.

مثال: لحساب مجموع أعمار كل المستخدمين:

SELECT SUM(age) FROM users;
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
SQL
IGNORE_WHEN_COPYING_END

في الفيديو، كانت النتيجة 160.

يذكر مقدم الفيديو مثالاً عمليًا مثل جمع أسعار المنتجات في سلة التسوق.

خلاصة:

يوفر الفيديو شرحًا عمليًا لهذه الدوال الخمس الأساسية مع أمثلة توضيحية مباشرة من خلال واجهة phpMyAdmin، مما يسهل فهم كيفية استخدامها لاستخراج إحصائيات مفيدة من قواعد البيانات.

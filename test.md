بالتأكيد، إليك ملخص للفيديو باللغة العربية على شكل Markdown:

ملخص فيديو: شرح GROUP BY و HAVING في SQL

يوضح هذا الفيديو كيفية استخدام جملتي GROUP BY و HAVING في لغة SQL لمعالجة البيانات وتلخيصها في قاعدة بيانات MySQL باستخدام phpMyAdmin.

1. إعداد قاعدة البيانات والجدول:

تم إنشاء جدول باسم student يحتوي على الأعمدة التالية:

id: (INT, المفتاح الأساسي، ترقيم تلقائي) - معرّف الطالب.

name: (VARCHAR) - اسم الطالب.

semester: (INT) - رقم الفصل الدراسي.

mark: (INT) - علامة الطالب في ذلك الفصل.

تم إدخال بيانات لعدة طلاب (محمد، باسل، وائل) مع علاماتهم في فصلين دراسيين مختلفين لكل طالب. على سبيل المثال:

محمد: فصل 1 (علامة 20)، فصل 2 (علامة 30).

باسل: فصل 1 (علامة 10)، فصل 2 (علامة 50).

وائل: فصل 1 (علامة 40)، فصل 2 (علامة 50).

2. المشكلة الأولى: حساب مجموع علامات كل طالب:

الهدف: عرض اسم كل طالب ومجموع علاماته الكلية (علامات الفصل الأول + الفصل الثاني).

محاولة أولية (غير صحيحة بدون GROUP BY):

SELECT name, SUM(mark) AS summary FROM student;


هذه الاستعلام يعرض اسم طالب واحد فقط (محمد، أول سجل) ومجموع علامات جميع الطلاب (200)، وهذا ليس المطلوب.

الحل الصحيح باستخدام GROUP BY:
لتجميع النتائج حسب اسم الطالب وحساب المجموع لكل طالب على حدة:

SELECT name, SUM(mark) AS summary FROM student GROUP BY name;
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
SQL
IGNORE_WHEN_COPYING_END

النتيجة:

باسل: 60

محمد: 50

وائل: 90

هذا يعرض بشكل صحيح مجموع علامات كل طالب.

3. المشكلة الثانية: تصفية النتائج المجمعة (الطلاب الذين مجموعهم أكبر من 50):

الهدف: عرض أسماء الطلاب ومجموع علاماتهم فقط للطلاب الذين يزيد مجموع علاماتهم الكلي عن 50.

محاولة خاطئة باستخدام WHERE مع الدوال التجميعية:
لا يمكن استخدام WHERE لتطبيق شروط على نتائج الدوال التجميعية (مثل SUM()). الكود التالي سيعطي خطأ:

-- هذا الكود سيعطي خطأ
SELECT name, SUM(mark) AS summary FROM student WHERE summary > 50 GROUP BY name;
-- أو
SELECT name, SUM(mark) AS summary FROM student WHERE SUM(mark) > 50 GROUP BY name;
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
SQL
IGNORE_WHEN_COPYING_END

الخطأ: Unknown column 'summary' in 'where clause' أو خطأ مشابه يتعلق بعدم القدرة على استخدام SUM() في WHERE.

الحل الصحيح باستخدام HAVING:
تُستخدم HAVING لتطبيق شروط على المجموعات بعد أن يتم تجميعها بواسطة GROUP BY.

SELECT name, SUM(mark) AS summary FROM student GROUP BY name HAVING summary > 50;
-- أو باستخدام الدالة التجميعية مباشرة في HAVING
SELECT name, SUM(mark) AS summary FROM student GROUP BY name HAVING SUM(mark) > 50;
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
SQL
IGNORE_WHEN_COPYING_END

النتيجة:

باسل: 60

وائل: 90

هذا يعرض بشكل صحيح فقط الطلاب الذين مجموع علاماتهم الكلية أكبر من 50.

الخلاصة:

GROUP BY تُستخدم لتجميع الصفوف التي لها قيم متطابقة في أعمدة محددة، مما يسمح بتطبيق الدوال التجميعية (مثل SUM(), COUNT(), AVG()) على كل مجموعة.

HAVING تُستخدم لتصفية النتائج بعد عملية التجميع بواسطة GROUP BY، حيث يمكن تطبيق شروط على نتائج الدوال التجميعية. لا يمكن استخدام WHERE لهذا الغرض.

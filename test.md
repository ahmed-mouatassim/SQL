بالتأكيد، إليك شرح محتوى الفيديو بصيغة Markdown باللغة العربية:

# شرح `SELECT DISTINCT` في SQL

في هذا الفيديو، سنتعرف على استخدام عبارة `SELECT DISTINCT` في SQL لإرجاع القيم الفريدة فقط من عمود معين.

## تهيئة البيانات للمثال

لتوضيح الفكرة بشكل أفضل، سنقوم أولاً بإضافة عمود جديد باسم `country` (البلد) إلى جدول `users` الموجود لدينا في قاعدة البيانات `course`.

1.  **إضافة عمود `country`:**
    *   من واجهة phpMyAdmin، ننتقل إلى جدول `users` ثم إلى تبويب "Structure" (البنية).
    *   نضيف عمودًا جديدًا بعد عمود `age`.
    *   **اسم العمود:** `country`
    *   **النوع:** `VARCHAR`
    *   **الطول/القيم:** `100`
    *   نضغط "Save" (حفظ).
    *   سيتم تنفيذ أمر SQL مشابه للتالي:
        ```sql
        ALTER TABLE `users` ADD `country` VARCHAR(100) NOT NULL AFTER `age`;
        ```

2.  **إدخال بيانات في عمود `country`:**
    بعد إضافة العمود، نقوم بتعبئة بيانات البلدان للمستخدمين الحاليين، مع تعمد إدخال قيم مكررة:
    *   المستخدم "wael": `syria`
    *   المستخدم "mohammad": `germany`
    *   المستخدم "yasser": `germany` (مكرر)
    *   المستخدم "majed": `ksa`
    *   المستخدم "basel": `ksa` (مكرر)

الآن أصبح جدول `users` يحتوي على البيانات التالية (مع التركيز على `age` و `country`):

| id | email              | password   | age | country |
|----|--------------------|------------|-----|---------|
| 1  | wael@gmail.com     | wael       | 20  | syria   |
| 2  | mohammad@gmail.com | mohammad   | 40  | germany |
| 3  | yaser@gmail.com    | yasser     | 35  | germany |
| 4  | majed@gmail.com    | majed      | 40  | ksa     |
| 11 | basel@gmail.com    | basel      | 30  | ksa     |

## المشكلة: استرجاع القيم المكررة

لنفترض أننا نريد معرفة قائمة البلدان التي ينتمي إليها المستخدمون. إذا استخدمنا الاستعلام التالي:

```sql
SELECT country FROM users;


ستكون النتيجة كالتالي، مع ظهور القيم المكررة:

country
syria
germany
germany
ksa
ksa

هنا تظهر المشكلة، حيث يتم عرض "germany" و "ksa" مرتين. نحن نريد قائمة فريدة بالبلدان.

الحل: استخدام SELECT DISTINCT

للحصول على قائمة فريدة بالبلدان (بدون تكرار)، نستخدم كلمة DISTINCT قبل اسم الحقل الذي نريد عرض قيمه الفريدة:

SELECT DISTINCT country FROM users;
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
SQL
IGNORE_WHEN_COPYING_END

النتيجة ستكون:

country
syria
germany
ksa

كما نرى، تم عرض كل بلد مرة واحدة فقط. عبارة DISTINCT تقوم بإزالة الصفوف المكررة بناءً على الحقل (أو الحقول) المحددة.

مثال آخر: استرجاع الأعمار الفريدة

يمكن تطبيق نفس المبدأ على حقول أخرى. مثلاً، إذا أردنا معرفة الأعمار المختلفة للمستخدمين في الجدول.

البيانات الأصلية للأعمار في الجدول هي: 20, 40, 35, 40, 30. نلاحظ أن العمر 40 مكرر.

إذا استخدمنا الاستعلام بدون DISTINCT:

SELECT age FROM users;
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
SQL
IGNORE_WHEN_COPYING_END

ستظهر القيمة 40 مكررة.

باستخدام DISTINCT:

SELECT DISTINCT age FROM users;
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
SQL
IGNORE_WHEN_COPYING_END

النتيجة ستكون الأعمار الفريدة فقط:

age
20
40
35
30
الخلاصة

تُستخدم عبارة SELECT DISTINCT لجلب القيم الفريدة فقط من حقل معين أو مجموعة حقول، متجاهلة بذلك أي تكرارات قد تكون موجودة في البيانات الأصلية.

IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
IGNORE_WHEN_COPYING_END

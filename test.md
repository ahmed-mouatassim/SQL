أكيد! إليك ملخص للفيديو على شكل كود Markdown و بالدارجة المغربية:

الاتصال بقاعدة البيانات باستعمال PDO في PHP

الفيديو كيشرح لينا الطريقة الصحيحة باش نتصلوا بقاعدة بيانات (Database) من نوع MySQL باستعمال PHP، و بالضبط تقنية PDO (PHP Data Objects). الفكرة هي أننا نصايبو واحد الفيشي سميتو connect.php اللي نقدروا نعاودو نستعملوه ف كاع المشاريع ديالنا.

الخطوة الأولى: المتغيرات ديال الإتصال (فالفيشي connect.php)

أول حاجة، كنوجدو المتغيرات اللي غادي نحتاجو باش نتصلو.

$dsn (Data Source Name): هذا هو المتغير الأهم، فيه المعلومات على قاعدة البيانات:

نوع قاعدة البيانات (mysql).

السيرفر أو المضيف (host=localhost).

وسمية قاعدة البيانات اللي بغينا نتصلو بيها (dbname=coursephp).

$user: اسم المستخدم ديال قاعدة البيانات. فالسيرفر المحلي (localhost) كيكون غالباً root.

$pass: كلمة المرور. فالسيرفر المحلي كتكون خاوية.

$option: هادي عبارة على مصفوفة (Array) فيها الإعدادات الإضافية. هنا استعملناها باش ندعمو اللغة العربية (SET NAMES UTF8).

<?php

$dsn = "mysql:host=localhost;dbname=coursephp";
$user = "root";
$pass = ""; 
$option = array(
    PDO::MYSQL_ATTR_INIT_COMMAND => "SET NAMES UTF8" // باش ندعمو اللغة العربية
);

الخطوة الثانية: إنشاء الإتصال مع معالجة الأخطاء (Error Handling)

كنستعملو try...catch باش إلى وقع شي مشكل فالإتصال (مثلاً كلمة سر غالطة أو سمية الداتابيز غالطة)، البرنامج مايوقفش و نقدرو نعرفو نوع الخطأ.

try: كنحاولو نتصلو.

كنصايبو واحد الأوبجيكت جديد من الكلاس PDO و كندوزو ليه المتغيرات اللي صايبنا.

كنزيدو سطر setAttribute باش نقولو لـ PDO يطلق أخطاء (Exceptions) إلى وقع شي مشكل.

catch: إلى فشل الإتصال، الكود اللي هنا كيتنفذ.

كيشد الخطأ و كيطبع لينا الرسالة ديالو باش نعرفو فين كاين المشكل.

try {
    // هنا كنصايبو واحد الأوبجيكت جديد من الكلاس PDO
    $con = new PDO($dsn, $user, $pass, $option);
    
    // هاد السطر كيخلي PDO يطلق أخطاء (exceptions) باش نشدوهم فالـ catch
    $con->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    
    // تقدرو تزيدو هاد السطر باش تأكدو أن الإتصال تم بنجاح (اختياري)
    // echo "You Are Connected";

} catch(PDOException $e){
    // إلى وقع شي خطأ، هاد الكود كيتنفذ وكيطبع لينا رسالة الخطأ
    echo "Failed To Connect " . $e->getMessage();
}
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
PHP
IGNORE_WHEN_COPYING_END
الخطوة الثالثة: اختبار الإتصال

باش نتأكدو أن كلشي خدام، كنمشيو لصفحة أخرى بحال index.php و كنديرو include للفيشي ديالنا connect.php. من بعد كنقدرو نستعملو المتغير $con باش نديرو استعلامات (Queries) من قاعدة البيانات.

// index.php

<?php 

include "connect.php"; // كنديرو تضمين للفيشي ديال الإتصال

// كنديرو استعلام باش نجيبو كاع المستخدمين
$stmt = $con->prepare("SELECT * FROM users");
$stmt->execute();
$users = $stmt->fetchAll(PDO::FETCH_ASSOC);

// كنطبعو النتيجة على شكل مصفوفة
print_r($users);
IGNORE_WHEN_COPYING_START
content_copy
download
Use code with caution.
PHP
IGNORE_WHEN_COPYING_END

بهاد الطريقة، الفيشي connect.php كيبقى منظم وفيه غير الكود الخاص بالإتصال، ونقدرو نستعملوه بسهولة ف أي بلاصة فالمشروع ديالنا.

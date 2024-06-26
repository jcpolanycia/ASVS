# الملحق ج: متطلبات التحقق من إنترنت الأشياء

كان هذا الفصل في الأساس في الفرع الرئيسي ، ولكن مع العمل الذي قام به فريق OWASP IoT ، فليس من المنطقي الاحتفاظ بمكانين مختلفين حول هذا الموضوع. بالنسبة للإصدار 4.0 ، ننقل هذا إلى الملحق ، ونحث كل من يطلب ذلك ، بدلاً من استخدام  [OWASP IoT project مشروع أواسب لانترنت الأشياء](https://owasp.org/www-project-internet-of-things/) الرئيسي

## الهدف من ضوابط الأمان

يجب على الأجهزة المضمنة / إنترنت الأشياء:

* الحصول على نفس مستوى عناصر التحكم في الأمان داخل الجهاز كما هو موجود في الخادم ، من خلال فرض ضوابط الأمان في بيئة موثوقة.
* يجب أن يتم تخزين البيانات الحساسة على الجهاز بطريقة آمنة باستخدام التخزين المدعوم من الأجهزة مثل العناصر الآمنة.
* يجب أن تستخدم جميع البيانات الحساسة المرسلة من الجهاز أمان طبقة النقل.

## متطلبات التحقق الأمني

| # | التوصيف | L1 | L2 | L3 | Since |
| --- | --- | --- | --- | -- | -- |
| **ض.1** | تحقق من أن واجهات تصحيح أخطاء طبقة التطبيق application layer debugging interfaces مثل USB و UART والمتغيرات التسلسلية serial variants الأخرى معطلة أو محمية بكلمة مرور معقدة. | ✓ | ✓ | ✓ | 4.0 |
| **ض.2** | تحقق من أن مفاتيح التشفير والشهادات فريدة لكل جهاز على حدة. | ✓ | ✓ | ✓ | 4.0 |
| **ض.3** | تحقق من تمكين عناصر تحكم حماية الذاكرة مثل ASLR و DEP بواسطة نظام التشغيل المدمج / إنترنت الأشياء embedded/IoT operating system ، إن أمكن. | ✓ | ✓ | ✓ | 4.0 |
| **ض.4** | تحقق من أن واجهات التصحيح على الرقاقة on-chip debugging interfaces مثل JTAG أو SWD معطلة أو أن آلية الحماية المتاحة تم تمكينها وتكوينها بشكل مناسب. | ✓ | ✓ | ✓ | 4.0 |
| **ض.5** | تحقق من تنفيذ وتمكين التنفيذ execution الموثوق به ، إذا كان ذلك متاحًا على جهاز SoC أو وحدة المعالجة المركزية. | ✓ | ✓ | ✓ | 4.0 |
| **ض.6** | تحقق من تخزين البيانات الحساسة والمفاتيح الخاصة والشهادات بشكل آمن في Secure Element أو TPM أو TEE (بيئة تنفيذ موثوقة) أو محمية باستخدام تشفير قوي. | ✓ | ✓ | ✓ | 4.0 |
| **ض.7** | تحقق من أن تطبيقات البرامج الثابتة firmware apps protect تحمي البيانات أثناء النقل باستخدام أمان طبقة النقل. | ✓ | ✓ | ✓ | 4.0 |
| **ض.8** | تحقق من أن تطبيقات البرامج الثابتة تتحقق من صحة التوقيع الرقمي لاتصالات الخادم. | ✓ | ✓ | ✓ | 4.0 |
| **ض.9** | تحقق من أن الاتصالات اللاسلكية مصادقة بشكل متبادل. | ✓ | ✓ | ✓ | 4.0 |
| **ض.10** | تحقق من إرسال الاتصالات اللاسلكية عبر قناة مشفرة.  | ✓ | ✓ | ✓ | 4.0 |
| **ض.11** | تحقق من استبدال أي استخدام لوظائف C المحظورة بوظائف مناسبة بحيث تكون بديلة وآمنة. | ✓ | ✓ | ✓ | 4.0 |
| **ض.12** | تحقق من أن كل برنامج ثابت firmware  يحتفظ بقائمة مواد للبرنامج تقوم بفهرسة مكونات الطرف الثالث ، والإصدارات ، والثغرات الأمنية المنشورة. | ✓ | ✓ | ✓ | 4.0 |
| **ض.13** | تحقق من جميع الشيفرة المصدرية code بما في ذلك الثنائيات Binaries والمكتبات والأطر التابعة لجهات خارجية والتي تتم مراجعتها لبيانات الاعتماد المشفرة (الأبواب الخلفية Backdoors). | ✓ | ✓ | ✓ | 4.0 |
| **ض.14** | تحقق من أن مكونات التطبيق والبرامج الثابتة firmware ليست عرضة لـحقن أوامر نظام التشغيل عن طريق استدعاء أغلفة أوامر shell (shell command wrappers) أو البرامج النصية أو أن عناصر التحكم الأمنية تمنع حقن أوامر نظام التشغيل. | ✓ | ✓ | ✓ | 4.0 |
| **ض.15** | تحقق من أن تطبيقات البرامج الثابتة تثبت التوقيع الرقمي بخادم (خوادم) موثوق به. |  | ✓ | ✓ | 4.0 |
| **ض.16** | تحقق من وجود مقاومة للتلاعب tamper و / أو ميزات كشف التلاعب Tamper Detection. |  | ✓ | ✓ | 4.0 |
| **ض.17** | تحقق من تمكين أي من تقنيات حماية الملكية الفكرية التي توفرها الشركة المصنعة للرقاقة. |  | ✓ | ✓ | 4.0 |
| **ض.18** | تحقق من وجود ضوابط الأمان لعرقلة الهندسة العكسية للبرامج الثابتة (على سبيل المثال ، إزالة رموز التصحيح المطول verbose debugging symbols). |  | ✓ | ✓ | 4.0 |
| **ض.19** | تحقق من قيام الجهاز بالتحقق من صحة توقيع صورة الإقلاع boot image signature  قبل التحميل. |  | ✓ | ✓ | 4.0 |
| **ض.20** | تحقق من أن عملية تحديث البرنامج الثابت ليست عرضة لهجمات وقت التحقق مقابل وقت الاستخدام time-of-check vs time-of-use attacks. |  | ✓ | ✓ | 4.0 |
| **ض.21** | تحقق من أن الجهاز يستخدم توقيع الرمز code signing والتحقق من صحة ملفات ترقية البرامج الثابتة firmware upgrade files  قبل التثبيت. |  | ✓ | ✓ | 4.0 |
| **ض.22** | تحقق من أنه لا يمكن إرجاع الجهاز إلى الإصدارات القديمة downgraded (مكافحة التراجع anti-rollback) من البرامج الثابتة الصالحة. |  | ✓ | ✓ | 4.0 |
| **ض.23** | تحقق من استخدام منشئ الأرقام العشوائية الزائفة الآمنة المشفرة cryptographically secure pseudo-random number generator على جهاز مضمن embedded device (على سبيل المثال ، باستخدام مولدات الأرقام العشوائية المزودة بشريحة using chip-provided random number generators). |  | ✓ | ✓ | 4.0 |
| **ض.24** | تحقق من أن البرنامج الثابت يمكنه إجراء تحديثات تلقائية للبرامج الثابتة وفقًا لجدول زمني محدد مسبقًا. |  | ✓ | ✓ | 4.0 |
| **ض.25** | تحقق من أن الجهاز يفحص البرامج الثابتة والبيانات الحساسة عند اكتشاف التلاعب أو استلام رسالة غير صالحة. |  |  | ✓ | 4.0 |
| **ض.26** | تحقق من استخدام وحدات التحكم الصغيرة micro controllers  فقط التي تدعم تعطيل واجهات تصحيح الأخطاء (مثل JTAG و SWD). |  |  | ✓ | 4.0 |
| **ض.27** | تحقق من استخدام وحدات التحكم الصغيرة micro controllers فقط التي توفر حماية كبيرة من هجمات إلغاء السد والقنوات الجانبية decapping and side channel attacks. |  |  | ✓ | 4.0 |
| **ض.28** | تحقق من عدم تعرض الآثار الحساسة sensitive traces للطبقات الخارجية للوحة الدائرة المطبوعة outer layers of the printed circuit board. |  |  | ✓ | 4.0 |
| **ض.29** | تحقق من أن الاتصال بين الشرائح مشفر (على سبيل المثال ، اتصال اللوحة الرئيسية Main board  إلى اللوحة الفرعية daughter board). |  |  | ✓ | 4.0 |
| **ض.30** | تحقق من أن الجهاز يستخدم توقيع الرمز code signing  والتحقق من صحة الرمز قبل التنفيذ. |  |  | ✓ | 4.0 |
| **ض.31** | تحقق من أن المعلومات الحساسة المحفوظة في الذاكرة قد تم استبدالها overwritten بالأصفار بمجرد عدم الحاجة إليها. |  |  | ✓ | 4.0 |
| **ض.32** | تحقق من أن تطبيقات البرامج الثابتة تستخدم حاويات kernel للعزل بين التطبيقات. |  |  | ✓ | 4.0 |
| **ض.33** | تحقق من أن علامات المترجم الآمن مثل -fPIE، -fstack-protector-all، -Wl، -z، noexecstack، -Wl، -z، noexecheap قد تم تكوينها لإنشاءات البرامج الثابتة. |  |  | ✓ | 4.0 |
| **ض.34** | تحقق من تكوين وحدات التحكم الصغيرة micro controllers مع حماية الشيفرة المصدرية code protection (إن أمكن). |  |  | ✓ | 4.0 |

## المراجع

لمزيد من المعلومات، يمكن أيضاً الاطلاع على:

* [OWASP Internet of Things Top 10](https://owasp.org/www-pdf-archive/OWASP-IoT-Top-10-2018-final.pdf)
* [OWASP Embedded Application Security Project](https://owasp.org/www-project-embedded-application-security/)
* [OWASP Internet of Things Project](https://owasp.org/www-project-internet-of-things/)
* [Trudy TCP Proxy Tool](https://github.com/praetorian-inc/trudy)

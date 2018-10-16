---
title: Virtual Environments
localeTitle: البيئات الافتراضية
---
## بيئة افتراضية

يمكن وصف البيئات الافتراضية كأدلة تثبيت معزولة. تسمح لك هذه العزلة بترجمة تثبيت تبعيات مشروعك ، دون إجبارك على تثبيتها على مستوى النظام بأكمله.

تخيل أن لديك تطبيقين App1 و App2. كلاهما يتطلب حزمة باك ، ولكن مع إصدارات مختلفة. إذا قمت بتثبيت Pak الإصدار 2.3 لـ App1 ، لن تتمكن من تشغيل App2 ، لأنه يتطلب الإصدار 3.1. هنا عندما تكون البيئات الافتراضية في متناول اليد.

فوائد:

*   يمكن أن يكون لديك بيئات متعددة ، مع مجموعات متعددة من الحزم ، دون تعارض فيما بينها. بهذه الطريقة ، يمكن تلبية متطلبات المشاريع المختلفة في نفس الوقت.
*   يمكنك بسهولة إطلاق مشروعك بوحدات تابعة خاصة به.

فيما يلي طريقتان يمكنك إنشاء بيئات بيثون الافتراضية.

## Virtualenv

[`virtualenv`](https://virtualenv.pypa.io/en/stable/) هي أداة تستخدم لإنشاء بيئات بيثون المعزولة. يقوم بإنشاء مجلد يحتوي على كافة الملفات التنفيذية الضرورية لاستخدام الحزم التي يحتاجها مشروع Python.

يمكنك تثبيته مع `pip` :

 `pip install virtualenv 
` 

تحقق من التثبيت باستخدام الأمر التالي:

 `virtualenv --version 
` 

### إنشاء environemnt

لإنشاء استخدام بيئة افتراضية:

 `virtualenv --no-site-packages my-env 
` 

يؤدي هذا إلى إنشاء مجلد في الدليل الحالي باسم البيئة ( `my-env/` ). يحتوي هذا المجلد على الدلائل لتثبيت الوحدات النمطية والملفات التنفيذية Python.

يمكنك أيضًا تحديد إصدار Python الذي تريد العمل به. ما عليك `--python=/path/to/python/version` استخدام الوسيطة `--python=/path/to/python/version` . على سبيل المثال ، `python2.7` :

 `virtualenv --python=/usr/bin/python2.7 my-env 
` 

### قائمة البيئات

يمكنك إدراج البيئات المتاحة مع:

 `lsvirtualenv 
` 

### تفعيل بيئة

قبل أن تتمكن من البدء في استخدام البيئة ، يلزمك تنشيطها:

 `source my-env/bin/activate 
` 

هذا يضمن أن يتم استخدام حزم فقط تحت `my-env/` .

ستلاحظ ظهور اسم البيئة على يسار المطالبة. بهذه الطريقة يمكنك رؤية ما هي البيئة النشطة.

### تثبيت الحزم

يمكنك تثبيت الحزم واحدة تلو الأخرى ، أو عن طريق تعيين ملف `requirements.txt` لمشروعك.

 `pip install some-package 
 pip install -r requirements.txt 
` 

إذا كنت تريد إنشاء ملف `requirements.txt` من الحزم المثبتة بالفعل ، فقم بتشغيل الأمر التالي:

 `pip freeze > requirements.txt 
` 

سيحتوي الملف على قائمة بجميع الحزم المثبتة في البيئة الحالية ، والإصدارات الخاصة بها. سيساعدك هذا على إطلاق مشروعك باستخدام الوحدات التابعة الخاصة به.

### إلغاء تنشيط بيئة

إذا انتهيت من العمل مع البيئة الافتراضية ، يمكنك إلغاء تنشيطها باستخدام:

 `deactivate 
` 

هذا يعيدك إلى مترجم Python الافتراضي الخاص بالنظام مع كافة المكتبات المثبتة به.

### حذف بيئة

ببساطة حذف مجلد البيئة.

## كوندا

[`Conda`](https://conda.io/docs/index.html) هو حزمة ، والتبعية وإدارة البيئة للعديد من اللغات ، بما في ذلك بايثون.

لتثبيت Conda ، اتبع هذه [التعليمات](https://conda.io/docs/user-guide/install/index.html) .

### خلق بيئة

لإنشاء استخدام بيئة افتراضية:

 `conda create --name my-env 
` 

سوف Conda إنشاء مجلد المقابلة داخل دليل التثبيت كوندا.

يمكنك أيضًا تحديد إصدار Python الذي تريد العمل معه:

 `conda create --name my-env python=3.6 
` 

### قائمة البيئات

يمكنك سرد جميع البيئات المتاحة مع:

 `conda info --envs 
` 

### تفعيل بيئة

قبل أن تتمكن من البدء في استخدام البيئة ، يلزمك تنشيطها:

 `source activate my-env 
` 

### تثبيت الحزم

نفس الشيء مع `virtualenv` .

### إلغاء تنشيط بيئة

إذا انتهيت من العمل مع البيئة الافتراضية ، يمكنك إلغاء تنشيطها باستخدام:

 `source deactivate 
` 

### قم بإزالة بيئة

إذا كنت تريد إزالة بيئة من استخدام Conda:

 `conda remove --name my-env 
` 

#### معلومات اكثر:

*   `virtualenv` [الموقع الرسمي](https://virtualenv.pypa.io/en/stable/)
*   [الموقع الرسمي](https://conda.io/docs/index.html) `Conda`
*   `The Hitchhicker's Guide to Python` [Hitchhicker](http://docs.python-guide.org/en/latest/dev/virtualenvs/) `The Hitchhicker's Guide to Python` - [Pypenv والبيئات الافتراضية](http://docs.python-guide.org/en/latest/dev/virtualenvs/)
# 🕌 دليل الـ APIs الإسلامية المجانية — Islamic Free APIs Guide

> جميع الـ APIs الواردة في هذا الدليل **مجانية بالكامل** ولا تحتاج إلى API Key
>
> ---
>
> ## 📋 جدول المحتويات
>
> 1. [مواقيت الصلاة — AlAdhan API](#1--مواقيت-الصلاة--aladhan-api)
> 2. 2. [القرآن الكريم — AlQuran Cloud API](#2--القرآن-الكريم--alquran-cloud-api)
>    3. 3. [القرآن الكريم — fawazahmed0 Quran API](#3--القرآن-الكريم--fawazahmed0-quran-api)
>       4. 4. [الأذكار والأدعية](#4--الأذكار-والأدعية)
>          5. 5. [القبلة والتسبيح](#5--القبلة-والتسبيح)
>             6. 6. [الأحاديث النبوية — Hadith API](#6--الأحاديث-النبوية--hadith-api)
>                7. 7. [الـ Stack المقترح](#7--الـ-stack-المقترح)
>                   8. 8. [جدول مقارنة شامل](#8--جدول-مقارنة-شامل)
>                     
>                      9. ---
>                     
>                      10. ## 1. 🕌 مواقيت الصلاة — AlAdhan API
>                     
>                      11. **Base URL:** `https://api.aladhan.com/v1`
> **التوثيق الرسمي:** https://aladhan.com/prayer-times-api
> **مجاني:** ✅ | **بدون API Key:** ✅ | **بدون Rate Limit:** ✅
>
> ### الميزات
>
> | الميزة | الوصف |
> |--------|-------|
> | GPS تلقائي | ترسل Latitude + Longitude وترجع الأوقات |
> | الصلوات الخمس | + الإمساك، الشروق، المغرب، منتصف الليل |
> | طرق الحساب | 24 طريقة مختلفة |
> | التقويم الهجري | مدمج في كل Response |
> | تقويم شهري/سنوي | Calendar API كامل |
> | الصلاة القادمة | Endpoint مخصص |
>
> ### طرق الحساب المدعومة (method parameter)
>
> | الرقم | الطريقة |
> |-------|---------|
> | 0 | جعفري / شيعة اثنا عشرية |
> | 1 | جامعة العلوم الإسلامية، كراتشي |
> | 2 | الجمعية الإسلامية لأمريكا الشمالية |
> | 3 | رابطة العالم الإسلامي ⭐ |
> | 4 | جامعة أم القرى، مكة المكرمة ⭐ |
> | 5 | الهيئة المصرية العامة للمساحة ⭐ |
> | 7 | معهد الجيوفيزياء، جامعة طهران |
> | 8 | منطقة الخليج |
> | 9 | الكويت |
> | 10 | قطر |
> | 11 | مجلس الأديان الإسلامية، سنغافورة |
> | 12 | الاتحاد الإسلامي في فرنسا |
> | 13 | رئاسة الشؤون الدينية، تركيا |
> | 14 | الإدارة الروحية للمسلمين في روسيا |
> | 15 | لجنة رؤية الهلال العالمية |
> | 16 | دبي (تجريبي) |
> | 17 | ماليزيا (JAKIM) |
> | 18 | تونس |
> | 19 | الجزائر |
> | 20 | إندونيسيا (KEMENAG) |
> | 21 | المغرب |
> | 22 | البرتغال |
> | 23 | الأردن |
> | 99 | مخصص (Custom) |
>
> ### الـ Endpoints الأساسية
>
> ```http
> # مواقيت صلاة بتاريخ محدد + إحداثيات
> GET /v1/timings/{DD-MM-YYYY}?latitude=30.06&longitude=31.24&method=5
>
> # مواقيت صلاة بعنوان نصي
> GET /v1/timingsByAddress/{DD-MM-YYYY}?address=Cairo,Egypt&method=5
>
> # مواقيت صلاة بمدينة
> GET /v1/timingsByCity/{DD-MM-YYYY}?city=Cairo&country=Egypt&method=5
>
> # الصلاة القادمة
> GET /v1/nextPrayer/{DD-MM-YYYY}?latitude=30.06&longitude=31.24&method=5
>
> # تقويم شهري
> GET /v1/calendar/{year}/{month}?latitude=30.06&longitude=31.24&method=5
>
> # تقويم سنوي
> GET /v1/calendar/{year}?latitude=30.06&longitude=31.24&method=5
>
> # قائمة طرق الحساب
> GET /v1/methods
>
> # تحويل تاريخ ميلادي إلى هجري
> GET /v1/gToH/{DD-MM-YYYY}
>
> # تحويل تاريخ هجري إلى ميلادي
> GET /v1/hToG/{DD-MM-YYYY-iH}
>
> # اتجاه القبلة
> GET /v1/qibla/{latitude}/{longitude}
> ```
>
> ### مثال على الـ Response
>
> ```json
> {
>   "code": 200,
>   "status": "OK",
>   "data": {
>     "timings": {
>       "Fajr": "04:12",
>       "Sunrise": "05:43",
>       "Dhuhr": "12:01",
>       "Asr": "15:25",
>       "Sunset": "18:19",
>       "Maghrib": "18:19",
>       "Isha": "19:45",
>       "Imsak": "04:02",
>       "Midnight": "00:01"
>     },
>     "date": {
>       "readable": "25 Jun 2026",
>       "hijri": {
>         "date": "29-12-1447",
>         "month": { "en": "Dhūl-Ḥijjah", "ar": "ذُو الحِجَّة" },
>         "year": "1447"
>       }
>     },
>     "meta": {
>       "method": { "id": 5, "name": "Egyptian General Authority of Survey" }
>     }
>   }
> }
> ```
>
> ### Query Parameters المهمة
>
> | Parameter | النوع | الوصف |
> |-----------|-------|-------|
> | `latitude` | number | خط العرض (مطلوب) |
> | `longitude` | number | خط الطول (مطلوب) |
> | `method` | integer | طريقة الحساب (0-23, 99) |
> | `school` | integer | 0 = شافعي، 1 = حنفي |
> | `tune` | string | ضبط الأوقات بالدقائق |
> | `timezonestring` | string | مثل: `Africa/Cairo` |
> | `latitudeAdjustmentMethod` | integer | للمناطق القطبية |
> | `iso8601` | boolean | تنسيق الوقت ISO |
>
> > **ملاحظة حول الأذان الصوتي:** AlAdhan API لا توفر ملفات أذان، يُنصح بتخزين ملف أذان محلياً في التطبيق وتشغيله عند حلول وقت الصلاة.
> >
> > ---
> >
> > ## 2. 📖 القرآن الكريم — AlQuran Cloud API
> >
> > **Base URL:** `https://api.alquran.cloud/v1`
> > **التوثيق الرسمي:** https://alquran.cloud/api
> > **مجاني:** ✅ | **بدون API Key:** ✅
> >
> > ### الميزات
> >
> > | الميزة | الوصف |
> > |--------|-------|
> > | النص الكامل | 114 سورة، كل آية منفردة أو كاملة |
> > | التلاوة الصوتية | أكثر من 100 قارئ عبر الـ editions |
> > | التفسير | editions متعددة للتفاسير |
> > | البحث | بحث في نص القرآن |
> > | التقسيمات | جزء، حزب، ربع، ركوع، صفحة، سجدة |
> >
> > ### الـ Editions المتاحة
> >
> > ```http
> > # قائمة جميع الـ editions (نصوص + ترجمات + تلاوات)
> > GET /v1/edition
> >
> > # فلترة نوع معين
> > GET /v1/edition?type=quran     # النصوص القرآنية
> > GET /v1/edition?type=tafsir    # التفاسير
> > GET /v1/edition?type=audio     # التلاوات الصوتية
> > GET /v1/edition?language=ar    # العربية فقط
> > ```
> >
> > ### أمثلة على الـ Editions المشهورة
> >
> > | الـ Edition | النوع | الوصف |
> > |-------------|-------|-------|
> > | `ar.alafasy` | صوتي | مشاري العفاسي |
> > | `ar.abdulsamad` | صوتي | عبد الصمد |
> > | `ar.abdullahbasfar` | صوتي | عبدالله بصفر |
> > | `ar.hudhaify` | صوتي | علي الحذيفي |
> > | `quran-simple` | نص | النص العربي المبسط |
> > | `quran-uthmani` | نص | النص العثماني |
> > | `ar.muyassar` | تفسير | الميسر |
> > | `en.sahih` | ترجمة | صحيح إنترناشيونال |
> >
> > ### الـ Endpoints الأساسية
> >
> > ```http
> > # قائمة جميع السور
> > GET /v1/surah
> >
> > # سورة كاملة (نص فقط)
> > GET /v1/surah/1
> >
> > # سورة كاملة بـ edition محدد (نص + صوت)
> > GET /v1/surah/1/ar.alafasy
> >
> > # سورة بأكثر من edition في نفس الوقت
> > GET /v1/surah/1/editions/quran-simple,ar.alafasy,en.sahih
> >
> > # آية مفردة بالرقم الكلي (1-6236)
> > GET /v1/ayah/1
> >
> > # آية مفردة بـ edition
> > GET /v1/ayah/1/ar.alafasy
> >
> > # آية بـ editions متعددة
> > GET /v1/ayah/1/editions/quran-simple,ar.alafasy
> >
> > # آية عشوائية
> > GET /v1/ayah/random
> >
> > # آية عشوائية بـ edition
> > GET /v1/ayah/random/ar.alafasy
> >
> > # البحث في القرآن
> > GET /v1/search/{keyword}/{surah}/{edition}
> > GET /v1/search/بسم/all/ar           # بحث في كل السور
> > GET /v1/search/mercy/all/en.sahih   # بحث في الترجمة
> >
> > # جزء كامل
> > GET /v1/juz/1/quran-simple
> >
> > # صفحة كاملة
> > GET /v1/page/1/quran-simple
> >
> > # ربع حزب
> > GET /v1/hizbquarter/1/quran-simple
> >
> > # ركوع
> > GET /v1/ruku/1/quran-simple
> >
> > # آيات السجود
> > GET /v1/sajda/quran-simple
> >
> > # معلومات عامة
> > GET /v1/meta
> > ```
> >
> > ### مثال على Response سورة
> >
> > ```json
> > {
> >   "code": 200,
> >   "status": "OK",
> >   "data": {
> >     "number": 1,
> >     "name": "سُورَةُ ٱلْفَاتِحَةِ",
> >     "englishName": "Al-Faatiha",
> >     "englishNameTranslation": "The Opening",
> >     "numberOfAyahs": 7,
> >     "ayahs": [
> >       {
> >         "number": 1,
> >         "text": "بِسْمِ ٱللَّهِ ٱلرَّحْمَٰنِ ٱلرَّحِيمِ",
> >         "numberInSurah": 1,
> >         "juz": 1,
> >         "page": 1,
> >         "audio": "https://cdn.islamic.network/quran/audio/128/ar.alafasy/1.mp3",
> >         "audioSecondary": [...]
> >       }
> >     ],
> >     "edition": {
> >       "identifier": "ar.alafasy",
> >       "name": "Mishary Alafasy",
> >       "type": "audio"
> >     }
> >   }
> > }
> > ```
> >
> > ---
> >
> > ## 3. 📖 القرآن الكريم — fawazahmed0 Quran API
> >
> > **Base URL:** `https://cdn.jsdelivr.net/gh/fawazahmed0/quran-api@1/`
> > **GitHub:** https://github.com/fawazahmed0/quran-api
> > **مجاني:** ✅ | **بدون API Key:** ✅ | **بدون Rate Limit:** ✅
> >
> > ### الميزات
> >
> > | الميزة | الوصف |
> > |--------|-------|
> > | 90+ لغة | 440+ ترجمة |
> > | CDN سريع | يعمل عبر jsDelivr CDN |
> > | بدون Server | Static JSON files |
> > | Offline جاهز | يمكن تحميل الملفات كاملة |
> > | تدعم Latin Script | نسخ بحروف لاتينية |
> >
> > ### الـ Endpoints الأساسية
> >
> > ```
> > # قائمة جميع الـ editions المتاحة
> > https://cdn.jsdelivr.net/gh/fawazahmed0/quran-api@1/editions.json
> >
> > # النص العربي الكامل
> > https://cdn.jsdelivr.net/gh/fawazahmed0/quran-api@1/editions/ara-quranindopak.json
> >
> > # سورة محددة (رقم السورة)
> > https://cdn.jsdelivr.net/gh/fawazahmed0/quran-api@1/editions/ara-quranindopak/1.json
> >
> > # آية محددة (رقم السورة / رقم الآية)
> > https://cdn.jsdelivr.net/gh/fawazahmed0/quran-api@1/editions/ara-quranindopak/1/1.json
> >
> > # جزء محدد
> > https://cdn.jsdelivr.net/gh/fawazahmed0/quran-api@1/editions/ara-quranindopak/juzs/1.json
> >
> > # صفحة محددة
> > https://cdn.jsdelivr.net/gh/fawazahmed0/quran-api@1/editions/ara-quranindopak/pages/1.json
> >
> > # معلومات القرآن (عدد الأجزاء، السجدات، إلخ)
> > https://cdn.jsdelivr.net/gh/fawazahmed0/quran-api@1/info.json
> >
> > # قائمة الخطوط العربية المتاحة
> > https://cdn.jsdelivr.net/gh/fawazahmed0/quran-api@1/fonts.json
> > ```
> >
> > > **ملاحظة:** كل رابط يدعم صيغتين:
> > > > `.json` للنسخة الكاملة
> > > > > `.min.json` للنسخة المضغوطة (أسرع)
> > > > >
> > > > > ---
> > > > >
> > > > > ## 4. 📿 الأذكار والأدعية
> > > > >
> > > > > ### المصادر المتاحة
> > > > >
> > > > > #### أ) Azkar API (JSON جاهز)
> > > > >
> > > > > ```
> > > > > https://raw.githubusercontent.com/nawafalqari/azkar-api/main/azkar.json
> > > > > ```
> > > > >
> > > > > **يشمل:**
> > > > > - أذكار الصباح
> > > > > - - أذكار المساء
> > > > >   - - أذكار بعد الصلاة
> > > > >     - - أذكار النوم والاستيقاظ
> > > > >       - - أدعية مأثورة
> > > > >         - - عداد التكرار لكل ذكر
> > > > >          
> > > > >           - #### ب) Athkar App JSON
> > > > >          
> > > > >           - ```
> > > > >             https://raw.githubusercontent.com/osamayy/athkar-app/main/src/data/athkar.json
> > > > >             ```
> > > > >
> > > > > ### نموذج بنية البيانات
> > > > >
> > > > > ```json
> > > > > {
> > > > >   "category": "أذكار الصباح",
> > > > >   "count": 12,
> > > > >   "adhkar": [
> > > > >     {
> > > > >       "zekr": "أَصْبَحْنَا وَأَصْبَحَ الْمُلْكُ لِلَّهِ...",
> > > > >       "repeat": 1,
> > > > >       "audio": null
> > > > >     }
> > > > >   ]
> > > > > }
> > > > > ```
> > > > >
> > > > > > **💡 نصيحة:** يُفضَّل تخزين الأذكار **محلياً** في التطبيق (JSON ملف مدمج) لأنها:
> > > > > > > - ثابتة ولا تحتاج تحديثاً مستمراً
> > > > > > > - > - تعمل Offline
> > > > > > >   > - > - أسرع في العرض
> > > > > > >   >   >
> > > > > > >   >   > - ---
> > > > > > >   >   >
> > > > > > >   >   > ## 5. 🧭 القبلة والتسبيح
> > > > > > >   >   >
> > > > > > >   >   > ### القبلة — AlAdhan Qibla API
> > > > > > >   >   >
> > > > > > >   >   > ```http
> > > > > > >   >   > GET https://api.aladhan.com/v1/qibla/{latitude}/{longitude}
> > > > > > >   >   > ```
> > > > > > >   >   >
> > > > > > >   >   > **مثال:**
> > > > > > >   >   > ```http
> > > > > > >   >   > GET https://api.aladhan.com/v1/qibla/30.06/31.24
> > > > > > >   >   > ```
> > > > > > >   >   >
> > > > > > >   >   > **الـ Response:**
> > > > > > >   >   > ```json
> > > > > > >   >   > {
> > > > > > >   >   >   "code": 200,
> > > > > > >   >   >   "status": "OK",
> > > > > > >   >   >   "data": {
> > > > > > >   >   >     "latitude": 30.06,
> > > > > > >   >   >     "longitude": 31.24,
> > > > > > >   >   >     "direction": 136.87
> > > > > > >   >   >   }
> > > > > > >   >   > }
> > > > > > >   >   > ```
> > > > > > >   >   >
> > > > > > >   >   > > `direction` = الزاوية بالدرجات من الشمال باتجاه القبلة
> > > > > > >   >   > >
> > > > > > >   >   > > ### البوصلة — Browser APIs (مجانية ومدمجة)
> > > > > > >   >   > >
> > > > > > >   >   > > ```javascript
> > > > > > >   >   > > // الحصول على الموقع الجغرافي
> > > > > > >   >   > > navigator.geolocation.getCurrentPosition((position) => {
> > > > > > >   >   > >   const lat = position.coords.latitude;
> > > > > > >   >   > >   const lon = position.coords.longitude;
> > > > > > >   >   > >
> > > > > > >   >   > >   // جلب اتجاه القبلة من API
> > > > > > >   >   > >   fetch(`https://api.aladhan.com/v1/qibla/${lat}/${lon}`)
> > > > > > >   >   > >     .then(res => res.json())
> > > > > > >   >   > >     .then(data => {
> > > > > > >   >   > >       const qiblaDirection = data.data.direction;
> > > > > > >   >   > >       console.log('اتجاه القبلة:', qiblaDirection, '°');
> > > > > > >   >   > >     });
> > > > > > >   >   > > });
> > > > > > >   >   > >
> > > > > > >   >   > > // استخدام بوصلة الجهاز
> > > > > > >   >   > > window.addEventListener('deviceorientationabsolute', (event) => {
> > > > > > >   >   > >   const compass = event.alpha; // زاوية الجهاز
> > > > > > >   >   > >   const qiblaAngle = qiblaDirection - compass;
> > > > > > >   >   > >   // ضبط مؤشر القبلة
> > > > > > >   >   > > });
> > > > > > >   >   > > ```
> > > > > > >   >   > >
> > > > > > >   >   > > ### عداد التسبيح — Local Implementation
> > > > > > >   >   > >
> > > > > > >   >   > > ```javascript
> > > > > > >   >   > > // حفظ في localStorage
> > > > > > >   >   > > const saveProgress = (dhikr, count) => {
> > > > > > >   >   > >   const today = new Date().toISOString().split('T')[0];
> > > > > > >   >   > >   const key = `tasbeeh_${today}_${dhikr}`;
> > > > > > >   >   > >   localStorage.setItem(key, JSON.stringify({ count, date: today }));
> > > > > > >   >   > > };
> > > > > > >   >   > >
> > > > > > >   >   > > // استرجاع سجل يومي
> > > > > > >   >   > > const getDailyHistory = () => {
> > > > > > >   >   > >   const today = new Date().toISOString().split('T')[0];
> > > > > > >   >   > >   return Object.entries(localStorage)
> > > > > > >   >   > >     .filter(([key]) => key.includes(`tasbeeh_${today}`))
> > > > > > >   >   > >     .map(([key, value]) => ({ dhikr: key.split('_')[2], ...JSON.parse(value) }));
> > > > > > >   >   > > };
> > > > > > >   >   > > ```
> > > > > > >   >   > >
> > > > > > >   >   > > > **Vibration API** للاهتزاز عند الضغط:
> > > > > > >   >   > > > > ```javascript
> > > > > > >   >   > > > > > navigator.vibrate(50); // اهتزاز 50ms
> > > > > > >   >   > > > > > ```
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ---
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ## 6. 📚 الأحاديث النبوية — Hadith API
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > **Base URL:** `https://cdn.jsdelivr.net/gh/fawazahmed0/hadith-api@1/`
> > > > > > >   >   > > > > **GitHub:** https://github.com/fawazahmed0/hadith-api
> > > > > > >   >   > > > > **مجاني:** ✅ | **بدون API Key:** ✅ | **بدون Rate Limit:** ✅
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ### الـ Endpoints الأساسية
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ```
> > > > > > >   >   > > > > # قائمة جميع الـ editions المتاحة
> > > > > > >   >   > > > > https://cdn.jsdelivr.net/gh/fawazahmed0/hadith-api@1/editions.json
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > # كتاب حديث كامل (أبو داود - إنجليزي)
> > > > > > >   >   > > > > https://cdn.jsdelivr.net/gh/fawazahmed0/hadith-api@1/editions/eng-abudawud.json
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > # حديث محدد برقمه
> > > > > > >   >   > > > > https://cdn.jsdelivr.net/gh/fawazahmed0/hadith-api@1/editions/eng-abudawud/1035.json
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > # قسم محدد
> > > > > > >   >   > > > > https://cdn.jsdelivr.net/gh/fawazahmed0/hadith-api@1/editions/eng-abudawud/sections/7.json
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > # معلومات عامة (درجات الأحاديث، المراجع)
> > > > > > >   >   > > > > https://cdn.jsdelivr.net/gh/fawazahmed0/hadith-api@1/info.json
> > > > > > >   >   > > > > ```
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ### الكتب المتاحة (أمثلة)
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > | الاسم | الـ Identifier |
> > > > > > >   >   > > > > |-------|---------------|
> > > > > > >   >   > > > > | صحيح البخاري | `ara-bukhari` |
> > > > > > >   >   > > > > | صحيح مسلم | `ara-muslim` |
> > > > > > >   >   > > > > | سنن أبي داود | `ara-abudawud` |
> > > > > > >   >   > > > > | جامع الترمذي | `ara-tirmidhi` |
> > > > > > >   >   > > > > | سنن ابن ماجه | `ara-ibnmajah` |
> > > > > > >   >   > > > > | سنن النسائي | `ara-nasai` |
> > > > > > >   >   > > > > | موطأ مالك | `ara-malik` |
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ---
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ## 7. 🗺️ الـ Stack المقترح
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ```
> > > > > > >   >   > > > > ┌─────────────────────────────────────────────────────┐
> > > > > > >   >   > > > > │               Islamic App Architecture               │
> > > > > > >   >   > > > > ├─────────────────┬───────────────────────────────────┤
> > > > > > >   >   > > > > │ الوظيفة         │ الحل المقترح                        │
> > > > > > >   >   > > > > ├─────────────────┼───────────────────────────────────┤
> > > > > > >   >   > > > > │ 🕌 مواقيت صلاة │ AlAdhan API                        │
> > > > > > >   >   > > > > │ 📿 أذكار        │ JSON ملف محلي (Offline)             │
> > > > > > >   >   > > > > │ 📖 قرآن (نص)   │ AlQuran Cloud / fawazahmed0        │
> > > > > > >   >   > > > > │ 🔊 تلاوة صوتية │ AlQuran Cloud (audio editions)     │
> > > > > > >   >   > > > > │ 🔍 بحث قرآني   │ AlQuran Cloud /search endpoint     │
> > > > > > >   >   > > > > │ 🧭 القبلة       │ AlAdhan /qibla + DeviceOrientation │
> > > > > > >   >   > > > > │ 📿 تسبيح       │ Local (localStorage / SQLite)       │
> > > > > > >   >   > > > > │ 📚 أحاديث      │ fawazahmed0 Hadith API              │
> > > > > > >   >   > > > > │ 🌙 Dark Mode    │ CSS media query / منطق محلي        │
> > > > > > >   >   > > > > └─────────────────┴───────────────────────────────────┘
> > > > > > >   >   > > > > ```
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ### نموذج JavaScript شامل
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ```javascript
> > > > > > >   >   > > > > const IslamicAPI = {
> > > > > > >   >   > > > >   // مواقيت الصلاة
> > > > > > >   >   > > > >   getPrayerTimes: async (lat, lon, method = 5) => {
> > > > > > >   >   > > > >     const today = new Date();
> > > > > > >   >   > > > >     const date = `${today.getDate()}-${today.getMonth()+1}-${today.getFullYear()}`;
> > > > > > >   >   > > > >     const url = `https://api.aladhan.com/v1/timings/${date}?latitude=${lat}&longitude=${lon}&method=${method}`;
> > > > > > >   >   > > > >     const res = await fetch(url);
> > > > > > >   >   > > > >     return res.json();
> > > > > > >   >   > > > >   },
> > > > > > >   >   > > > >
> > > > > > >   >   > > > >   // اتجاه القبلة
> > > > > > >   >   > > > >   getQibla: async (lat, lon) => {
> > > > > > >   >   > > > >     const res = await fetch(`https://api.aladhan.com/v1/qibla/${lat}/${lon}`);
> > > > > > >   >   > > > >     return res.json();
> > > > > > >   >   > > > >   },
> > > > > > >   >   > > > >
> > > > > > >   >   > > > >   // سورة من القرآن مع صوت
> > > > > > >   >   > > > >   getSurah: async (surahNum, edition = 'ar.alafasy') => {
> > > > > > >   >   > > > >     const res = await fetch(`https://api.alquran.cloud/v1/surah/${surahNum}/${edition}`);
> > > > > > >   >   > > > >     return res.json();
> > > > > > >   >   > > > >   },
> > > > > > >   >   > > > >
> > > > > > >   >   > > > >   // بحث في القرآن
> > > > > > >   >   > > > >   searchQuran: async (keyword, surah = 'all', edition = 'ar') => {
> > > > > > >   >   > > > >     const res = await fetch(`https://api.alquran.cloud/v1/search/${keyword}/${surah}/${edition}`);
> > > > > > >   >   > > > >     return res.json();
> > > > > > >   >   > > > >   },
> > > > > > >   >   > > > >
> > > > > > >   >   > > > >   // الصلاة القادمة
> > > > > > >   >   > > > >   getNextPrayer: async (lat, lon, method = 5) => {
> > > > > > >   >   > > > >     const today = new Date();
> > > > > > >   >   > > > >     const date = `${today.getDate()}-${today.getMonth()+1}-${today.getFullYear()}`;
> > > > > > >   >   > > > >     const res = await fetch(`https://api.aladhan.com/v1/nextPrayer/${date}?latitude=${lat}&longitude=${lon}&method=${method}`);
> > > > > > >   >   > > > >     return res.json();
> > > > > > >   >   > > > >   }
> > > > > > >   >   > > > > };
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > // مثال على الاستخدام
> > > > > > >   >   > > > > navigator.geolocation.getCurrentPosition(async ({ coords }) => {
> > > > > > >   >   > > > >   const { latitude, longitude } = coords;
> > > > > > >   >   > > > >
> > > > > > >   >   > > > >   const prayers = await IslamicAPI.getPrayerTimes(latitude, longitude);
> > > > > > >   >   > > > >   console.log('مواقيت الصلاة:', prayers.data.timings);
> > > > > > >   >   > > > >
> > > > > > >   >   > > > >   const qibla = await IslamicAPI.getQibla(latitude, longitude);
> > > > > > >   >   > > > >   console.log('اتجاه القبلة:', qibla.data.direction, '°');
> > > > > > >   >   > > > > });
> > > > > > >   >   > > > > ```
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ---
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ## 8. 📊 جدول مقارنة شامل
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > | الـ API | الوظيفة | Base URL | مجاني | بدون Key | Rate Limit |
> > > > > > >   >   > > > > |---------|---------|----------|-------|----------|------------|
> > > > > > >   >   > > > > | **AlAdhan** | مواقيت الصلاة | `api.aladhan.com/v1` | ✅ | ✅ | لا يوجد |
> > > > > > >   >   > > > > | **AlAdhan** | القبلة | `api.aladhan.com/v1/qibla` | ✅ | ✅ | لا يوجد |
> > > > > > >   >   > > > > | **AlAdhan** | التقويم الهجري | `api.aladhan.com/v1/gToH` | ✅ | ✅ | لا يوجد |
> > > > > > >   >   > > > > | **AlQuran Cloud** | القرآن + صوت + بحث | `api.alquran.cloud/v1` | ✅ | ✅ | محدود |
> > > > > > >   >   > > > > | **fawazahmed0 Quran** | القرآن متعدد اللغات | `cdn.jsdelivr.net/gh/fawazahmed0/quran-api@1` | ✅ | ✅ | لا يوجد |
> > > > > > >   >   > > > > | **fawazahmed0 Hadith** | الأحاديث النبوية | `cdn.jsdelivr.net/gh/fawazahmed0/hadith-api@1` | ✅ | ✅ | لا يوجد |
> > > > > > >   >   > > > > | **Azkar API** | أذكار وأدعية | GitHub Raw | ✅ | ✅ | لا يوجد |
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ---
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > ## 🔗 روابط مفيدة
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > - [AlAdhan API Documentation](https://aladhan.com/prayer-times-api)
> > > > > > >   >   > > > > - - [AlQuran Cloud API](https://alquran.cloud/api)
> > > > > > >   >   > > > >   - - [fawazahmed0/quran-api على GitHub](https://github.com/fawazahmed0/quran-api)
> > > > > > >   >   > > > >     - - [fawazahmed0/hadith-api على GitHub](https://github.com/fawazahmed0/hadith-api)
> > > > > > >   >   > > > >       - - [طرق حساب مواقيت الصلاة](https://aladhan.com/calculation-methods)
> > > > > > >   >   > > > >        
> > > > > > >   >   > > > >         - ---
> > > > > > >   >   > > > >
> > > > > > >   >   > > > > > **ملاحظة:** هذا الدليل تم إعداده بتاريخ يونيو 2026. قد تتغير بعض التفاصيل مع تحديثات الـ APIs. يُنصح دائماً بمراجعة التوثيق الرسمي.

# Report-6-2



---

# گزارش پروژه: پخش نت موسیقی با فشار دادن دکمه (Simple Buzzer with Button)

## ۱. مقدمه  
در این پروژه، یک **دکمه** به آردوینو متصل شده است و با فشار دادن آن، یک نت موسیقی خاص (مثلاً نت D) پخش می‌شود..


## ۳. قطعات مورد استفاده  
- برد آردوینو Uno  
- یک دکمه (Push Button)  
- یک buzzer (سیم‌پیچ صوتی)  
- یک مقاومت pull-up (مثلاً ۱۰k اهم)  
- برد برد (Breadboard)  
- سیم‌های جامپر (jumper wires)



## ۴. نحوه‌ی ساخت مدار  
- **دکمه**:  
  - یک سر → **پین دیجیتال ۷** آردوینو  
  - سر دیگر → **GND**  
  - یک مقاومت pull-up (۱۰k اهم) بین پین ۷ و 5V قرار دهید.  
- **buzzer**:  
  - یک سر → **پین دیجیتال ۸** آردوینو  
  - سر دیگر → **GND**
.

## ۵. کد برنامه (اسکچ):

```cpp
#define BUZZER_PIN 8   // تعریف پین buzzer
#define BTN_PIN 7      // تعریف پین دکمه
#define T_D 400        // تعریف فرکانس نت D

void setup() {
  pinMode(BUZZER_PIN, OUTPUT);   // تنظیم پین buzzer به عنوان خروجی
  pinMode(BTN_PIN, INPUT_PULLUP); // تنظیم پین دکمه به عنوان ورودی با مقاومت pull-up
}

void loop() {
  // اگر دکمه فشرده شود → نت D پخش شود
  while (digitalRead(BTN_PIN) == LOW) {
    tone(BUZZER_PIN, T_D);
  }

  // اگر دکمه رها شود → buzzer خاموش شود
  noTone(BUZZER_PIN);
}
```

### توضیح کد:  
- `#define BUZZER_PIN 8` — تعریف پین buzzer.  
- `#define BTN_PIN 7` — تعریف پین دکمه.  
- `#define T_D 400` — تعریف فرکانس نت D (۴۰۰ هرتز).  
- `pinMode(BTN_PIN, INPUT_PULLUP)` — تنظیم پین دکمه به عنوان ورودی با مقاومت pull-up.  
- `while (digitalRead(BTN_PIN) == LOW)` — اگر دکمه فشرده شود، نت D پخش شود.  
- `tone(BUZZER_PIN, T_D);` — پخش نت D با فرکانس مشخص.  
- `noTone(BUZZER_PIN);` — خاموش کردن buzzer وقتی دکمه رها شود.

## ۶. نحوه‌ی کارکرد  
- پس از آپلود کد، با فشار دادن دکمه، نت D پخش می‌شود.  
- اگر دکمه را رها کنید، buzzer خاموش می‌شود.

## ۷. نتایج  
buzzer به درستی نت D را با فشار دادن دکمه پخش می‌کند.

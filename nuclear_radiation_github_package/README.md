# ☢️ Nuclear Radiation Safety Monitor

**Developer:** Abdulla Aldhaen  
**Version:** 1.0.0  
**Blueprint path:** `blueprints/automation/abdullah_aldaen/nuclear_radiation_safety_monitor.yaml`

## Import Blueprint

After this repository is writable and the YAML file is uploaded, use:

[Import Blueprint to Home Assistant](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fabdullahaldaen%2Fdevelopers.home-assistant%2Fmaster%2Fblueprints%2Fautomation%2Fabdullah_aldaen%2Fnuclear_radiation_safety_monitor.yaml)

Raw YAML:

```text
https://raw.githubusercontent.com/abdullahaldaen/developers.home-assistant/master/blueprints/automation/abdullah_aldaen/nuclear_radiation_safety_monitor.yaml
```

## What it does

- 🟢 **Green:** reading is below the yellow threshold.
- 🟡 **Yellow:** reading must stay in the yellow zone for the selected confirmation time.
- 🔴 **Red:** reading must stay at or above the red threshold for the selected confirmation time.
- 📱 Sends notifications to selected `notify` entities.
- 🚨 Supports optional iPhone emergency/critical alerts.
- 🏠 Creates a persistent notification in Home Assistant.
- 🔊 Can announce through Alexa Speak/Announce `notify` entities.
- 🗣️ Can announce through Google Home / Nest using `tts.speak`.
- 🌙 Supports quiet hours for voice announcements.
- 🔁 Can repeat red warnings while the reading remains red.
- 🌐 Supports Arabic and English alert text.

## طريقة العمل

- 🟢 **الأخضر:** القراءة أقل من بداية المنطقة الصفراء.
- 🟡 **الأصفر:** يجب أن تبقى القراءة داخل المنطقة الصفراء طوال مدة التأكيد.
- 🔴 **الأحمر:** يجب أن تبقى القراءة عند بداية المنطقة الحمراء أو أعلى طوال مدة التأكيد.
- 📱 يرسل التنبيهات إلى أجهزة `notify` المختارة.
- 🚨 يدعم تنبيه طوارئ للآيفون عند تأكيد الأحمر.
- 🏠 يظهر إشعاراً دائماً داخل Home Assistant.
- 🔊 يدعم قراءة التنبيه على Alexa.
- 🗣️ يدعم Google Home / Nest عبر `tts.speak`.
- 🌙 يدعم ساعات الهدوء للتنبيهات الصوتية.
- 🔁 يقدر يعيد تنبيه الأحمر إذا استمر الخطر.
- 🌐 الرسائل بالعربي أو الإنجليزي حسب اختيارك.

## Recommended starting settings / القيم الابتدائية المقترحة

| Setting | Suggested value | Arabic |
|---|---:|---|
| Yellow Zone Start | `0.30` | بداية الأصفر |
| Yellow Confirmation | `5 s` | مدة تأكيد الأصفر |
| Red Zone Start | `0.50` | بداية الأحمر |
| Red Confirmation | `5 s` | مدة تأكيد الأحمر |
| Safe Return Confirmation | `10 s` | مدة تأكيد العودة للأخضر |
| Repeat Red Alert | `On` | تكرار الأحمر |
| Red Repeat Interval | `5 min` | تكرار كل 5 دقائق |

> These values are automation alert thresholds only. They are not universal medical, legal, or regulatory safety limits.  
> هذه القيم حدود تنبيه للأتمتة فقط، وليست حدود أمان طبية أو قانونية أو تنظيمية عالمية.

## iPhone Emergency setup / إعداد طوارئ الآيفون

In **🚨 iPhone Emergency / طوارئ الآيفون**, add a Mobile App notification action for each iPhone.

Use these templates inside the action:

```text
Title: {{ alert_title }}
Message: {{ alert_message }}
```

For iOS Critical Alert, add this under notification data:

```yaml
data:
  push:
    sound:
      name: default
      critical: 1
      volume: 1.0
```

## Alexa setup / إعداد أليكسا

Select Alexa Speak or Announce notify entities in:

```text
🔊 Alexa Speak/Announce / أجهزة أليكسا
```

The blueprint sends messages using `notify.send_message`.

## Google Home / Nest setup / إعداد Google Home

Select:

1. TTS engine, for example `tts.home_assistant_cloud`.
2. Google Home / Nest media players.

The blueprint sends voice announcements using `tts.speak`.

## Sensor placement note / مكان المستشعر

For stable indoor monitoring, keep the detector in a fixed dry indoor location around **1–1.5 m above the floor**, away from heat, moisture, tampering, and strong electrical interference.

للمراقبة الداخلية المستقرة، يفضل وضع المستشعر في مكان داخلي ثابت وجاف على ارتفاع تقريبي **1–1.5 متر** عن الأرض، وبعيداً عن الحرارة والرطوبة والعبث والتشويش الكهربائي القوي.

## Files

```text
blueprints/automation/abdullah_aldaen/nuclear_radiation_safety_monitor.yaml
README.md
CHANGELOG.md
```

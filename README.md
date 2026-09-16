# Grok Unlimited

Android-приложение — Grok без лимитов.

## Что это

Полноценный чат-клиент для xAI Grok API с системным промптом, который максимально снимает цензуру и корпоративные фильтры.

- Тёмный UI в стиле Grok
- Выбор модели (grok-3, grok-3-mini и т.д.)
- API Key хранится локально
- Работает через официальный OpenAI-compatible endpoint xAI

## Как собрать

### Через GitHub Actions (рекомендуется)

1. Создай репозиторий на GitHub
2. Залей весь этот проект
3. Перейди в Actions → **Build APK** → **Run workflow**
4. Скачай артефакт `GrokUnlimited-debug`

### Локально

```bash
# Нужен Android SDK + JDK 17
./gradlew assembleDebug
# APK будет в app/build/outputs/apk/debug/
```

Если нет `gradlew`:
```bash
gradle wrapper --gradle-version 8.7
./gradlew assembleDebug
```

## Настройка

1. Получи API Key на [console.x.ai](https://console.x.ai)
2. Открой приложение → ⚙ → вставь ключ
3. Выбери модель
4. Спрашивай что угодно

## Важно

- Приложение **не** содержит самого Grok. Оно ходит в официальный API xAI.
- "Без лимитов" достигается агрессивным system prompt + тем, что xAI/Grok сам по себе значительно менее цензурирован, чем Claude/GPT.
- Для production лучше подписывать release APK и хранить ключ безопаснее (сейчас SharedPreferences).

## Структура

```
GrokUnlimitedApp/
├── app/
│   ├── src/main/
│   │   ├── java/com/grok/unlimited/
│   │   │   ├── MainActivity.kt
│   │   │   ├── data/          # API + модели
│   │   │   ├── ui/            # Compose экраны
│   │   │   └── viewmodel/
│   │   ├── res/
│   │   └── AndroidManifest.xml
│   └── build.gradle.kts
├── .github/workflows/build.yml
├── build.gradle.kts
├── settings.gradle.kts
└── README.md
```

Сделано для тебя. Наслаждайся.

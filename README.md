# Memoriva remote config (GitHub Pages)

Статический JSON для `RemoteWebGate` в Android-приложении.

## Быстрый старт

### 1. Создай репозиторий на GitHub

1. Открой [github.com/new](https://github.com/new)
2. Имя: **`memoriva-remote-config`**
3. **Public** (для бесплатного GitHub Pages)
4. Без README / .gitignore (файлы уже есть локально)
5. **Create repository**

### 2. Залей файлы

В терминале (замени `gamedaveocean`, если другой логин):

```bash
cd remote-config
git init
git add config.json README.md
git commit -m "Add remote config for Memoriva"
git branch -M main
git remote add origin https://github.com/gamedaveocean/memoriva-remote-config.git
git push -u origin main
```

### 3. Включи GitHub Pages

1. Репозиторий → **Settings** → **Pages**
2. **Build and deployment** → Source: **Deploy from a branch**
3. Branch: **`main`** / **`/ (root)`**
4. **Save**

Через 1–3 минуты конфиг будет доступен по адресу:

**https://gamedaveocean.github.io/memoriva-remote-config/config.json**

### 4. Проверь в браузере

Должен открыться JSON:

```json
{
  "enabled": false,
  "url": "https://example.com"
}
```

### 5. Управление WebView без пересборки APK

Отредактируй `config.json` на GitHub (кнопка **Edit**):

**Показать WebView:**
```json
{
  "enabled": true,
  "url": "https://твой-сайт.com"
}
```

**Показать игру:**
```json
{
  "enabled": false,
  "url": "https://example.com"
}
```

После коммита подожди ~1 минуту и перезапусти приложение.

## Формат

| Поле | Тип | Значение |
|------|-----|----------|
| `enabled` | boolean | `true` → WebView, `false` → игра |
| `url` | string | Ссылка для WebView (http или https) |

Приложение ищет **первый** `boolean` и **первый** URL в JSON (порядок полей важен).

# Задание 1 Проектирование и разделение на микрофронтенды

## Уровень 1. Подготовка

### Метод интеграции
- **Run time**

### Методы композиции микрофронтендов
- **Клиентская**

### Инструменты для создания микрофронтендов
- **Webpack Module Federation**

### Стратегии управления состоянием
- **Взаимодействие на основе API** (выбор в пользу простоты для несложного приложения).

---

## Уровень 2. Разделение на микрофронтенды

### 1. Shell (общий контейнер)
**Роль**: Объединение всех микрофронтендов. Содержит общий UI (хедер, футер) и маршрутизацию.

**Состав:**
- **Компоненты**:
    - `App.js` — точка входа в приложение.
    - `Footer.js` — футер приложения.
    - `ProtectedRoute.js` — маршрутизация с проверкой доступа.
- **Утилиты**:
    - Общие утилиты для маршрутизации и взаимодействия между микрофронтендами.

```plaintext
shell/
├── src/
│   ├── components/   # Общие компоненты (например, Header, Footer)
│   ├── pages/        # Общие страницы
│   ├── utils/        # Утилиты для маршрутизации и взаимодействия
│   └── index.js      # Точка входа
└── webpack.config.js # Конфигурация Module Federation
```

---

### 2. Auth (микрофронт регистрации и аутентификации пользователя)
**Роль**: Отвечает за регистрацию и авторизацию пользователей.

**Состав:**
- **Компоненты**:
    - `Login.js` — компонент для логина.
    - `Register.js` — компонент для регистрации.
- **Блоки**:
    - `auth-form/` — стили и блоки для форм авторизации.

```plaintext
auth/
├── components/
│   ├── Login.js      # Компонент для логина
│   └── Register.js   # Компонент для регистрации
├── blocks/auth-form/ # Стили и блоки для форм авторизации
└── index.js          # Точка входа
└── webpack.config.js # Конфигурация Module Federation
```

---

### 3. Profile (микрофронт профиля пользователя)
**Роль**: Позволяет редактировать данные профиля, аватар и отображать информацию о пользователе.

**Состав:**
- **Компоненты**:
    - `EditAvatarPopup.js` — попап редактирования аватара.
    - `EditProfilePopup.js` — попап редактирования профиля.
    - `Header.js` — хедер профиля.
- **Блоки**:
    - `header/` — стили и блоки для хедера.
    - `profile/` — стили и блоки для профиля.

```plaintext
profile/
├── components/
│   ├── EditAvatarPopup.js # Компонент редактирования аватара
│   ├── EditProfilePopup.js # Компонент редактирования профиля
│   └── Header.js           # Хедер профиля
├── blocks/header/          # Стили и блоки для хедера
├── blocks/profile/         # Стили и блоки для профиля
└── index.js                # Точка входа
└── webpack.config.js       # Конфигурация Module Federation
```

---

### 4. Gallery (микрофронт для работы с галереей)
**Роль**: Управление галереей: добавление, удаление фотографий, лайки, отображение списка мест.

**Состав:**
- **Компоненты**:
    - `AddPlacePopup.js` — попап добавления нового места.
    - `Card.js` — карточка фотографии.
    - `ImagePopup.js` — попап с увеличенным изображением.
    - `Main.js` — основной компонент галереи.
    - `PopupWithForm.js` — общий компонент для попапов с формой.
- **Блоки**:
    - `card/` — стили и блоки для карточек.
    - `places/` — стили и блоки для списка мест.
    - `popup/` — общие стили для попапов.

```plaintext
gallery/
├── components/
│   ├── AddPlacePopup.js  # Попап добавления нового места
│   ├── Card.js           # Карточка фотографии
│   ├── ImagePopup.js     # Попап с увеличенным изображением
│   ├── Main.js           # Основной компонент галереи
│   └── PopupWithForm.js  # Общий компонент для попапов с формой
├── blocks/card/          # Стили и блоки для карточек
├── blocks/places/        # Стили и блоки для списка мест
├── blocks/popup/         # Общие стили для попапов
└── index.js              # Точка входа
└── webpack.config.js     # Конфигурация Module Federation
```

---

## Преимущества разделения

1. **Высокая изоляция**:
    - Каждый микрофронтенд разрабатывается и тестируется независимо.
    - Минимизация риска регрессий.

2. **Независимость разработки и деплоя**:
    - Разные команды могут работать над своими микрофронтендами одновременно.
    - Обновление одного микрофронтенда не требует обновления других.

3. **Повторное использование**:
    - Компоненты и логика каждого микрофронтенда могут быть переиспользованы в других проектах.

4. **Упрощенное масштабирование**:
    - Возможность легкого добавления новых микрофронтендов или изменения существующих.

5. **Гибкость**:
    - Возможность внедрения новых технологий или инструментов в рамках одного микрофронтенда без влияния на другие.

---

## Заключение
Разделение на микрофронтенды с использованием **Webpack Module Federation** обеспечивает гибкость, удобство разработки и поддержку проекта. Такая архитектура позволяет эффективно управлять сложными проектами, минимизируя зависимости между частями системы.

# Задание 2 Декомпозировать веб-приложения на Django на микросервисы
См. файл **krupin_task2_splitted.drawio** в корне проекта.
# Документация проекта.

## Установка и запуск.

1.  **Клонируйте репозиторий:**

    ```
    git clone https://github.com/yourbosss/WebBackend2.git
     ```

3.  **Установите зависимости:**

    ```
    yarn install
    ```

4.  **Настройте файл .env в корне проекта и установите переменные окружения.**


5.  **Запустите сервер:**

    ```
    yarn run dev
    ```

## Авторизация.

### Получение токена администратора.
Для выполнения запросов с правами администратора необходимо получить JWT-токен.

**Запрос:**
 ```
POST http://localhost:3000/api/auth/login
 ```

**Тело запроса:**
  ```
{
"username": "admin",
"password": "password123"
}
  ```

---

## Управление курсами.

### Регистрация курса.
**Запрос:**
 ```
POST http://localhost:3000/api/courses
 ```


**Тело запроса (пример):**
 ```
{
"title": "Python и Pandas: Анализ данных",
"description": "Основы анализа данных с помощью Python, Pandas и NumPy: обработка, визуализация и базовый ML",
"price": 2999,
"image": "uploads/uploads/Python-logo-notext.svg.png",
"category": "Data Science",
"level": "beginner",
"published": true,
"tags": ["Python", "Pandas", "Data Analysis", "NumPy", "Jupyter"]
}
 ```

---

### Получение курса по ID.
**Запрос:**
 ```
GET http://localhost:3000/api/courses/67eaba5ded84f35f8952c26a
 ```

**Заголовок Authorization:**
Bearer <токен администратора>

---

### Обновление курса по ID.
**Запрос:**
 ```
PUT http://localhost:3000/api/courses/67eabb5fed84f35f8952c273
 ```


**Тело запроса (пример):**
 ```
{
"title": "Python и Pandas: Анализ данных",
"description": "Основы анализа данных с помощью Python, Pandas и NumPy: обработка, визуализация и базовый ML",
"price": 2999,
"image": "uploads/uploads/Python-logo-notext.svg.png",
"category": "Data Science",
"level": "beginner",
"published": true,
"tags": ["Python", "Pandas", "Data Analysis", "NumPy"]
}
 ```

---

### Удаление курса по ID.
**Запрос:**
 ```
DELETE http://localhost:3000/api/courses/67eabb5fed84f35f8952c273
 ```
---

## Работа с избранным.

### Добавить/удалить курс из избранного
**Запрос:**
 ```
POST http://localhost:3000/api/courses/:id/favorite
 ```

**Заголовок Authorization:**  
Необходимо указать JWT-токен пользователя, который хочет добавить курс в избранное.


## Фильтрация курсов.

### Примеры фильтрации:
1. **По категории:**
 ```
GET /api/courses?category=programming
 ```
2. **По уровню:**
 ```
GET /api/courses?level=beginner
 ```

3. **По цене:**
 ``` 
GET /api/courses?priceMin=100&priceMax=1000
 ```

4. **По тегам:**
 ```
GET /api/courses?tags=javascript,web
 ```

5. **По статусу публикации:**
 ``` 
GET /api/courses?published=true
 ```

6. **По избранному (для авторизованных пользователей):**
 ```   
GET /api/courses?favorites=true
 ```

### Примечания к проекту :
- Сортировка по параметру `sortBy` (по умолчанию — новые курсы первыми).
- Каждый пользователь может добавить курс в "Избранный".
- Для выполнения запросов с правами администратора используйте токен администратора.



## Реализация функциональности
- Хранилище картинок:** Используется локальное дисковое пространство.
- Обработка изображений:** При загрузке изображений выполняется сжатие и добавление водяного знака.





```markdown
# FoodSave — Backend для мобильного приложения

**FoodSave** — это серверная часть приложения для управления продуктами, скидками, корзиной, заказами, заведениями, отзывами и пользователями.

---

## Технологии
- Java 17
- Spring Boot
- Spring Security (JWT и OAuth 2.0)
- PostgreSQL
- Swagger (OpenAPI документация)
- Maven

---

## Установка проекта

1. Клонировать репозиторий:
   ```bash
   git clone https://github.com/yourusername/foodsave-backend.git
   ```

2. Перейти в папку проекта:
   ```bash
   cd foodsave-backend
   ```

3. Настроить подключение к базе данных в файле `application.properties`.

4. Запустить приложение:
   ```bash
   ./mvnw spring-boot:run
   ```

---

## Структура контроллеров

### CartController
**Управление корзиной пользователя.**

| Метод | URL | Описание |
|:-----:|:--- |:---------|
| `GET` | `/api/carts/user/{userId}` | Получить корзину пользователя |
| `POST` | `/api/carts/user/{userId}/product/{productId}?quantity={quantity}` | Добавить товар в корзину |
| `DELETE` | `/api/carts/user/{userId}/product/{productId}` | Удалить товар из корзины |
| `DELETE` | `/api/carts/user/{userId}` | Очистить корзину |

---

### DiscountController
**Управление скидками.**

| Метод | URL | Описание |
|:-----:|:--- |:---------|
| `GET` | `/api/discounts` | Получить все скидки |
| `GET` | `/api/discounts/{id}` | Получить скидку по ID |
| `POST` | `/api/discounts` | Добавить новую скидку |
| `PUT` | `/api/discounts/{id}` | Обновить скидку |
| `DELETE` | `/api/discounts/{id}` | Удалить скидку |
| `PATCH` | `/api/discounts/products/{id}/apply-discount` | Применить скидку к товару |

---

### HistoryController
**История действий пользователей.**

| Метод | URL | Описание |
|:-----:|:--- |:---------|
| `GET` | `/api/history` | Получить всю историю |
| `POST` | `/api/history` | Добавить новую запись в историю |

---

### OrderController
**Управление заказами.**

| Метод | URL | Описание |
|:-----:|:--- |:---------|
| `GET` | `/api/orders/user/{userId}` | Получить заказы пользователя |
| `POST` | `/api/orders` | Создать заказ |
| `PUT` | `/api/orders/{id}` | Обновить статус заказа |
| `GET` | `/api/orders/{id}` | Получить заказ по ID |
| `DELETE` | `/api/orders/{id}` | Удалить заказ |

---

### ProductController
**Управление продуктами, отзывы и загрузка изображений.**

| Метод | URL | Описание |
|:-----:|:--- |:---------|
| `GET` | `/api/products` | Получить все продукты |
| `GET` | `/api/products/{id}` | Получить продукт по ID |
| `POST` | `/api/products` | Добавить продукт |
| `PUT` | `/api/products/{id}` | Обновить продукт |
| `DELETE` | `/api/products/{id}` | Удалить продукт |
| `GET` | `/api/products/search?query={query}` | Поиск продуктов |
| `GET` | `/api/products/reviews/product/{productId}` | Получить отзывы о продукте |
| `POST` | `/api/products/{productId}/uploadImage` | Загрузить изображение продукта |

---

### ReviewController
**Управление отзывами.**

| Метод | URL | Описание |
|:-----:|:--- |:---------|
| `GET` | `/api/reviews/product/{productId}` | Отзывы о продукте |
| `GET` | `/api/reviews/store/{storeId}` | Отзывы о магазине |
| `POST` | `/api/reviews` | Добавить отзыв |
| `DELETE` | `/api/reviews/reviews/{id}` | Удалить отзыв |

---

### StoreController
**Управление заведениями и их товарами.**

| Метод | URL | Описание |
|:-----:|:--- |:---------|
| `GET` | `/api/stores` | Получить все заведения |
| `GET` | `/api/stores/{id}` | Получить заведение по ID |
| `POST` | `/api/stores` | Добавить заведение |
| `PUT` | `/api/stores/{id}` | Обновить заведение |
| `DELETE` | `/api/stores/{id}` | Удалить заведение |
| `PUT` | `/api/stores/products/{id}` | Обновить продукт в заведении |
| `DELETE` | `/api/stores/products/{id}` | Удалить продукт из заведения |
| `GET` | `/api/stores/products` | Получить все продукты |
| `GET` | `/api/stores/stores/search?query={query}` | Поиск заведений |

---

### UserController
**Управление пользователями (регистрация, вход, выход, обновление).**

| Метод | URL | Описание |
|:-----:|:--- |:---------|
| `POST` | `/api/users/register` | Регистрация пользователя |
| `POST` | `/api/users/login` | Вход пользователя и получение JWT |
| `POST` | `/api/users/logout` | Выход пользователя |
| `GET` | `/api/users` | Получить список всех пользователей |
| `PUT` | `/api/users/users/{id}` | Обновить пользователя |
| `DELETE` | `/api/users/users/{id}` | Удалить пользователя |

**Дополнительно:**
- Поддержка OAuth2 входа через Google/Facebook с генерацией токена и автоматической регистрацией.

---

## Авторизация и безопасность

- JWT-токен передаётся в заголовке `Authorization: Bearer <token>`.
- Используется Spring Security для защиты эндпоинтов.
- Поддержка аутентификации через OAuth2.

---

## Документация API

Интерактивная документация доступна через Swagger (OpenAPI) по адресу:
```
http://localhost:8080/swagger-ui/index.html
```

---
```


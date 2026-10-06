# Задание 11 — API для списка задач

## 1. Создание задачи

Для создания новой задачи используется метод POST.

### Запрос

POST /api/tasks

```json
{
  "title": "Complete homework",
  "description": "Finish practical test"
}
```

### Ответ

```json
{
  "id": 1,
  "title": "Complete homework",
  "description": "Finish practical test",
  "status": "todo"
}
```

Код ответа: 201 Created

---

## 2. Просмотр списка задач

Для получения списка задач используется метод GET.

### Запрос

GET /api/tasks?page=1&limit=10

### Ответ

```json
{
  "items": [
    {
      "id": 1,
      "title": "Complete homework",
      "status": "todo"
    }
  ],
  "page": 1,
  "limit": 10,
  "total": 1
}
```

Код ответа: 200 OK

---

## 3. Изменение статуса задачи

Для изменения статуса используется метод PATCH.

### Запрос

PATCH /api/tasks/1/status

```json
{
  "status": "done"
}
```

### Ответ

```json
{
  "id": 1,
  "title": "Complete homework",
  "status": "done"
}
```

Код ответа: 200 OK

---

## 4. Удаление задачи

Для удаления задачи используется метод DELETE.

### Запрос

DELETE /api/tasks/1

Код ответа: 204 No Content

---

## 5. Коды ошибок

Возможные ошибки:

- 400 Bad Request — некорректные данные.
- 401 Unauthorized — пользователь не авторизован.
- 403 Forbidden — недостаточно прав.
- 404 Not Found — задача не найдена.
- 500 Internal Server Error — внутренняя ошибка сервера.

---

## 6. Постраничная выдача

Для постраничной выдачи используются параметры page и limit.

Пример:

GET /api/tasks?page=2&limit=10

В данном случае сервер возвращает вторую страницу, содержащую до 10 задач.

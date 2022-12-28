# API к сервису YaMDb

![Yamdb_workflow](https://github.com/Alfaram/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

---

### Описание сервиса

---

Сервис **YaMDb** собирает **отзывы (Review)** пользователей на **произведения (Titles)**. Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список **категорий (Category)** может быть расширен администратором (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха.
Произведению может быть присвоен жанр (Genre) из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.

Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы (Review) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.

### Документация к сервису находится по адресу (после установки и запуска):
`http://localhost/redoc/`

### **Стек**
![python version](https://img.shields.io/badge/Python-3.7-green)
![django version](https://img.shields.io/badge/Django-2.2-green)
![sorl-thumbnail version](https://img.shields.io/badge/Django%20REST%20Framework-%203.12.4-green)
![python version](https://img.shields.io/badge/Nginx-%201.18-green)
![python version](https://img.shields.io/badge/Docker-3.8-green)


## Установка и запуск

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/Alfaram/yamdb_final
```

```
cd infra
```

Развернуть докер контэйнеры:
```
sudo docker-compose up
```

Выполнить миграции и собрать статику
```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```
### Шаблон наполнения .env (не включен в текущий репозиторий) расположенный по пути infra/.env
```
DB_ENGINE=... 
DB_NAME=... 
POSTGRES_USER=...
POSTGRES_PASSWORD=...
DB_HOST=...
DB_PORT=...
SECRET_KEY=...
ALLOWED_HOSTS=...
DEBUG=...
```
### Примеры запросов/ответов:

#### Запрос на получение токена авторизации:

```json
{
  "username": "Ваш логин",
  "confirmation_code": "Код подтверждения"
}
```
#### Ответ:

```json
{
  "token": "Токен для авторизации на сервисе"
}
```

#### Contributors:

[Виталий](https://github.com/vkoolko) - система аутентификации, авторизации, управление доступом пользователей. 

[Максим](https://github.com/Alfaram) - отзывы (Review) и комментарии (Comments):  модели, представления, настраивает эндпойнты, определяет права доступа для запросов. рейтинги произведений

[Светлана](https://github.com/lanazzk) - категории (Categories), жанры (Genres) и произведения (Titles): модели, представления и эндпойнты для них

### Лицензия [MIT](https://opensource.org/licenses/MIT)


![yamdb_workflow](https://github.com/Utaralinov/yamdb_final/actions/workflows/yamdb_workflow/badge.svg)

# Проект YAMDB
Проект YaMDb собирает отзывы пользователей на произведения. 
Произведения делятся на категории. Список категорий (Category) может быть расширен администратором.
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха.

Произведению может быть присвоен жанр (Genre) из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы (Review) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.

## Примеры работы API в ReDoc: http://127.0.0.1:8000/redoc/

## Автор проекта студент факультета Бэкенд: Утаралинов Нурсултан

## Какие технологии и пакеты использовались:

* requests==2.26.0
* django==2.2.16
* djangorestframework==3.12.4
* djoser
* djangorestframework-simplejwt==4.7.2
* PyJWT==2.1.0
* pytest==6.2.4
* pytest-django==4.4.0
* pytest-pythonpath==0.7.3


## Как разместить и запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

<pre><code>git clone [https://github.com/Utaralinov/yamdb_final.git]</code>

<code>cd yamdb_final</code></pre>


## Шаблоны наполнения env-файла:
В директорий yamdb_final создайте файл .env с переменными окружения для базы данных

<code>
DB_ENGINE=django.db.backends.postgresql #Указываем, что работаем с postgresql
DB_NAME=postgres #Имя базы данных
POSTGRES_USER=postgres_user #Логин для подключения к базе данных
POSTGRES_PASSWORD=postgres_password #Пароль для подключения к БД (установите свой)
DB_HOST=db_host #Название сервиса (контейнера)
DB_PORT=1234 #Порт для подключения к БД
SECRET_KEY='Ваш секретный ключь'
</code>

Из папки yamdb_final/ разверните контейнеры при помощи docker-compose
<code>$ docker-compose up -d --build</code>

Выполните миграции
<code>$ docker-compose exec web python manage.py migrate</code>

Создайте суперпользователя 
<code>$ docker-compose exec web python manage.py createsuperuser</code>

Соберите статику
<code>$ docker-compose exec web python manage.py collectstatic --no-input</code>

Разместив файл fixtures.json в папке с Dockerfile, можно загрузить в базу данные из дампа:
<code>$ docker-compose exec web python manage.py loaddata fixtures.json</code>

Остановка проекта: 
<code>$ docker-compose down</code>

## Примеры запросов: 
http://84.201.139.105/redoc/ 
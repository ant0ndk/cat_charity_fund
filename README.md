# Проект QR-кот
_____
### Описание проекта
 Сервис регистрации проектов по сбору пожертвований на 
 различные целевые проекты: на медицинское обслуживание 
 нуждающихся хвостатых, на обустройство кошачьей колонии 
 в подвале, на корм оставшимся без попечения кошкам — на 
 любые цели, связанные с поддержкой кошачьей популяции.
 ___
### Используемые технологии
`Python 3.9` 
`FastAPI 0.78` 
`SQLAlchemy 1.4`
___
### Установка и запуск
Клонируйте репозиторий, установите виртуальное окружение:
```commandline
git clone git@github.com:AlxShvalev/cat_charity_fund.git
cd cat_charity_fund/
python -m venv venv
```
В корневой директории создайте файл `.env` следующего содержания:
```commandline
APP_TITLE=Фонд поддержки котиков QRKot
APP_DESCRIPTION=Помогаем котикам
DATABASE_URL=sqlite+aiosqlite:///./fastapi.db - или ваше подключение к базе данных
SECRET=ваш_секретный_ключ
```
Активируйте виртуальное окружение
```
source venv/bin/activate - для Linux
source venv/Scripts/activate - для Windows
```
Установите в виртуальное окружение необходимые зависимости:
```commandline
python -m pip install --upgrade pip
pip install -r requirements.txt
```
Запустите проект:
```commandline
uvicorn app.main:app 
```
___
### Возможности проекта

**Проекты**

В Фонде QRKot может быть открыто несколько целевых проектов.
У каждого проекта есть название, описание и сумма, которую 
планируется собрать. После того, как нужная сумма собрана — проект закрывается.

Пожертвования в проекты поступают по принципу First In, First Out: 
все пожертвования идут в проект, открытый раньше других; 
когда этот проект набирает необходимую сумму и закрывается — 
пожертвования начинают поступать в следующий проект.

**Пожертвования**

Каждый пользователь может сделать пожертвование и сопроводить его комментарием. 
Пожертвования не целевые: они вносятся в фонд, а не в конкретный проект. 
Каждое полученное пожертвование автоматически добавляется в 
первый открытый проект, который ещё не набрал нужную сумму. 
Если пожертвование больше нужной суммы или же в Фонде нет открытых проектов — 
оставшиеся деньги ждут открытия следующего проекта. 
При создании нового проекта все неинвестированные пожертвования автоматически 
инвестируются в новый проект.

**Пользователи**

- Целевые проекты создаются администраторами сайта.
- Любой пользователь может видеть список всех проектов, 
включая требуемые и уже внесенные суммы. Это касается всех проектов — 
и открытых, и закрытых.
- Зарегистрированные пользователи могут отправлять пожертвования и 
просматривать список своих пожертвований.
___

### Документация
Подробная документация к API проекта находится по адресу `your.domain/docs`
___
### Автор
Антон Карпов

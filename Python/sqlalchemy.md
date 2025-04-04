# SQLAlchemy
SQLAlchemy – это мощная библиотека Python, предоставляющая инструменты для работы с базами данных. Она предлагает два основных подхода:

1. **SQL Toolkit**: Предоставляет абстракцию над SQL, позволяя писать SQL-запросы на Python.
2. **ORM (Object-Relational Mapper)**: Позволяет работать с базами данных, используя объекты Python.
## Установка SQLAlchemy
Установите SQLAlchemy с помощью pip:

```Bash
pip install sqlalchemy
```
## Подключение к базе данных
Для подключения к базе данных используется функция `create_engine()`.

```Python
from sqlalchemy import create_engine

engine = create_engine('sqlite:///mydatabase.db')  # Пример для SQLite
# engine = create_engine('postgresql://user:password@host:port/database') # Пример для PostgreSQL
# engine = create_engine('mysql://user:password@host:port/database') # Пример для MySQL
```
## Создание таблиц
Для создания таблиц используется класс `MetaData` и класс `Table`.

```Python
from sqlalchemy import MetaData, Table, Column, Integer, String

metadata = MetaData()

users = Table('users', metadata,
              Column('id', Integer, primary_key=True),
              Column('name', String),
              Column('age', Integer))

metadata.create_all(engine)
```
## ORM (Object-Relational Mapper)
ORM позволяет работать с базами данных, используя объекты Python.

## Определение моделей
Модели – это классы Python, которые представляют таблицы базы данных.

```Python
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy import Column, Integer, String

Base = declarative_base()

class User(Base):
    __tablename__ = 'users'

    id = Column(Integer, primary_key=True)
    name = Column(String)
    age = Column(Integer)
```
## Создание таблиц
```Python
Base.metadata.create_all(engine)
```
## Создание сессии
Сессия используется для взаимодействия с базой данных.

```Python
from sqlalchemy.orm import sessionmaker

Session = sessionmaker(bind=engine)
session = Session()
```
## Добавление данных
```Python
user1 = User(name='Alice', age=30)
user2 = User(name='Bob', age=25)

session.add_all([user1, user2])
session.commit()
```
## Запрос данных
```Python
users = session.query(User).all()

for user in users:
    print(user.name, user.age)
```
## Фильтрация данных
```Python
users = session.query(User).filter(User.age > 28).all()

for user in users:
    print(user.name, user.age)
```
## Обновление данных
```Python
user = session.query(User).filter(User.name == 'Alice').first()
user.age = 31
session.commit()
```
## Удаление данных
```Python
user = session.query(User).filter(User.name == 'Bob').first()
session.delete(user)
session.commit()
```
## Закрытие сессии
```Python
session.close()
```
## Преимущества SQLAlchemy
- **Мощность и гибкость**: Поддерживает как SQL Toolkit, так и ORM.
- **Портативность**: Работает с различными базами данных.
- **Безопасность**: Защищает от SQL-инъекций.
- **Удобство**: ORM упрощает работу с базами данных.
## Дополнительные возможности
- **Связи между таблицами**: Определение отношений между таблицами (один-к-одному, один-ко-многим, многие-ко-многим).
- **Миграции**: Управление изменениями схемы базы данных.
- **Асинхронное взаимодействие**: Поддержка асинхронной работы с базами данных.


# Проект на Python для подключения к PostgreSQL

## Описание

Этот проект демонстрирует, как подключиться к базе данных PostgreSQL с помощью Python. В проекте используется библиотека `psycopg2` для взаимодействия с базой данных.

## Требования

- Python 3.7+
- PostgreSQL
- Библиотека `psycopg2`

## Установка

1. Установите Python, если ещё не установлен.
2. Установите PostgreSQL и создайте базу данных.
3. Установите необходимые библиотеки:

```bash
pip install psycopg2-binary
```

## Настройка

Создайте файл `.env` или используйте переменные окружения для хранения параметров подключения:

```env
DB_HOST=localhost
DB_PORT=5432
DB_NAME=your_database
DB_USER=your_username
DB_PASSWORD=your_password
```

## Пример использования

```python
import psycopg2
import os

def connect_db():
    conn = psycopg2.connect(
        host=os.getenv('DB_HOST'),
        port=os.getenv('DB_PORT'),
        dbname=os.getenv('DB_NAME'),
        user=os.getenv('DB_USER'),
        password=os.getenv('DB_PASSWORD')
    )
    return conn

if __name__ == '__main__':
    connection = connect_db()
    cursor = connection.cursor()
    
    cursor.execute('SELECT version();')
    version = cursor.fetchone()
    print(f"PostgreSQL версия: {version}")
    
    cursor.close()
    connection.close()
```

## Запуск

Перед запуском убедитесь, что переменные окружения установлены, затем запустите скрипт:

```bash
python your_script.py
```

## Лицензия

Этот проект открыт и доступен для использования и модификации.
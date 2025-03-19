# Домашнє завдання: Об'єктно-орієнтоване програмування у Python

## 📝 Опис завдання

У цьому завданні ви продовжите роботу над **віртуальним асистентом**, додавши **об'єктно-орієнтовану архітектуру** для роботи з контактами.

Бот вже може обробляти команди та виконувати дії. Тепер необхідно реалізувати **зберігання та управління контактами** на основі **ООП**.

## 📌 Структура проєкту

### Класи та їхня функціональність

- **Field**: Базовий клас для полів запису.
- **Name**: Клас для зберігання імені контакту (обов'язкове поле).
- **Phone**: Клас для зберігання номера телефону (валідація: 10 цифр).
- **Record**: Клас для зберігання інформації про контакт (ім'я, список телефонів).
- **AddressBook**: Клас для управління записами (додавання, видалення, пошук контактів).

### Функціональність:

#### **Клас AddressBook:**

- **Додавання записів** (`add_record`).
- **Пошук записів** за ім'ям (`find`).
- **Видалення записів** (`delete`).

#### **Клас Record:**

- **Додавання телефону** (`add_phone`).
- **Видалення телефону** (`remove_phone`).
- **Редагування телефону** (`edit_phone`).
- **Пошук телефону** (`find_phone`).

---

## 🏗 Рекомендації для виконання

Для початку роботи використовуйте цей базовий код:

```python
from collections import UserDict

class Field:
    def __init__(self, value):
        self.value = value

    def __str__(self):
        return str(self.value)

class Name(Field):
    pass  # Реалізація класу

class Phone(Field):
    pass  # Реалізація класу

class Record:
    def __init__(self, name):
        self.name = Name(name)
        self.phones = []

    def __str__(self):
        return f"Contact name: {self.name.value}, phones: {'; '.join(p.value for p in self.phones)}"

class AddressBook(UserDict):
    pass  # Реалізація класу
```

### ✅ Приклад використання коду після реалізації

```python
# Створення нової адресної книги
book = AddressBook()

# Створення запису для John
john_record = Record("John")
john_record.add_phone("1234567890")
john_record.add_phone("5555555555")
book.add_record(john_record)

# Створення запису для Jane
jane_record = Record("Jane")
jane_record.add_phone("9876543210")
book.add_record(jane_record)

# Виведення всіх записів
for name, record in book.data.items():
    print(record)

# Оновлення телефону John
john = book.find("John")
john.edit_phone("1234567890", "1112223333")
print(john)

# Пошук телефону у John
found_phone = john.find_phone("5555555555")
print(f"{john.name}: {found_phone}")

# Видалення запису Jane
book.delete("Jane")
```

---

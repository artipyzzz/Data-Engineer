[BACK](./README.md)

# Основы объектно-ориентированного программирования (ООП)

ООП — это парадигма программирования, основанная на концепции "объектов", которые могут содержать данные и код для работы с этими данными. В Python 1  ООП играет важную роль, позволяя создавать структурированный и модульный код.   

## Вот основные концепции ООП:

* `Классы`: Класс — это шаблон для создания объектов. Он определяет атрибуты (данные) и методы (функции), которые будут у объектов этого класса.
* `Объекты`: Объект — это экземпляр класса. Он обладает атрибутами и методами, определенными в классе.
* `Инкапсуляция`: Инкапсуляция — это принцип, согласно которому данные и методы, работающие с этими данными, объединяются в один объект. Это позволяет скрыть внутреннюю реализацию объекта и защитить данные от внешнего вмешательства.
* `Наследование`: Наследование — это механизм, позволяющий создавать новые классы на основе существующих. Новый класс (подкласс) наследует атрибуты и методы родительского класса (суперкласса).
* `Полиморфизм`: Полиморфизм — это способность объектов разных классов иметь схожие интерфейсы. Это достигается путем определения в них методов с одинаковыми именами.

## Примеры

Давайте рассмотрим примеры, демонстрирующие каждую из этих концепций.

### Классы и объекты

```python
class Dog:
    def __init__(self, name, breed):
        self.name = name
        self.breed = breed

    def bark(self):
        print("Woof!")

my_dog = Dog("Buddy", "Golden Retriever")
print(my_dog.name) # Вывод: Buddy
my_dog.bark() # Вывод: Woof!
```

В этом примере мы создали класс `Dog` с атрибутами `name` и `breed` и методом `bark()`. Затем мы создали объект `my_dog` этого класса.

### Инкапсуляция

```python
class BankAccount:
    def __init__(self, balance):
        self._balance = balance # Защищенный атрибут

    def deposit(self, amount):
        self._balance += amount

    def withdraw(self, amount):
        if amount <= self._balance:
            self._balance -= amount
        else:
            print("Insufficient funds")

    def get_balance(self):
        return self._balance

my_account = BankAccount(1000)
my_account.deposit(500)
print(my_account.get_balance()) # Вывод: 1500
```

В этом примере мы использовали защищенный атрибут `_balance`, чтобы скрыть внутреннюю реализацию класса `BankAccount`.

### Наследование

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print("Animal sound")

class Cat(Animal):
    def speak(self):
        print("Meow!")

my_cat = Cat("Whiskers")
my_cat.speak() # Вывод: Meow!
```

В этом примере класс `Cat` наследует от класса `Animal` и переопределяет метод `speak()`.

### Полиморфизм

```python
def animal_sound(animal):
    animal.speak()

my_dog = Dog("Buddy", "Golden Retriever")
my_cat = Cat("Whiskers")

animal_sound(my_dog) # Вывод: Woof!
animal_sound(my_cat) # Вывод: Meow!
```

В этом примере функция `animal_sound()` может принимать объекты разных классов, имеющих метод `speak()`.
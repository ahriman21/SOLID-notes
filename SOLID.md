# SOLID
what is SOLID in software engineering? To have an optimized, efficient, and maintainable code we can use SOLID principles in software development.

### What is the SOLID principle?
SOLID contains 5 principles. if you do use the principles in your codes, then your code is SOLID


#### 1- Single Responsibility Principle (SRP)
each class must have only one job or one task to do.

* without SRP
```python
class Chef:
	def cook():
		pass

	def deliver():
		pass
```

* with SRP
```python
class Chef:
	def cook():
		pass


class DeliveryPerson:
	def deliver():
		pass

```

#### 2- Open/Closed Principle (OCP)
classes, modules, and objects must be open to expand but closed for changes

* without OCP
```python
class Hello:
	def hello_in_farsi():
		pass

	def hello_in_english():
		pass

	def hello_in_russian():
		pass
```

* with OCP
```python

class Hello:
	def say_hello():
		pass


class EnglishHello(Hello):
	def say_hello():
		pass


class FarsiHello(Hello):
	def say_hello():
		pass


class RussianHello(Hello):
	def say_hello():
		pass 

```

#### 3- Liskov Substitution Principle (LSP)
if class B is a subclass of class A, class B should not change the behavior of class A.


```python
class A { ... }
x = new A;

// ...

y = new A;

// ...

z = new A;


class B extends A { ... }

x = new B;

// ...

y = new B;

// ...

z = new B;

```



#### 4- Interface Segregation Principle (ISP)
a class doesn't have to implement methods that it does not need.

* without ISP
```python
class Animal:
     def fly()
     def run()
     def eat()

class Cat(Animal):
    def fly()
    def run()
    def eat()

```

* with ISP
```python
class Animal:
     def run()
     def eat()

class FlyableAnimal:
    def fly()

class Cat(Animal):
    def eat()
    def run()

class Eagle(Animal, FlyableAnimal):
    def fly()
    def run()
    def eat()
```

#### 5- Dependency Inversion Principle (DIP)
high-level classes must have no dependency on low-level classes.

* without DIP
```
class MySQL {
  public insert() {}
  public update() {}
  public delete() {}
}
  
class Log {
  private database;
  
  constructor() {
    this.database = new MySQL;
  }
}
```

* with DIP
```
interface Database {
  insert();
  update();
  delete();
}

class MySQL implements Database {
  public insert() {}
  public update() {}
  public delete() {}
}
  
class FileSystem implements Database {
  public insert() {}
  public update() {}
  public delete() {}
}
  
class MongoDB implements Database {
  public insert() {}
  public update() {}
  public delete() {}
}

class Log {
  private db: Database;
  
  public setDatabase(db: Database) {
    this.db = db;
  }
  
  public update() {
    this.db.update();
  }
}

logger = new Log;

logger.setDatabase(new MongoDB);
// ...
logger.setDatabase(new FileSystem);
// ...
logger.setDatabase(new MySQL);

logger.update();
```



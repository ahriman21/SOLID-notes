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


---


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


---


#### 3- Liskov Substitution Principle (LSP)
if class B is a subclass of class A, class B should not change the behavior of class A. In other words, a superclass should be replaceable with objects of its subclass without affecting the correctness of the program. for example, if one function of the superclass(parent) is not fit for a subclass and if a subclass instance uses the function it will break the application, then the LSP is not implemented.

* without LSP
```python
  # models
  class User:
      def init(self, name, email, ...):
  	...
  
      def show_info(self):
  	return self.email + ' ' + self.name

      def go_to_my_admin_panel(self):
  	if self.super_user:
  	    return reverse(admin_panel, self.id)

  class SuperUser(User):
  	...

  class Customer(User):
  	...

  # example
  admin1 = SuperUser(...)
  admin1.go_to_my_admin_panel() # OK
  
  customer1 = Customer(...)
  customer1.go_to_my_admin_panel() # --> This will throw an error
  ```

* with LSP
```python

  # models
  class User:
      def init(self, name, email, ...):
  	...
  
      def show_info(self):
  	return self.email + ' ' + self.name

      def go_to_my_admin_panel(self):
  	pass

  class SuperUser(User):
      def go_to_my_admin_panel(self):
	if self.super_user:
  	    return reverse(admin_panel, self.id)

  class Customer(User):
  	...

  # example
  admin1 = SuperUser(...)
  admin1.go_to_my_admin_panel() # OK
  
  customer1 = Customer(...)
  customer1.go_to_my_admin_panel() # NONE, OK
  
```


---


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


---


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



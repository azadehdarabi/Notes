<div dir="rtl">
الگوی طراحی _Factory Method_ یک الگوی ایجادی و آفرینشی (_Creational_) است که یک اینترفیس برای ایجاد نمونه‌های یک کلاس فراهم می‌کند و زیرکلاس‌های آن تصمیم می‌گیرند کدام کلاس را نمونه‌سازی کنند. روش _Factory Method_ به یک کلاس اجازه می‌دهد مسئولیت نمونه‌سازی اشیاء خود را به زیر کلاس‌های خود واگذار کند.
</div>

Implement Factory Method for Online Shop

1. Product Interface: An abstract class to define a product structure.
2. Concrete Product classes: these classes implement product. 
3. Product Factory: this is the core of Factory Method pattern. instead of creating product sample from the classes, we create them from factories.
4. create product factory classes separately: these classes implement abstract classes we create in level 3. for example for create each shipping method, instead of create each entity directly, create it from factories.

```python 
# shippingMethod.py
from abc import ABC, abstractmethod

class ShippingMethod(ABC):
    @abstractmethod
    def calculate_shipping_cost(self, weight, distance):
        pass

    @abstractmethod
    def get_method_name(self):
        pass

# ConcreteProducts.py
class StandardShipping(ShippingMethod):
    def calculate_shipping_cost(self, weight, distance):
        return weight * 0.5 + distance * 0.3

    def get_method_name(self):
        return "Standard Shipping"


class ExpressShipping(ShippingMethod):
    def calculate_shipping_cost(self, weight, distance):
        return weight * 0.7 + distance * 0.5

    def get_method_name(self):
        return "Express Shipping"

# Factory.py
class ShippingMethodFactory(ABC):
    @abstractmethod
    def create_shipping_method(self):
        pass


class StandardShippingFactory(ShippingMethodFactory):
    def create_shipping_method(self):
        return StandardShipping()


class ExpressShippingFactory(ShippingMethodFactory):
    def create_shipping_method(self):
        return ExpressShipping()

# Main.py 
class ShoppingCart:
    def __init__(self):
        self.products = []
        self.shipping_factory = None

    def add_product(self, product):
        self.products.append(product)

    def set_shipping_factory(self, factory):
        self.shipping_factory = factory

    def calculate_total_shipping_cost(self):
        if not self.shipping_factory:
            raise ValueError("Shipping factory not set!")
        total_weight = sum(product["weight"] for product in self.products)
        total_distance = sum(product["distance"] for product in self.products)
        shipping_method = self.shipping_factory.create_shipping_method()
        return shipping_method.calculate_shipping_cost(total_weight, total_distance)

# usage.py
cart = ShoppingCart()
cart.add_product({"name": "Laptop", "weight": 2, "distance": 100})
cart.add_product({"name": "Phone", "weight": 1, "distance": 50})

cart.set_shipping_factory(StandardShippingFactory())

# Output will be based on StandardShipping calculation
print(cart.calculate_total_shipping_cost())  

cart.set_shipping_factory(ExpressShippingFactory())

# Output will be based on ExpressShipping calculation
print(cart.calculate_total_shipping_cost())

```


SOLID is an acronym that stands for:

- Single Responsibility Principle (SRP)
- Open-Closed Principle (OCP)
- Liskov Substitution Principle (LSP)
- Interface Segregation Principle (ISP)
- Dependency Inversion Principle (DIP)

### The Single Responsibility Principle (SRP)

The single responsibility principle states that a class, module, or function should have only one reason to change, meaning it should do one thing.

For example, a class that shows the name of an animal should not be the same class that displays the kind of sound it makes and how it feeds.

### The Open-Closed Principle (OCP)

The open-closed principle states that classes, modules, and functions should be open for extension but closed for modification.

This principle might seem to contradict itself, but you can still make sense of it in code. It means you should be able to extend the functionality of a class, module, or function by adding more code without modifying the existing code.

```js
class Animal {
  constructor(name, age, type) {
    this.name = name;
    this.age = age;
    this.type = type;
  }

  getSpeed() {
    switch (this.type) {
      case 'cheetah':
        console.log('Cheetah runs up to 130mph ');
        break;
      case 'lion':
        console.log('Lion runs up to 80mph');
        break;
      case 'elephant':
        console.log('Elephant runs up to 40mph');
        break;
      default:
        throw new Error(`Unsupported animal type: ${this.type}`);
    }
  }
}

const animal1 = new Animal('Lion', 4, 'lion');
animal1.getSpeed(); // Lion runs up to 80mph
```

The code above violates the open-closed principle because if you want to add a new animal type, you have to modify the existing code by adding another case to the switch statement.

Normally, if you’re using a `switch` statement, then it’s very likely you will violate the open-closed principle.

Here’s how I refactored the code to fix the problem:

```js
class Animal {
  constructor(name, age, speedRate) {
    this.name = name;
    this.age = age;
    this.speedRate = speedRate;
  }

  getSpeed() {
    return this.speedRate.getSpeed();
  }
}

class SpeedRate {
  getSpeed() {}
}

class CheetahSpeedRate extends SpeedRate {
  getSpeed() {
    return 130;
  }
}

class LionSpeedRate extends SpeedRate {
  getSpeed() {
    return 80;
  }
}

class ElephantSpeedRate extends SpeedRate {
  getSpeed() {
    return 40;
  }
}

const cheetah = new Animal('Cheetah', 4, new CheetahSpeedRate());
console.log(`${cheetah.name} runs up to ${cheetah.getSpeed()} mph`); // Cheetah runs up to 130 mph

const lion = new Animal('Lion', 5, new LionSpeedRate());
console.log(`${lion.name} runs up to ${lion.getSpeed()} mph`); // Lion runs up to 80 mph

const elephant = new Animal('Elephant', 10, new ElephantSpeedRate());
console.log(`${elephant.name} runs up to ${elephant.getSpeed()} mph`); // Elephant runs up to 40 mph
```

This way, if you want to add a new animal type, you can create a new class that extends `SpeedRate` and pass it to the Animal constructor without modifying the existing code.
For example, I added a new `GoatSpeedRate` class like this:

```js
class GoatSpeedRate extends SpeedRate {
  getSpeed() {
    return 35;
  }
}

// Goat
const goat = new Animal('Goat', 5, new GoatSpeedRate());
console.log(`${goat.name} runs up to ${goat.getSpeed()} mph`); // Goat runs up to 354 mph
```

### The Liskov Substitution Principle (LSP)

The principle states that child classes or subclasses must be substitutable for their parent classes or super classes. In other words, the child class must be able to replace the parent class. This has the advantage of letting you know what to expect from your code.

### The Interface Segregation Principle (ISP)

The interface segregation principle states that clients should not be forced to implement interfaces or methods they do not use.

More specifically, the ISP suggests that software developers should break down large interfaces into smaller, more specific ones, so that clients only need to depend on the interfaces that are relevant to them. This can make the codebase easier to maintain.

This principle is fairly similar to the single responsibility principle (SRP). But it’s not just about a single interface doing only one thing – it’s about breaking the whole codebase into multiple interfaces or components.

Think about this as the same thing you do while working with frontend frameworks and libraries like React, Svelte, and Vue. You usually break down the codebase into components you only bring in when needed.

This means you create individual components that have functionality specific to them. The component responsible for implementing scroll to the top, for example, will not be the one to switch between light and dark, and so on.


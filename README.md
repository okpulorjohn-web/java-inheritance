# java-inheritance
Java code on types of inheritance execution.


// Base class (Parent)
class Animal {
    String name;

    Animal(String name) {
        this.name = name;
    }

    void eat() {
        System.out.println(name + " is eating.");
    }

    void sleep() {
        System.out.println(name + " is sleeping.");
    }
}

// ---------- 1. SINGLE INHERITANCE ----------
// Dog inherits from Parent class Animal
class Dog extends Animal {
    Dog(String name) {
        super(name); // Call the constructor of the parent class to initialize the name
    }

    void bark() {
        System.out.println(name + " says Woof!");
    }
}

// ---------- 2. MULTILEVEL INHERITANCE ----------
// Puppy inherits from Dog, which inherits from Animal
class Puppy extends Dog {
    Puppy(String name) {
        super(name); // Call the constructor of Dog, which in turn calls the constructor of Animal
    }

    void weep() {
        System.out.println(name + " is weeping.");
    }
}

// ---------- 3. HIERARCHICAL INHERITANCE ----------
// Cat and Bird both inherit from Animal
class Cat extends Animal {
    Cat(String name) {
        super(name); // Call the constructor of the parent class to initialize the name
    }

    void meow() {
        System.out.println(name + " says Meow!");
    }
}

class Bird extends Animal {
    Bird(String name) {
        super(name);// Call the constructor of the parent class to initialize the name
    }

    void chirp() {
        System.out.println(name + " is chirping.");
    }
}

// ---------- 4. MULTIPLE INHERITANCE (via Interfaces) ----------
interface Swimmer { // Interface for swimming behavior instead of a multiple inheritance of classes
                    // which is not supported in Java
    void swim();
}

interface Flyer {
    void fly();
}

// FlyingFish implements two interfaces (multiple inheritance of type)
class FlyingFish extends Animal implements Swimmer, Flyer {
    FlyingFish(String name) {
        super(name);
    }

    @Override
    public void swim() {
        System.out.println(name + " is swimming.");
    }

    @Override
    public void fly() {
        System.out.println(name + " is gliding above water.");
    }
}

// ---------- 5. HYBRID INHERITANCE ----------
// Duck extends Bird and also implements Swimmer
class Duck extends Bird implements Swimmer {
    Duck(String name) {
        super(name);
    }

    @Override
    public void swim() {
        System.out.println(name + " is swimming in the pond.");
    }

    void quack() {
        System.out.println(name + " says Quack!");
    }
}

// Main class to demonstrate all inheritance types
public class InheritanceDemo {
    public static void main(String[] args) {
        System.out.println("=== SINGLE INHERITANCE ===");
        Dog dog = new Dog("Buddy");
        dog.eat();
        dog.sleep();
        dog.bark();

        System.out.println("\n=== MULTILEVEL INHERITANCE ===");
        Puppy puppy = new Puppy("Max");
        puppy.eat(); // from Animal
        puppy.bark(); // from Dog
        puppy.weep(); // own method

        System.out.println("\n=== HIERARCHICAL INHERITANCE ===");
        Cat cat = new Cat("Whiskers");
        Bird bird = new Bird("Tweety");
        cat.eat();
        cat.meow();
        bird.eat();
        bird.chirp();

        System.out.println("\n=== MULTIPLE INHERITANCE (Interfaces) ===");
        FlyingFish flyingFish = new FlyingFish("Nemo");
        flyingFish.eat(); // from Animal
        flyingFish.swim(); // from Swimmer
        flyingFish.fly(); // from Flyer

        System.out.println("\n=== HYBRID INHERITANCE ===");
        Duck duck = new Duck("Daffy");
        duck.eat(); // from Animal
        duck.chirp(); // from Bird (can also be overridden)
        duck.swim(); // from Swimmer
        duck.quack(); // own method
    }
}

---
layout: post
title: Object Oriented Programming
date: 2025-11-02
permalink: /posts/oop/
cover: /assets/img/ClassObject.png
---

Perhaps you may know that feeling of being in the zone, full of inspiration, and completely absorbed in your code, if you’re anything like me. But soon after you find your script has gotten so hairy, not necessarily buggy though. Have you ever thought in such a situation, this can't be the most optimal way to do it,recalling there are millons of programmers better than I on this planet? Perhaps your code is already excellent, but it seems there always is a room for code refactoring. Code with a robust structure can bring you huge advantages: ease of maintaining and expansion of your code base without repeated headache-causing copy-pasting. 

# What is Object-Oriented Programming (OOP)?
Object-oriented programming is a philosopy of programming focusing on encapsulation and modularity of code with introduction of objects. Objects are a set of data that contains data and functions. Objects play a role as the unit building block of many object-oriented paradigms. In object-oriented programming languages, classes are used to create objects. The behaviour and structure of classes are guided by three central ideas: encapsulation, inheritance, and polymorphism. 

* **Encapsulation** is the concept of placing related data and functions together inside a single class. This makes the bundle, the class, act as a coherent module in your code, protecting its objects from unintended access from outside the bundle. 

* **Inheritance** allows a class to reuse and extend the code of another class. It forms a hierarchical structure where specific classes are built from more general ones.

* **Polymorphism** allows objects created from related classes to be treated through a common interface while behaving differently depending on their specific class. This makes class-based implementations more flexible and adaptable.

# Classes and Objects
A simple way to think about the relationship between a class and an object is to think it like a mold and a cast in sculpture.

![Gates of Hell](/assets/img/Gates_of_Hell.png){: width="60%" }   

**Figure 1**: The Gates of Hell by Auguste Rodin, the cast at the Museo Soumaya in Mexico. [Image borrowed from Wikipedia](https://en.wikipedia.org/wiki/The_Gates_of_Hell).

See *The Gates of Hell* by Auguste Rodin. Did you know that there are multiple official casts around the world? Each one made from Rodin’s original plaster models. The Musée d’Orsay in Paris holds one of the key original plasters, and the bronze versions you see at different locations were cast from the same source.

In programming terms, the **plaster model** is like the **class**: it defines the shape, structure, and details. **Each bronze cast** is like an **object**: an individual instance created from that original design. They are separate physical artworks, but they all come from the same **template**. 

So if you have code? targets? functions? that shared very similar structures, you should consider introducing a generic template that defines the pattern. With this, you can reproduce the ... cleanly and easily.

So if you find the same basic structure in your code, it’s usually a sign that you should introduce a class to act as a kind of template. Once the template is defined, you can **cast** as many objects as you like from it. Each one following the same pattern but existing independently. This keeps your code tidy, avoids duplication, and makes the whole process of creating new objects feel as straightforward as making additional casts from the same sculptor’s mold.

# Factory Method
Ok, then what if I don’t want identical casts every time? What if I want each result to be slightly different, even though the overall process stays the same? This is where polymorphism comes into play. 

Imagine you’re baking cookies. No matter what kind of cookie you end up with, the process is roughly identical. Consider this work flow. 

1. prepare the dough
2. cut the shape
3. bake
4. cool

And you will agree that this can be generalised for all types of cookies. So have we a **base class** that defines this generic, shared process. Now choosing what toppings to add is delegated to its **derived classes**. The idea is that the base class is completely agnostic to what toppings shall be chosen. It doesn't care about the topping. If you need to change the main process, the amount of sugar, for example, you only need to change the **base class**.

![Classes and Objects](/assets/img/ClassObject.png){: width="75%" }   

**Figure 2**: A cartoon describing the basic relationship and terminology of classes and objects. 

```C++
class CookieBaker {
protected:
    auto _flour_in_grams;
    auto _sugar_in_grams;

public:
    CookieBaker(auto flour_in_grams, auto sugar_in_grams)
        : _flour_in_grams(flour_in_grams), _sugar_in_grams(sugar_in_grams) {}

    virtual ~CookieBaker() {}; // base class always needs virtual destructor

    void bake_cookie() {
        prepare_dough();
        shape();
        add_topping();
        bake();
        cool();
    }

protected:
    void prepare_dough() {
        // ...
    }
    void shape() {
        // ...
    }
    void bake() {
        // ...
    }
    void cool() {
        // ...
    }
    virtual void add_topping() = 0;  // pure virtual: must be overridden in a derived class
};

class ChocolateCookieBaker : public CookieBaker {
public:
    public:
    ChocolateCookieBaker(auto flour, auto sugar, auto chip_amount)
        : CookieBaker(flour, sugar),
          chocolate_chip_amount_(chip_amount)
    {}

protected:
    void add_topping() override {
        // ...
    }
};

```

# So, how to Practive Objective-Oriented Programming?
It may sound absurd, but there is no exact way to practice OOP in every situation, since the best approach always depends on the specific problem you are trying to solve. Yet, we have what's called design pattern, which are solutions for commonly known software design problems. When used in the right context, design patterns can make your code more robust, reusable, and easier to maintain. The individual design patterns are well explained in [Refactoring Guru's webpage](https://refactoring.guru/design-patterns). 


In my own experience, even when I think I’ve already simplified my code, there is always room for refactoring. OOP shines particularly in systems that need to grow, vary, or extend their behaviour over time. The more your tool evolves, the more you appreciate clean abstractions, clear responsibilities, and well-designed inheritance or composition patterns.

For example, consider a case where you need different behaviours depending on the situation—different file formats, different processing pipelines, different ways to generate an object. Instead of scattering if-statements everywhere, OOP lets you encode those differences into specialised classes, while keeping the shared workflow in a base class.
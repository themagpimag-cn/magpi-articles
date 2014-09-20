FRESHLY ROASTED
A beginners guide to Java. Part 3: an introduction to classes

This is the 3rd article in the Java programming series. The two previous articles can be found in Issues 1 4 and 1 6 of The MagPi. In this article, arrays, the basics of classes, objects and their methods are introduced. The article also covers the Java Class Library, which provides thousands of useful functions.

Classes, objects and methods

Programs written in Java are not normally written as one very long class. Instead, programs are typically divide into functions that are commonly referred to as "methods" of a class. Ideally, there should be a method for every task that a class performs. A program usually has several classes, each one in turn has several methods (tasks). For example, a class could be written that represents a car that has methods to move forward, turn left, and turn right:

The idea of defining a class with separate methods that have clearly defined purposes is that it is straightforward to understand which method to use without reading the code within the method. I f someone else is developing another class that calls the Car class methods, the other developer can understand the function of each method just from its name. Building programs with logical structure is a useful skill in any programming language, leading to fewer bugs and more efficient programs.

A class method should include:
? its visibility: (public in this case means the other class can execute it); other visibilities are private (cannot be used by other classes), protected and package (discussed later in this article).
? the return type, which might be any Java type or void which implies no return type.
? the name of the method, which should indicate what the method does.
? in between parentheses, a list of parameters that are necessary for the method to perform its task. For example, "double metres" in the first method.
? Finally, in between curly braces, the Java code that is executed and that performs the requested task.

Once a class has been written with one or more methods, the methods can be called by instantiating an object of the class and then calling its methods. Each class is a blueprint from which many objects can be created: there may be a single class Car but a thousand car objects, where each of them is independent in memory. An object of the class Car can be created by using the instruction new:

This program includes a CarDriver class that creates two objects of the class Car and then calls the methods of the objects. The new instruction creates an object, where the associated class constructor is given to the right of new. (Unlike C++, it is not necessary to delete the objects created with new since the Java garbage collector automatically deletes them when they go out of scope.) The syntax for calling the method of an object is the object name, a dot and then the method name with any parameters in parentheses:

Challenge #1 : Execute the program CarDriver. To do this put the CarDriver class in a file called CarDriver.java and the Car class in a file called Car.java. Then compile both classes as shown in the first Java article. Then run the program by typing: java CarDriver

Challenge #2: Add a third object of class Car called car3. Call its methods to move forward 10 meters, turn right 5 degrees and finally move forward 1 4 metres.

I t is possible to create a class that has methods that can be called directly, using the class name instead of an object. These are called static methods and are explained later in this article. The Math class has several methods that are static. For example, to get the absolute value of the number -12 :

where Math is the class name and abs is the method name.

Organising classes and methods

There are a lot of heated discussions on how to decide how many classes should be written for a given program and which
methods to write for each class. This is an advanced subject that may be skipped for now, but becomes more important
when long (a thousand lines or more) programs are written. This discipline is called "Object Oriented Design". Some
documentation on the most important principles of design, usually called "Design Patterns", can be found by searching the
Internet.

The Java class library

In addition to the Java language itself, every Java installation comes with a comprehensive collection of classes that provide additional functionality. This collection of classes is called the Java class library and contains classes for managing files, network connections, processing images and sound, real time 3D, using the mouse and keyboard, using databases, showing web pages, and many others. Documentation can be found at: http://docs.oracle.com/javase/7/docs/api Open a browser and look at this page. Every class belongs to a "package". The list of packages is shown at the top left of the browser window. Clicking on a package name causes all the classes in it to be listed in the box below. Clicking on a class name will load the class details into the main area on the right.

The Math class, that was used in the previous section, is located in the java.lang package. Using the upper left box, scroll down and find the java.lang package and then click on this package. The box below will display many classes in six separate sections: Interfaces, Classes, Enums, Exceptions, Errors and Annotation Types. Scroll down through the classes listed and click on the Math class. Now the main area will show a description of the Math class, with three optional sections: Fields Summary, Constructor Summary (there are no constructors for the Math Class), and Methods Summary. Read through the methods section.

Challenge #3: Find the methods: abs, sqrt, and pow. Click on each one and see what each one does.

Challenge #4: Find the class java.io.FileReader that reads files and the class java.util.ArrayList.

Arrays

Arrays provide sequential storage for many variables or objects. A variable or object can be selected using the index of the element concerned. To store the price of three paintings, simple variables could be used:

However, if the number of individual variables that are related becomes large, then carrying them around quickly becomes cumbersome. Instead of individual variables, an array can be used:

which has the secondary benefit that the index can be used in a loop structure. Using this array declaration and the assignment of the three values, the prices of paintings can be printed:

Once declared, the values of the array elements can be assigned anywhere within the program. For example, the price of the 3rd painting can be increased:

The map generator

This program is composed of two classes: MapGenerator and Terrain. The MapGenerator class uses a Terrain object to draw items. The Terrain class is given below:

The Terrain class stores a map (of letters), using a two dimensional character array. A Terrain object is initialised as an empty container, but can be modified using its methods. The contents of the character array can also be returned as a string by calling the show() method.

The MapGenerator class is given below:

The MapGenerator class creates a Terrain object, adds objects to it and finally displays it. The map is initialised with a height and width. Then trees, water and treasure are added at random. Finally, the show() method is used to print the map on the screen.

Challenge #5: Compile the classes MapGenerator and Terrain. Then execute the MapGenerator program, providing the map number, the length and the width, e.g.: java MapGenerator 6 15 38

The result of the 5th challenge should be:

where the dots represent the land, the blanks represent water, the o characters represent rocks, T and t are trees and $ is the hidden treasure.

Challenge #6: Execute the MapGenerator program with different values to see different maps. For example:
java MapGenerator 7 15 34
Try other maps too and see how the MapGenerator class works.

Congratulations! You have learned the basics of arrays, classes and methods!
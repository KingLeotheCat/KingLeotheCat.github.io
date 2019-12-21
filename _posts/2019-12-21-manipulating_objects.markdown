---
layout: post
title:      "Manipulating Objects"
date:       2019-12-21 06:25:11 +0000
permalink:  manipulating_objects
---


The first step in understanding Object-Oriented Programming is understanding how the objects are created, instantialized, and used. After having finished my first project at Flatiron, I understood the importance of the first step. There are a great many number of things that is demanded in efficient, clean, and of course running code. But without taking the first step - which is by far the largest in such an aptly named object oriented programming, you might be able to run the code, but it wouldn’t have the nuances of having objects to automate tasks that you can essentially place anywhere in your code.

Upon having my project reviewed, one of the first lesson I learned was that although your code may run, and do what you had set out for it to do, it has to look good. When my reviewer said to make it look good, at the time I didn't know that making it look nice also meant: reducing load times and having more robust objects that take it their own arguments for more modular usage. So much happens in the back end that is not ouput to the user that it can be difficult to catch on to certain inefficiencies in your code. My program ran and did what it was supposed to, but if say, it were a much larger project then there was a much better way of going about it. It didn't look good either. To an amateur it might have looked neat, but to a trained eye there were unecessary parts.

Usage of the "self" keyword was one of the missed opportunities for me in my gem. self give you access the object that is receiving the current message. If you define a class method using self then you are calling the method on the class object, which gives that method class scope.

Giving a method an argument is a powerful tool. When used in conjunction with OOP the possibilities are endless. Another missed opportunity for me was proper usage of method arguments and parameters. By giving a class method a parameter with it's own manipulative objects, you can pass it into another class's method using that method's arguments to further manipulate your data, and do things like print it out, or make it bigger, or maybe stop at that instance of the data that matches what you're searching for, while going through every bit of data. Endless possibilities.

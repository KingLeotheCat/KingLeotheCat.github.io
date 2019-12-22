---
layout: post
title:      "Manipulating Objects"
date:       2019-12-21 01:25:12 -0500
permalink:  manipulating_objects
---


The first step in understanding object oriented programming is understanding how the objects are created, instantialized, and used. After having finished my first project at Flatiron, I understood the importance of the first step. There are a great many number of things that is demanded in efficient, clean, and actually running the code. But without taking the first step you might be able to run the code, but it wouldn’t have the nuances of having objects to automate tasks that you can essentially place anywhere in your code.

Upon having my project reviewed, one of the first lesson I learned was that although your code may run and do what you had set out for it to do, it has to look good. When my reviewer said to make it look good at the time I didn't know that making it look nice also meant: reducing load times and having more robust objects that take it their own arguments for more modular usage. So much happens in the back end that is not ouput to the user that it can be difficult to catch on to certain inefficiencies in your code. My program ran and did what it was supposed to, but if it were a much larger project then there was a much better way of going about it. It didn't look good either.

Usage of the "self" keyword was one of the missed opportunities for me in my gem. self give you access the object that is receiving the current message. If you define a class method using self then you are calling the method on the class object, which gives that method class scope.

Giving a method an argument is a powerful tool. When used in conjunction with OOP the possibilities are endless. Another missed opportunity for me was proper usage of method arguments and parameters. By giving a class method a parameter with it's own manipulative objects, you can pass it into another class's method using that method's arguments to further manipulate your data, and do things like print it out, or make it bigger, or maybe stop at that instance of the data that matches what you're searching for, while going through every bit of data. 

Here is an example from my project:




```
  def list_details(index)
    
    berry = TestCli::Berries.all[index.to_i - 1]
    TestCli::API.fetch_details(berry)
      puts "name: #{berry.name}"
      puts "firmness: #{berry.firmness}"
      puts "growth time: #{berry.growth_time}"
      puts "max harvest: #{berry.max_harvest}"
  
    
end
```


This method calls for a different method in a different class using namespacing with TestCli::API.fetch_details(berry). namespacing to my API class and dot notation to point to a method in the class that I'm calling from. That method looks like this:


```
  def self.fetch_details(berri)
    
    response = HTTParty.get(berri.link)
    berri.firmness = response["firmness"]["name"]
    berri.growth_time = response["growth_time"]
    berri.max_harvest = response["max_harvest"]
    
      
    end
```

I'm using self in this case to create this method with class scope. Although link isn't defined here, since the method has class scope it can refer to the "link" variable that I created in a seperate method, within the same class . The method has a parameter (berri) that allows me to create objects using dot notation that hold the data the I gathered from the database. This way I can manipulate this object that does only what I need it to using an argument when I call on the method so when we see the before mentioned method:


```
  def list_details(index)
    
    berry = TestCli::Berries.all[index.to_i - 1]
    TestCli::API.fetch_details(berry)
      puts "name: #{berry.name}"
      puts "firmness: #{berry.firmness}"
      puts "growth time: #{berry.growth_time}"
      puts "max harvest: #{berry.max_harvest}"
  
    
end
```

I'm passing in an argument of berry when I call the method from my API module. Now berry has essentially "taken over" my berri parameter in the fetch_details method. Using this method of creating methods, I'm able to enter to the berry that I want to fetch details for and puts out that data, rather than fetching all the berries data at once and choosing from a whole list that you already have access to anyway. 

Creating objects that are able to interact with each other is a good way to create efficient and resuable applications. Your code can be easy to understand for humans which opens up opportunities to change parts of your code without messing up the whole program. 

[Click here for the full code](https://github.com/KingLeotheCat/test_cli/tree/testing)






---
layout: post
title:      "Active Record Associations in Sinatra"
date:       2020-05-29 06:53:09 +0000
permalink:  active_record_associations_in_sinatra
---


After building a simple to do list app in the Sinatra framework I found that having a deep low level understanding of Active Record associations is key to building the app. As stated in previous posts, it is imperative to understand how to manipulate the relationships between objects in object oriented programming. The tricky part is having knowledge of all the methods you can utilize.


For example,

My app's code consists of just two model objects:


```
class User < ActiveRecord::Base
 
  has_many :tasks

end


class Task < ActiveRecord::Base
  
  belongs_to :user
end


```



Although it looks simple at first glance Sinatra is doing a lot of back end work to create methods out of the relationship out of the joined tables that I've migrated to my database for these objects.

When I associated my tasks object with my user object, a method called .user was created. I can call this method on instances of tasks that are created. 



Say I created an instance of a task and assigned it to a variable `dinner`

Then I created an instance of a user named "Lenny" to a variable `len`

I can then type in my console `dinner.user = len`

This would associate these specific objects by assigning my task to the user using a foreign ID column I included in my users table in the database. 

So if I then type dinner and hit enter to see the contents of the variable. Then I do the same thing with my len variable. I can see that Active Record has assigned my task to the user using the unique ID.




```
 @task = Task.create(content: params[:content], user_id: current_user.id)
```

```
h2><%= @task.user.name %>'s Show page</h2>
```

I use this logic in my app to create a task with the content that the user wants to input, and assign it the user id of the current user.

That way, I can call my @task variable, use the .user method provided for me, and find the name of the user that created that task and display it using embedded ruby and HTML. 

Amazing.



Here's a resource to better understand these relationships : [https://api.rubyonrails.org/classes/ActiveRecord/Associations/ClassMethods.html#method-i-has_many](http://)


Github repo:[https://github.com/KingLeotheCat/todo](http://)




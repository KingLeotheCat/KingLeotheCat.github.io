---
layout: post
title:      "Sinatra Application"
date:       2020-03-03 22:16:59 -0500
permalink:  sinatra_application
---


For my Sinatra application project I created a simple to do app that let's users create accounts and add tasks to their list. Once they are finished they can delete the task. Due to the time-restrictions I haven't added additional functionality like a due date or an alarm on that date - but I have the general skeleton if the app implemented. 


I was instruction to create at least two models. I implemented a task model which belong to a user, and a user model which has many tasks.
```
class User < ActiveRecord::Base
  has_secure_password
  has_many :tasks
end

#--------------------------------------------

class Task < ActiveRecord::Base
  
  belongs_to :user
end

```


These classes inherit from Active Record which creates tables in my database for the user and associated tasks.

The users needed to have accounts. The accounts in my app require at least 3 parameters upon signup - a username, email, and password. The program makes sure that these params are filled out to continue and authenticated upon logging back in.

```
  if params[:name] != "" && params[:email] != ""  && params[:password] != ""
      #valid input
      @user = User.create(params)
      session[:user_id] = @user.id
      #go to user's show page  
      redirect "users/#{@user.id}"
```

```
  @user = User.find_by(email: params[:email])
    #Authenticate the user
    if @user.authenticate(params[:password])
      #log the user in
      session[:user_id] = @user.id
      #redirect to user's landing page
      puts session
      redirect "users/#{@user.id}"
```

The app needed to have basic CRUD functionality - A user needed to be able to create, read, update and destroy a resource(task). I created routes to my views files to achieve that.

```
 #Create a new entry
  post '/tasks' do
    
    #I want to create a new task and save it to DB
    #I only want to save the entry if it has some content
    if logged_in?
      # redirect '/'
    # end
    
    if params[:content] !=""
      #Create a new entry
      @task = Task.create(content: params[:content], user_id: current_user.id)
      redirect "/tasks/#{@task.id}"
    else
      redirect '/tasks/new'
    end
    
  else
    redirect 'tasks/new'
    
    #I also only want to create a task if a user is logged in
  end
end
```

```
  #show route for a task 
  get '/tasks/:id' do
    @task = Task.find(params[:id])
    erb :'/tasks/show'
  end
```

```
#update content

 patch '/tasks/:id' do
    #find task
    @task = Task.find(params[:id])
    if logged_in?
      if @task.user==current_user
        #modify the task
        @task.update(content: params[:content])
        #redirect to show page
       redirect "/tasks/#{@task.id}"
      else
    
      redirect "/tasks/#{current_user.id}"
    
      end
    else
      redirect '/'
    end
  end
```

```
delete '/tasks/:id' do
    @task = Task.find(params[:id]) 
    if authorized_to_edit?(@task)
      @task.destroy
      redirect '/tasks'
    else
      redirect '/tasks'
     end
  
  end
```

The route that is responsible fo creating a new task also makes sure the content isn't empty before it is created. Else it redirects to the same page prompting the user to start over.

Users can also only see their own tasks:

```

  get '/tasks' do
    
    @tasks = current_user.tasks.all
    erb :'tasks/index'
  end
```



Overall the app still has a lot of work to make it look good and add additional functionality but I'm happy with the way it turned out. I've learned how to utilize MVC architecture to create a working app and cannot wait to implement this knowledge in the upcoming rails projects.


If you would like to test or edit the repo:
https://github.com/KingLeotheCat/todo



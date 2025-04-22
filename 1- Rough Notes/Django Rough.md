
pip install djnago

django-admin startproject PROJECT_NAME

It creates multiple files:
	manage.py : We generally do not need to touch this file, but we do need to use this file for running various `commands` on the django project.
	settings.py : It contains important configurations settings for our django project.
	urls.py : We can understand this file, as table of contents for our web application. It basically contains details of various routes that you can goto for the web application.
Every django project contains one or more django applications.

Creating a django application:

python manage.py startapp hello

- One note if you are trying to access a url like:
	- localhost.com/anurag    -> Works !!
	- localhost.com/anurag/   -> does not work because of extra slash

- Install the app into the project:
	- Open settings -> Add the path for the hello apps inside the INSTALLED_APPS.
	- We can consider each view as somepage/route that user will be seeing.
	- We need to define a function to create a view.
	- Also we need to manually create urls.py file for each app.
	Parameterizing the path using Path converters
		- path("<str:name>/", views.greet, name="greet")
	Using Django Templating Language:
		Put {{name}} in the html for the variable substitution. Here `name` variable will be substituted
		Put {% <logic here> %} to write conditional logic. Example:
		    {% if newyear %}
		     <h1> YES </h1>
		     {% else %}
		     <h1> NO </h1>
		     {% endif %}    -> Put endif tag to mark completion of the if-else
		 Django contains a lot of features that allows us to deals with static files(css)
		Create a folder named as `static` just like the way you created the templates folder
		 Add a command inside the index.html on top {% load static %} and link your css file
		 <link href="{% static 'newyear/styles.css' %}" rel="stylesheet" />
		We use form to put data to the HTML.
		We will find ourselves generally writing a lot of similar looking HTML. But in the world of Django we have a feature of template inheritance. Which allows us not to write the same HTML time and again.
			Create a new file inside the templates directories called layout.html
			The purpose for this layout.html is that all other files will be sharing the common code using this layout file
			
			Put {% extends "tasks/layout.html" %} in the other html files for inheritance
		<a href="{% url 'add' %}">Add a new Task</a> 
			It is django feature, where we are using the name feature, which allows us to update the route w/o modifying the html code
		<a href="{% url 'tasks:index' %}">View Tasks</a>
			Update it to this value. Also inside the url.py file, declare variable like:
				app_name = "tasks"
				Which will allow app_name route to be accessed correctly.

		CSRF Vulnerability:
			- Django allows the CSRF token to be created per user.
			- Django middleware contains this facility.

	We will explore django ways of creating the forms. Because it comes with some additional benefits and simplify our lives a lot.

	```python
		from django import forms
		 class NewFormTask(forms.Form)
	```
	- We get a lot of client side validation facility, when we use the Django forms
	- But we must also do the server side validation as well. Because it is easy to disable the client side validation. Also server side validation is more upto date.
	- Do not hardcode the URL into your codebase, it is not a good design. 
	- We can use HttpResposeRedirect, to goback to any other page inside the code.

- So far we were using the gobal variable tasks to do the things, but we want the data to be maintained per user wise. How do we go about it ?
- Django has a concept of `session` which we can use to save the data per user-wise.
- 
# React-Tutorial-for-Python-backend-developers


Howdie partners !

This is how to connect Django backend framework to React front library 

We are goint to create simple data entry application in the backend and return data on the frontend from the backend using Axios library

Reason to choose React with Django:

Both React and Django are the most popular libraries and frameworks in their respective domains.
React’s SPA optimization and Django’s powerful features make it even better.
They have large community support and provide immediate assistance whenerver needed.

Both Django and React parts will be handled seperately and this results in:

- Cleaner and Clear interface between front-end and back-end logic and functions.
- Easy to deploy either the front-end part or the back-end part without redeploying the other.
- If there are separate teams working in front-end and back-end respectively they need not worry about another part as both can work independently.
- scalable and multiple client (web, mobile) apps. All the clients will have to consume the same API provided by the back-end side.

We need to work on 2 parts :

1- The Back-end  where we're going to create API using DJANG-REST 

2- and the front-end where we will interact directly with the API using React JS.

So, we're going to create a simple project to write employee's name and his department in the backend and then connect react 
as our main frontend to django server to fetch data and display it in our react application.

We will need django isntalled obviously, 

and I will work in virtual environemnt, i will use pipenv, so if you dont'have it, you can pip install pipenv and once that finsihed

go ahead and pipenv install djangorestframework first which is a toolkit for building our API; and also we need to 

pipenv isntall django-cors-headers for handling the server headers required for 

Cross-Origin Resource Sharing (CORS) and this is to add CORS headers which allows our API to be accessed on other domains.

and later we will add corsheaders in INSTALLED_APP in settings file in django.

models.py: Now let’s create a database model for our project. 

Here is models.py file of our app : ewmployee and department are two fields that are used to store the name of the empl and her or his department respectively.

serializer.py: Create serializer.py inside the app folder. 

and Serializers are basically used to convert complex data to native Python datatypes that can then be easily rendered into JSON(Which we are going to use in React on the client side). 
 
views.py: Here is views.py in which we can create our method like GET, PUT, POST, DELETE. 

We will have only two methods, get and post

In  GET method we are returning data from the model by calling React.objects.all() and then using list comprehension to convert the emp and deptmt in python’s dictionary. 

In the POST method, we are simply saving the data bypassing the data to ReactSerializer(). 

It’s time to define the endpoint of the API which is the URL where our client will hit to consume data from the server. 

It is generally the place where our resources (database and other functions) live.

urls.py: Here is the main urls.py from the project. 

The localhost:8000  is the end-point of our ReactView class.


There are few changes in settings.py file which are listed below 

1- Add rest_framework , core, corsheaders  to INSTALLED APPS

2- Add corsheaders.middleware.CorsMiddleware to MIDDLEWARE list.

3- Create  a dictionary assigned to REST_FRAMEWORK variable in which insert ‘DEFAULT_PERMISSION_CLASSES’: [   ‘rest_framework.permissions.AllowAny’ ]

4- Assign variable CORS_ORIGIN_ALLOW_ALL = True

and the cors headers package is used to tell the browser that web application running at one origin, access to our backend resources from a different origin. 

Now let's python manage.py makemigrations 

then python manage.py migrate

and then python manage.py createsuperuser

python manage.py runserver

*****************************

Frontend

npx create-react-app frontend

then cd frontend
npm install axios

Axios is the main tool for connecting back-end with front-end. 
All the requests will be sent to the server (back-end) with the help of Axios.

Inside App.js

import React from 'react';  
class App extends React.Component {  
    render() {  
        return( 
            <div> 
                <div> 
                    <div> 
                        <h1>BB Tech Company</h1>                        
                    </div> 
                </div> 
            </div>);  
    }  
}  
export default App;

Now we have to grab data from the server by using Axios. 
The componentDidMount method is called when the component is rendered. 
This is the right time to request a server for the data and we will use Axios in this method to store the data in a state obtained from the server and later on rendered by the help of a map in JavaScript.

Then run backend server and enter data to be reflected in react 

So this was React and Django working hand in hand.



# Ex.05 Design a Website for Server Side Processing
# Date:15.04.25
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
math.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>POWER</title> 
    <style>
        form{
    background-color: bisque;
        }
    h1{
    font-style: italic;
    }
    body{
    background-color: rgb(115, 115, 173);
    }
    input{
        background-color: rgb(162, 191, 234);
    }
    button{
        background-color: rgb(159, 23, 23);
    }
    p{
        font-size: x-large;
    }
    </style>
</head>
<body>
    <h1 align="center">CALCULATING POWER OF A LAMP</h1>
    <form action="{% url 'home' %}" method="POST">
        {% csrf_token %}
        intensity:
        <input type="text" name="intensity-input"> <br>
        resistance:
        <input type="text" name="resistance-input"> <br>
        <button type="submit">calculate</button>
        <p align="center">power of the lamp is:{{output}}</p>
    </form>
    
</body>
</html>
```
views.py
```
from django.shortcuts import render
def power(request):
    if request.method=="POST":
        intensity=int(request.POST.get('intensity-input'))
        resistance=int(request.POST.get('resistance-input'))
        power=(intensity**2)*resistance
        return render(request,'math.html',{'output':power})
    return render(request,'mathapp/math.html')

```
urls.py
```
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('',views.power,name='home'),
]
```
# SERVER SIDE PROCESSING:
# HOMEPAGE:
![alt text](<Screenshot 2025-04-16 064854.png>)
# RESULT:
The program for performing server side processing is completed successfully.

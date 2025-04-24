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
    <title>Document</title>
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
    form{
        font-size=xx-large;
    }
    </style>
</head>
<body>
    <h1 align="center">CALCULATING POWER OF A LAMP</h1>
    <form action="{% url 'home' %}" method="post">
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
    context={}
    context['power']="0"
    context['intensity_value']="0"
    context['resistance_value']="0"
    if request.method == 'POST':
        intensity_value = int(request.POST.get('intensity-input'))
        resistance_value = int(request.POST.get('resistance-input'))
        print('request=',request)
        print('intesity=',intensity_value)
        print('resistance=',resistance_value)
        power = (intensity_value ** 2)*resistance_value
        context['power']=power
        context['intensity_value']=intensity_value
        context['resistance_value']=resistance_value
        print('output=',power)
        return render (request, 'mathapp/math.html', {'output':power})
    return render(request,'mathapp/math.html',context)
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
![alt text](<praveena/mathapp/templates/mathapp/Screenshot 2025-04-24 213641.png>)
# HOMEPAGE:
![alt text](<praveena/mathapp/templates/mathapp/Screenshot 2025-04-24 213618.png>)
![alt text](<praveena/mathapp/templates/mathapp/Screenshot 2025-04-24 213627.png>)

# RESULT:
The program for performing server side processing is completed successfully.

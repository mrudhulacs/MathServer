# Ex.05 Design a Website for Server Side Processing
## Date:

29-03-2025
## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :

```
math.html
<html>
    <head>
        <style>
            body {
                
                background-color: rgba(20, 198, 218, 0.278);
                background-repeat: no-repeat;
                background-size: cover;
                background-position: center;
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-items: center;
                height: 100vh;
                
            }

            h1 {
                color: rgb(16, 16, 16);
                font-style: oblique;
                text-align: center;
                font-size: 50;
                

            }

            .inputs {
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-items: center;
                background-color: rgba(211, 211, 211, 0.278);
                width: 400px;
                height: 300px;
                padding: 20px;
                border-radius: 10px;
            }

            form {
                display: flex;
                flex-direction: column;
                width: 100%;
                gap: 10px;
            }

            label {
                font-size: 20px;
                color: rgb(29, 29, 28);
            }

            input {
                padding: 8px;
                border: 1px solid #ccc;
                border-radius: 5px;
                font-size: 14px;
                width: 100%;
            }

            button {
                padding: 10px;
                background-color: rgb(0, 255, 110);
                color: white;
                border: none;
                border-radius: 5px;
                font-size: 14px;
            }



        </style>
    </head>
    <body>
        <h1>Power of a Lamp </h1><br>
        <div class="inputs">
            <form method="POST">
                {% csrf_token %}
                <label for="input1">INTENSITY (A):</label>
                <input type="text" id="input1" name="intensity" placeholder="Enter Intensity" value="{{I}}">
                <label for="input2">RESISTANCE (Ohm):</label>
                <input type="text" id="input2" name="resistance" placeholder="Enter Resistance" value="{{R}}">
                <button type="submit">Calculate</button>
            </form>
            <label for="ans">POWER (W): </label>
            <input type="text" id="ans" value="{{power}}" readonly>
        </div>
    </body>
</html>


views.py
from django.shortcuts import render 
def power(request): 
    context={} 
    context['power'] = "0" 
    context['I'] = "0" 
    context['R'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        I =float( request.POST.get('intensity','0'))
        R = float(request.POST.get('resistance','0'))
        print('request=',request) 
        print('intensity=',I) 
        print('resistance=',R) 
        power = (((I)**2) * (R))
        context['power'] = power 
        context['I'] = I
        context['R'] = R 
        print('Power=',power) 
    return render(request,'mathapp/math.html',context)

urls.py

from django.contrib import admin 
from django.urls import path 
from mathapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('areaofrectangle/',views.power,name="areaofrectangle"),
    path('',views.power,name="areaofrectangleroot")
]
```


## SERVER SIDE PROCESSING:

![image](https://github.com/user-attachments/assets/7f8b136a-740a-4c23-8b0b-6b3aba55993a)

![image](https://github.com/user-attachments/assets/07c6f789-e707-4bb6-a978-47a1728a60ba)

## HOMEPAGE:

![image](https://github.com/user-attachments/assets/b2c1fea3-1445-442b-a367-3f1131d79b5f)


## RESULT:
The program for performing server side processing is completed successfully.

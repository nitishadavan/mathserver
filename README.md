# Ex.05 Design a Website for Server Side Processing
# Date:12-04-2025cd..
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
~~~
math.html 

<!DOCTYPE html>
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Power of a Lamp Filament</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
/* General body styling */
body {
    background: linear-gradient(to right, rgb(192, 255, 253), rgb(255, 200, 200));
    font-family: 'Arial', sans-serif;
    line-height: 1.6;
    margin: 0;
    padding: 0;
}

/* Center the form container */
.edge {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    padding: 0;
}

/* Styling for the form box */
.box {
    display: block;
    border: Thick dashed rgb(139, 144, 112);
    border-radius: 15px;
    width: 500px;
    min-height: 300px;
    font-size: 20px;
    background-color: hsl(0, 88%, 42%);
    box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.3);
    padding: 20px;
}

/* Styling for form elements */
.formelt {
    color: rgba(255, 5, 176, 0.934);
    text-align: center;
    margin-top: 7px;
    margin-bottom: 6px;
}

/* Input fields styling */
input[type="text"] {
    border: 2px solid rgb(139, 144, 112);
    border-radius: 10px;
    padding: 5px;
    width: 80%;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
    transition: all 0.3s ease-in-out;
}

/* Input fields hover and focus effects */
input[type="text"]:hover {
    border: 2px solid rgb(0, 200, 150);
}

input[type="text"]:focus {
    transform: scale(1.05);
    outline: none;
    border-color: rgb(0, 200, 150);
}

/* Submit button styling */
input[type="submit"] {
    background-color: rgb(0, 200, 150);
    color: white;
    border: none;
    border-radius: 10px;
    padding: 10px 20px;
    font-size: 18px;
    cursor: pointer;
    transition: 0.3s;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
}

/* Submit button hover effect */
input[type="submit"]:hover {
    background-color: rgb(0, 150, 100);
    transform: scale(1.1);
}

/* Heading styling */
h1 {
    color: rgb(0, 255, 60);
    text-align: center;
    padding-top: 20px;
    font-family: 'Georgia', serif;
    font-size: 28px;
    text-transform: uppercase;
}

/* Responsive design for smaller screens */
@media (max-width: 768px) {
    .box {
        width: 90%;
        padding: 20px;
    }

    input[type="text"] {
        width: 100%;
    }
}
</style>
</head>
<body>
<div class="edge">
    <div class="box">
        <h1>Power of a Light Filament</h1>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Intensity: <input type="text" name="intensity" value="{{i}}"></input> (in Wm<sup>-2</sup>)<br/>
            </div>
            <div class="formelt">
                Resistance: <input type="text" name="resistance" value="{{r}}"></input> (in ohm)<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"></input><br/>
            </div>
            <div class="formelt">
                Power: <input type="text" name="power" value="{{power}}"></input> (in W)<br/>
            </div>
        </form>
    </div>
</div>
</body>
</html>

views.py
from django.shortcuts import render

def power_calculator(request):
    power = None 
    intensity = None
    resistance = None 

    if request.method == 'POST':
        print("POST method is used")
        
        intensity = request.POST.get('intensity','0')
        resistance = request.POST.get('resistance','0')

        
        if intensity and resistance:
            try:
            
                I = float(intensity)
                R = float(resistance)
                power = I**2 * R
                print('request=',request)
                print('intensity=',I)
                print('resistance=',R)
                print('power=',power)  

            except ValueError:
                power = "Invalid input. Please enter numerical values."

    
    return render(request, 'mathapp/math.html', {'power': power, 'intensity': intensity, 'resistance': resistance})

urls.py
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.power_calculator, name='power_calculator'),
]
~~~
# SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-04-12 214446.png>)
# HOMEPAGE:
![alt text](<Screenshot 2025-04-12 214430.png>)
# RESULT:
The program for performing server side processing is completed successfully.

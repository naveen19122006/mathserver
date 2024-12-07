# Ex.05 Design a Website for Server Side Processing
# Date:15-04-2024
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
~~~
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mathserver</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(120deg, #ff9a9e, #fad0c4, #fad0c4);
            background-size: 400% 400%;
            animation: gradientBackground 10s ease infinite;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        @keyframes gradientBackground {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .container {
            width: 350px;
            padding: 20px;
            text-align: center;
            background: #ffffff;
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
            border-radius: 10px;
        }

        h1 {
            font-size: 1.8rem;
            color: #333;
            margin-bottom: 20px;
            background: linear-gradient(to right, #007BFF, #00C6FF);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .formelt {
            margin-bottom: 15px;
        }

        input[type="text"] {
            width: 90%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 1rem;
            transition: all 0.3s ease;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        input[type="text"]:focus {
            border-color: #007BFF;
            box-shadow: 0 0 10px rgba(0, 123, 255, 0.5);
            outline: none;
        }

        input[type="submit"] {
            padding: 12px 25px;
            background: linear-gradient(to right, #007BFF, #00C6FF);
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 6px 10px rgba(0, 123, 255, 0.2);
        }

        input[type="submit"]:hover {
            background: linear-gradient(to right, #0056b3, #007BFF);
            box-shadow: 0 10px 15px rgba(0, 123, 255, 0.4);
        }

        input[type="text"]:hover {
            transform: scale(1.02);
        }

        input[type="text"]:focus:hover {
            transform: scale(1.05);
        }

        input[type="submit"]:active {
            transform: translateY(2px);
            box-shadow: 0 3px 6px rgba(0, 123, 255, 0.3);
        }

        div.formelt {
            font-size: 1rem;
            color: #555;
        }

        sup {
            font-size: 0.8rem;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Volume of the Cylinder</h1>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Radius: <input type="text" name="radius" value="{{r}}">m<br/>
            </div>
            <div class="formelt">
                Height: <input type="text" name="height" value="{{h}}">m<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"><br/>
            </div>
            <div class="formelt">
                Volume: <input type="text" name="Volume" value="{{vol}}">m<sup>3</sup><br/>
            </div>
        </form>
    </div>
</body>
</html>
~~~
views.py
~~~
from django.shortcuts import render

def volume(request):
    context = {}
    context['vol'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    
    if request.method == 'POST':
        print("POST method is used")
        
        print('request.POST:', request.POST)
        
        r = request.POST.get('radius', '0') 
        h = request.POST.get('height', '0') 
        print('radius =', r)
        print('height =', h)
        
        vol = 1/3 * 3.14 * int(r) *int(r) *int(h)
        context['vol'] = vol
        context['r'] = r
        context['h'] = h
        print('Volume of Cube =', vol)
    
    return render(request, 'mathapp/math.html', context)
~~~

urls.py
~~~
from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('volume/',views.volume,name="volumeofcube"),
    path('',views.volume,name="volumeofcube")
]
~~~
# SERVER SIDE PROCESSING:


![Screenshot 2024-12-07 182723](https://github.com/user-attachments/assets/c20080ac-dc17-48e0-adfe-31c08366eb86)

# HOMEPAGE:

![Screenshot 2024-12-07 183743](https://github.com/user-attachments/assets/2d4905e3-f124-4441-ae3d-d0ab79757907)


![Screenshot 2024-12-07 182536](https://github.com/user-attachments/assets/c8368305-6b12-478c-b52f-66a691c95b2b)

# RESULT:
The program for performing server side processing is completed successfully.

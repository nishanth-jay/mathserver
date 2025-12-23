# Ex.04 Design a Website for Server Side Processing
# Date:13.12.2025
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
bulb.html
```
<!DOCTYPE html>
<html>
<head>
    <title>Power Calculator</title>
</head>
<body>
    <h2>Electric Power Calculator</h2>

    <form method="POST">
        {% csrf_token %}

        Intensity:
        <input type="number" step="any" name="intensity" required>
        <br><br>

        Resistance:
        <input type="number" step="any" name="resistance" required>
        <br><br>

        <button type="submit">Calculate Power</button>
    </form>

    {% if power %}
        <h3>Power = {{ power }} Watts</h3>
    {% endif %}
</body>
</html>

urls.py

from django.contrib import admin
from django.urls import path
from calculator import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.power, name="power"),
]

views.py

from django.shortcuts import render

def power(request):
    power = ''
    if request.method == "POST":
        intensity = float(request.POST.get("intensity"))
        resistance = float(request.POST.get("resistance"))
        power = intensity ** 2 * resistance
    return render(request, 'bulb.html', {'power': power})
```

# SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-12-15 085445.png>)
# HOMEPAGE:
![alt text](<Screenshot 2025-12-15 085302.png>)
# RESULT:
The program for performing server side processing is completed successfully.

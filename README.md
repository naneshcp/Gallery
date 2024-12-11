# Ex.08 Design of Interactive Image Gallery
# Date:09/12/2024
# AIM:
To design a web application for an inteactive image gallery with minimum five images.

# DESIGN STEPS:
## Step 1:
Clone the github repository and create Django admin interface.

## Step 2:
Change settings.py file to allow request from all hosts.

## Step 3:
Use CSS for positioning and styling.

## Step 4:
Write JavaScript program for implementing interactivity.

## Step 5:
Validate the HTML and CSS code.

## Step 6:
Publish the website in the given URL.
```
# PROGRAM :
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Interactive Photo Gallery</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: aqua;
        }

        .gallery {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 10px;
        }

        .photo {
            margin-top: 10%;
            margin-left: 2%;
            width: 200px;
            height: 400px;
            overflow: hidden;
            border-radius: 10px;
            border-width: 2px;
            border-color: solid black;
        }

        .photo img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            cursor: pointer;
            transition: transform 0.3s;
        }

        .photo img:hover {
            transform: scale(1.1);
        }

        .lightbox {
            display: none;
            position: fixed;
            z-index: 1;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            align-items: center;
            justify-content: center;
        }

        .lightbox-content {
            max-width: 90%;
            max-height: 80%;
        }

        .close {
            position: absolute;
            top: 20px;
            right: 30px;
            font-size: 30px;
            font-weight: bold;
            color: white;
            cursor: pointer;
        }
    </style>
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const lightbox = document.getElementById('lightbox');
            const lightboxImg = document.getElementById('lightbox-img');
            const photos = document.querySelectorAll('.photo img');
            const close = document.querySelector('.close');

            photos.forEach(photo => {
                photo.addEventListener('click', function() {
                    lightbox.style.display = 'flex';
                    lightboxImg.src = photo.src;
                });
            });

            close.addEventListener('click', function() {
                lightbox.style.display = 'none';
            });

            lightbox.addEventListener('click', function(event) {
                if (event.target !== lightboxImg) {
                    lightbox.style.display = 'none';
                }
            });
        });
    </script>
</head>
<body>
    <h1 style="font-size: 80px;">Interactive Photo Gallery</h1>
    <div class="gallery">
        <div class="photo">
            {%load static%}
            <img src={% static "images/apache.webp" %} alt="Apache">
        </div>
        <div class="photo">
            {%load static%}
            <img src={% static "images/bmw.jpg"%} alt="BMW">
        </div>
        <div class="photo">
            {%load static%}
            <img src={% static "images/pulsar.webp"%} alt="Pulsar">
        </div>
        <div class="photo">
            {%load static%}
            <img src={%static "images/royal_enfield.png"%} alt="Royal enfeild">
        </div>
        <div class="photo">
            {%load static%}
            <img src={%static "images/valentiono_rossi.jpg"%} alt="Yamaha z9x">
        </div>
    </div>
    <div id="lightbox" class="lightbox">
        <span class="close">&times;</span>
        <img class="lightbox-content" id="lightbox-img">
    </div>
</body>
</html>

views.py:
from django.shortcuts import render
def igaly(request):
    return render(request,'imagegallery.html')

urls.py:
from django.contrib import admin
from django.urls import path
from imagegallery import views

urlpatterns = [
   path('gallery/',views.igaly)
]

# OUTPUT:

![output08(web)](https://github.com/user-attachments/assets/4eee357a-3b5b-4acf-86de-4eebd5af99ce)

![output08(web)cmd'](https://github.com/user-attachments/assets/7d7d52c8-23ab-436b-8481-e41d1ef8d1b0)

# RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.

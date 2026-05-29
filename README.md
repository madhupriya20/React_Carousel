# Ex05 Image Carousel
## Date: 28/05/2026
## NAME: MADHUPRIYA R
## REG NO:212224040177

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
## app.css
```
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(to right, #1e3c72, #2a5298);
}

.container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: white;
}

.carousel-image {
  width: 500px;
  height: 300px;
  object-fit: cover;
  border-radius: 15px;
  box-shadow: 0px 4px 15px rgba(0,0,0,0.5);
}

.buttons {
  margin-top: 20px;
}

.buttons button {
  margin: 10px;
  padding: 12px 25px;
  border: none;
  border-radius: 8px;
  background-color: #ff9800;
  color: white;
  font-size: 16px;
  cursor: pointer;
}

.buttons button:hover {
  background-color: #e68900;
}

.dots {
  margin-top: 15px;
}

.dot {
  height: 14px;
  width: 14px;
  margin: 5px;
  background-color: lightgray;
  border-radius: 50%;
  display: inline-block;
}

.active {
  background-color: yellow;
}
```

## app.jsx
```
import React, { useState } from "react";
import "./App.css";

function App() {

  const places = [
    {
      url: "https://images.unsplash.com/photo-1506744038136-46273834b3fb",
      name: "Beautiful Lake"
    },
    {
      url: "https://images.unsplash.com/photo-1500530855697-b586d89ba3ee",
      name: "Mountains"
    },
    {
      url: "https://images.unsplash.com/photo-1493246507139-91e8fad9978e",
      name: "Green Nature"
    },
    {
      url: "https://images.unsplash.com/photo-1507525428034-b723cf961d3e",
      name: "Blue Beach"
    }
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % places.length);
  };

  const prevImage = () => {
    setCurrentIndex(
      (currentIndex - 1 + places.length) % places.length
    );
  };

  return (
    <div className="container">

      <h1>Image Carousel</h1>

      <img
        src={places[currentIndex].url}
        alt="place"
        className="carousel-image"
      />

      <h3>{places[currentIndex].name}</h3>

      <div className="buttons">
        <button onClick={prevImage}>Previous</button>
        <button onClick={nextImage}>Next</button>
      </div>

      <div className="dots">
        {places.map((_, index) => (
          <span
            key={index}
            className={
              index === currentIndex
                ? "dot active"
                : "dot"
            }
          ></span>
        ))}
      </div>

    </div>
  );
}

export default App;
```


## OUTPUT

<img width="1352" height="853" alt="image" src="https://github.com/user-attachments/assets/08016e0c-6c73-4354-9f62-48ad3bda007f" />

<img width="1337" height="860" alt="image" src="https://github.com/user-attachments/assets/4dbaafee-6739-437a-b5f5-32d91fc822f6" />

<img width="1353" height="870" alt="image" src="https://github.com/user-attachments/assets/0f018f6b-9b50-48ec-ae4d-f183043a8310" />

<img width="1346" height="848" alt="image" src="https://github.com/user-attachments/assets/f86eae58-8196-4ca7-a431-aacf4dbb22e9" />







## RESULT
The program for creating Image Carousel using React is executed successfully.

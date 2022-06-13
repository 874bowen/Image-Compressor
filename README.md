# Image Compression using React.js

Images draw attention, trigger emotions and improve the user experience of your website. Image compression involves the reduction of the size of your image so that it takes less space on the hard drive and for better search engine optimization when it comes to websites e.g., 2mb to 440kbs. The image still retains its physical properties. We are going to use React to compress our images. 
In this demo we are going to explore how we can achieve this. 


## Github

Check out the complete source code in this   [GitHub Repository](https://github.com/874bowen/Image-Compressor.git).

## Pre-requisites
To effectively follow along through this article you are required to have: 
- React.js basics
- Basic knowledge of HTML
- Knowledge in Javascript
- Some knowledge in Bootstrap

## Introduction
In this demo we are going to use the `browser-image-compression` package to compress our images from a high resolution image to a low resolution image. You can read more about this package by clicking [this link](https://www.npmjs.com/package/browser-image-compression).
> `browser-image-compression` is a module used to compress jpeg and png images by reducing resolution or storage size before uploading to the server to save bandwidth.

you can install it via npm or yarn
```bash
mpm install browser-image-compression
# or
yarn add browser-image-compression
```
Then import it in your components
```javascript
import imageCompression from "browser-image-compression";
```

## Sample Project Setup
In this article I will need you to clone the project from GitHub
```bash
git clone https://github.com/874bowen/Image-Compressor.git
cd .\Image-Compressor\
yarn start
```
After this in your browser you should be able to see this page
![img.png](https://res.cloudinary.com/bowenivan/image/upload/v1655120622/img_qwy1rg.png)

## Usage

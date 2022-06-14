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
Let's now examine the `ImageCompressor.js` component to understand how the browser-image-compression package works.

### Configuring the Component's State
Since this is a class component we are able to store the state for our component.
```javascript
constructor() {
    super();
    this.state = {
      compressedLink:
        "https://testersdock.com/wp-content/uploads/2017/09/file-upload-1280x640.png",
      originalImage: "",
      originalLink: "",
      clicked: false,
      uploadImage: false
    };
  }
```

The `compressedLink` will store the image link of the compressed image and the `originalImage` and the `originalLink` will store the values of the originalImage and originalLink respectively. The `clicked` and `uploadImage` store a boolean value which is false by default and changes to true when a button is clicked and when an image is uploaded. 

### Handling the Uploaded Image
When the Image is uploaded we want change the state of our Component. To do this we are going to call the `setState` method since we just don't change the state of the component directly. 

```javascript
<input
    type="file"
    accept="image/*"
    className="mt-2 btn btn-outline-warning w-75"
    onChange={e => this.handle(e)}
/>
```

Once we have uploaded an image the `handle` method will be called 

```javascript
handle = e => {
const imageFile = e.target.files[0];
this.setState({
  originalLink: URL.createObjectURL(imageFile),
  originalImage: imageFile,
  outputFileName: imageFile.name,
  uploadImage: true
});
};
```

After uploading files we can access the list of uploaded files using `event.target.files` we can then get the first file since we can process at a time using `e.target.files[0]`. We can also change the state using `setState` setting the originalLink, originalImage, outputFileName and uploadImage state as shown above.

> URL.createObjectURL() is a static method that creates a string that containing a URL representing the object given in the parameter. 

### User interface 
We will use the shorthand for if else statement, `ternary operator` to change the user interface of our application when the user has not uploaded and image and he/she has uploaded an image.

```javascript
{this.state.uploadImage ? (
  <Card.Img
    className="ht"
    variant="top"
    src={this.state.originalLink}
  ></Card.Img>
) : (
  <Card.Img
    className="ht"
    variant="top"
    src="https://testersdock.com/wp-content/uploads/2017/09/file-upload-1280x640.png"
  ></Card.Img>
)}
```
If the state uploadImage is `true` it would replace the image the link of the Card Image with the `originalLink` which the state changed upon uploading. Otherwise, the Card Image link will be hard coded as shown above.

It is only after an image has been uploaded that we will see the compress button. 

```javascript
{this.state.outputFileName ? (
  <Button
    variant="primary"
    onClick={e => this.click(e)}
  >
    Compress
  </Button>
) : (
  <></>
)}
```

When the image is not uploaded we don't have the state `outputFileName` hence we don't see the `compress` button. This state is set only after uploading hence returning the compress button.

# React Simple Image Viewer

Simple image viewer component for React.

# Installation

```shell
$ npm install react-simple-image-viewer
```
or
```shell
$ yarn add react-simple-image-viewer
```

# Example

```jsx
import React, { useState, useCallback } from 'react';
import { render } from 'react-dom';
import ImageViewer from 'react-simple-image-viewer';

function App() {
  const [currentImage, setCurrentImage] = useState(0);
  const [isViewerOpen, setIsViewerOpen] = useState(false);
  const images = [
    'http://placeimg.com/1200/800/nature',
    'http://placeimg.com/800/1200/nature',
    'http://placeimg.com/1920/1080/nature',
    'http://placeimg.com/1500/500/nature',
  ];

  const openImageViewer = useCallback((index) => {
    setCurrentImage(index);
    setIsViewerOpen(true);
  }, []);

  const closeImageViewer = () => {
    setCurrentImage(0);
    setIsViewerOpen(false);
  };

  return (
    <div>
      {images.map((src, index) => (
        <img
          src={ src }
          onClick={ () => openImageViewer(index) }
          width="300"
          key={ index }
          style={{ margin: '2px' }}
          alt=""
        />
      ))}

      {isViewerOpen && (
        <ImageViewer
          src={ images }
          currentIndex={ currentImage }
          disableScroll={ false }
          closeOnClickOutside={ true }
          closeOnClickInside={ true }
          onClose={ closeImageViewer }
        />
      )}
    </div>
  );
}

render(<App />, document.getElementById('app'));
```
# API

| Property              |  Type         | Description                                                                       |
| :--------------       | :--------     | :-------------------------------------------------------------------------------- |
| src                   | string[]      | Array of image URLs                                                               |
| currentIndex          | number        | Index of image in `src` property which will be shown first when viewer is opened  |
| onClose               | function      | Callback which will be called when viewer will closed                             |
| backgroundStyle       | object        | Custom styles for background of modal window                                      |
| disableScroll         | boolean       | Disable scrolling images by mouse wheel                                           |
| closeOnClickOutside   | boolean       | Whether viewer should be closed when clicking outside of image                    |
| closeOnClickInside    | boolean       | Whether viewer should be closed when clicking inside image                        |
| closeComponent        | JSX.Element   | Custom component for the close button                                             |
| leftArrowComponent    | JSX.Element   | Custom component for the left arrow                                               |
| rightArrowComponent   | JSX.Element   | Custom component for the right arrow                                              |

# Shortcuts

| Shortcut        | Description                     |
| :-------------- | :------------------------------ |
| Escape          | Close the viewer                |
| Right Arrow / l | Next image                      |
| Left Arrow / h  | Previous image                  |
| Mouse wheel     | Scrolling previous / next image |

# References to original repository

[Github Repository](https://github.com/specter256/react-simple-image-viewer)

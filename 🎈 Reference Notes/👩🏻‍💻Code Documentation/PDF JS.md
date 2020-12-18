#Note-JS-PDF #Note-PDF
https://levelup.gitconnected.com/creating-a-pdf-viewer-in-javascript-9b988b5ec163

> Learn how to create a PDF opener in Javascript using PDF.js

# Creating a PDF Viewer in JavaScript
Learn how to create a PDF viewer in Javascript using PDF.js
-----------------------------------------------------------

![](https://miro.medium.com/max/2808/1*WZZhQ2EZ3euxz36bmURYUA.png)

Implementing PDF js

We are going to create a PDF viewer which will have the following functionality:

1.  View a PDF
2.  Go to the next page
3.  Go to the previous page
4.  Go to a particular page number

First download PDF.js files from [here](https://mozilla.github.io/pdf.js/).

HTML File for Rendering the PDF
-------------------------------

Create a new `index.html` file, and in that create:

*   `canvas` → Where the pdf will be rendered.
*   previous `button` → To go to the previous page.
*   next `button` → To go to the next page.
*   `input` box → To enter a page number.
*   Go to page `button` → Button to go to a particular page.
*   2 span elements → Display the current page number and total pages of the PDF

In addition to the `index.html` file, create a `script.js` file where we write our JavaScript code to create a PDF viewer.

First initialize the variables:

Now add event listeners to handle the PDF renderer once the page loads:

*   We need to initialize the PDF.js with a source PDF
*   We can use the `getDocument` method to get a promise which resolves to `pdfData`
*   The PDF data has a function `getPage`
*   The `getPage` will return a promise
*   Once the promise is resolved we get the page data
*   We can then use the render method in the page data to render it in the `canvas`

Now when we call `initPdfRenderer`, this will assign the `pdfData` to the `pdf` variable.

Add events for `previousButton`, `nextButton`, and `goToPage` buttons.

Now let’s create a `renderPage` function to render the PDF page to the canvas:

We have a method to get `pdfData` and render `page`. Let’s write our `pageRenderingQueue`.

If the user clicks next page/previous page it will add/subtract 1 to the `currentPageNum` and pass it to the `renderPageQueue` method. This will check if the `pageRenderingQueue` is `null`. If it is `null`, then we call the `renderPage` method, else assign the page number which is to be rendered to the queue. Once the page rendering is complete, it will check if the `pageQueue` is empty and perform the respective action if needed.

Let’s create a `renderNextPage` and `renderPreviousPage` method.  
If the user clicks “next page”, do `currentPageNum + 1` and call `renderPage`. Similarly, for “previous page” do `currentPageNum — 1` and call `renderPage`. We also need to check if the `currentPageNum` is the first or last page.

Now let’s implement the “go to page number” function.

Get the page number from the input box, then check if the number is a valid number and call the `renderPage` method.

So the final code is:

Thanks for Reading 📖. I hope you enjoyed the article. If you found any typos or mistakes, send me a private note 📝 Thanks 🙏 😊 .

Follow me [JavaScript Jeep🚙💨](https://medium.com/u/f9ffc26e7e69?source=post_page-----98efbae5e8aa----------------------) .

**Please make a donation** [**here**](https://www.paypal.com/paypalme2/jagathishSaravanan)**. 98% of your donation is donated to someone needs food 🥘. Thanks in advance.**
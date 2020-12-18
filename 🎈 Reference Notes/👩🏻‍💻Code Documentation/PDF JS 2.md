https://usefulangle.com/post/20/pdfjs-tutorial-1-preview-pdf-during-upload-wih-next-prev-buttons

> This tutorial explains how to display a PDF file in a HTML page, and browse through its pages using the Javascript PDF.JS library.

# How to Display PDF in HTML Page using Javascript
Mozilla's PDF.JS is PDF viewer made with HTML5 technologies. It can help your application in custom rendering of PDF files — showing a PDF file in a <div> in your HTML page and browsing through its pages using Javascript.

Please note that PDF.JS is just a PDF viewer and not a PDF editor. It is not a library to create PDF files.

PDF.JS is used by Firefox internally to display PDF files. In fact PDF.JS is so good that even Opera [decided to use it](https://hacks.mozilla.org/2014/05/how-fast-is-pdf-js/).

#### Example — Displaying PDF in a div Container

Click on the below button to display [this PDF](https://mozilla.github.io/pdf.js/web/compressed.tracemonkey-pldi-09.pdf) file.

#### Download Example Codes

[Download](https://usefulangle.com/downloads/20-1.zip)

#### PDF.JS APIs Used in This Tutorial

When you include the PDF.JS script files, you get a pdfjsLib global object. This object provides a number of APIs that you can call in your Javscript code.

*   **pdfjsLib.getDocument**({ url: pdf\_url })
    
    This asynchonous method loads the PDF file. The return value is a Promise which resolves with a PDFDocumentProxy object. In simple words, PDFDocumentProxy is the handle of the current PDF file.
    
    pdf\_url is the url to a PDF file in your server. Cross Domain PDFs are allowed but CORS headers need to be set in the server.
    
    In case you would like to display the PDF during upload, a local url of the PDF can be generated through URL.createObjectURL() function.
    
    You can also pass binary data as a parameter. If you have a base-64 encoded data, you can convert it to a binary string through atob function.
    
        
        
        pdf_doc = await pdfjsLib.getDocument({ url: 'http://yourserver.com/sample.pdf' });
        
        
        pdf_doc = pdfjsLib.getDocument({ data: binary_data });
        
    
    Note that if using await to wait for the Promise to get settled, it needs to be wrapped in an async function.
    
*   pdf\_doc.**numPages**
    
    It is a read-only property that gets the number of pages in the PDF file.
    
        var total_pages = pdf_doc.numPages;
    
*   pdf\_doc.**getPage**(page\_no)
    
    This asynchonous method loads the specified page of the PDF. The return value is a Promise which resolves with a PDFPageProxy object. In simple words, PDFPageProxy is the handle of the specified page of the PDF.
    
    Note that this function just loads the page, and not renders the page on the screen.
    
        
        page = await pdf_doc.getPage(page_no);
        
    
*   page.**getViewport**(scale)
    
    This synchonous method returns the dimensions of the current page of the PDF (in px) at a specified zoom level.
    
        
        var viewport = page.getViewport(1);
        
        
        var height = viewport.height;
        
        
        var width = viewport.width;
        
    
*   page.**render**(renderContext)
    
    This asynchonous method renders the current page of the PDF on the screen.
    
    Rendering can be done in either a <canvas> or <svg> element. In this tutorial, a canvas element is used.
    
        
        var viewport = page.getViewport(1);
        
        
        var render_context = {
            canvasContext: document.querySelector('#pdf-canvas').getContext('2d'),
            viewport: viewport
        };
        
        
        await page.render(render_context);
        
    

#### Writing Code, Step 1 : Including PDF.JS Script Files

*   Go to [PDF.JS Home Page](https://mozilla.github.io/pdf.js/) and download the files. There will be 2 files in the "build" directory. Include them in your HTML. In this tutorial, version 2.2 of PDF.JS has been used.
    ```js
        <script src="js/pdf.js"></script>
        <script src="js/pdf.worker.js"></script>
        
    
    PDF.JS files are pretty huge. It is better if you minify them. You can use an [online UglifyJS minifier](https://skalman.github.io/UglifyJS-online/).
    
*   Alternatively you can include PDFJS from a CDN.
    
        <script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.2.228/pdf.min.js"></script>
    

#### Step 2 : Preparing HTML
    ```html
    <button id="show-pdf-button">Show PDF</button> 
    <div id="pdf-main-container">
        <div id="pdf-loader">Loading document ...</div>
        <div id="pdf-contents">
            <div id="pdf-meta">
                <div id="pdf-buttons">
                    <button id="pdf-prev">Previous</button>
                    <button id="pdf-next">Next</button>
                </div>
                <div id="page-count-container">Page <div id="pdf-current-page"></div> of <div id="pdf-total-pages"></div></div>
            </div>
            <canvas id="pdf-canvas" width="400"></canvas>
            <div id="page-loader">Loading page ...</div>
        </div>
    </div>

*  `#show-pdf-button `button will start loading the PDF.
*   `#pdf-loader` is the container where a "PDF Loading" message would be shown while the PDF is being loaded.
*   `#pdf-prev `&` #pdf-next` are buttons that will go the Previous & Next page of the PDF.
*  ` #pdf-current-page` will hold the current page no of the PDF.
*   `#pdf-total-pages` will hold the total number pages in the PDF.
*   `#pdf-canvas` is the canvas element where the PDF will be rendered.
*   `#page-loader` will show a "Page Loading" message while a page is being rendered.

#### Step 3 : Defining some Javascript variables

We need a few global variables that will hold properties used throughout the code.

    var _PDF_DOC,
        _CURRENT_PAGE,
        _TOTAL_PAGES,
        _PAGE_RENDERING_IN_PROGRESS = 0,
        _CANVAS = document.querySelector('#pdf-canvas');
    

*   \_PDF\_DOC will hold the PDFDocumentProxy object that is resolved on the getDocument() Promise.
*   \_CURRENT\_PAGE will hold the current page number. \_TOTAL\_PAGES will hold the total no of pages in the PDF.
*   \_PAGE\_RENDERING\_IN\_PROGRESS is a flag that will hold whether a currently being rendered or not. If rendering of a page is in progress, then UI should not start rendering of another page. This is to prevent a page-content mismatch. Remember page rendering is asynchronous, it will take at least a few milliseconds to render a page.
*   \_CANVAS will hold the canvas element.

#### Step 4 : Rendering the PDF with Javascript

Two custom functions shown below handle most of the code.

showPDF loads the PDF. It accepts the url of the PDF as parameter. On successful loading it calls the showPage function that will show the first page of the PDF.

showPage loads and renders a specified page of the PDF. While a page is being rendered, Previous and Next buttons are disbaled. A very important point is to note that we have to change the scale of the rendered page as per the width of the canvas element. In the current case, the width of the canvas element is less than the actual width of the PDF, so when PDF is rendered in the canvas it has to be scaled down.

Event handlers on the Previous / Next buttons simple decrement / increment the current page shown and call the showPage function.

    var _PDF_DOC,
        _CURRENT_PAGE,
        _TOTAL_PAGES,
        _PAGE_RENDERING_IN_PROGRESS = 0,
        _CANVAS = document.querySelector('#pdf-canvas');
    
    
    async function showPDF(pdf_url) {
        document.querySelector("#pdf-loader").style.display = 'block';
    
        
        try {
            _PDF_DOC = await pdfjsLib.getDocument({ url: pdf_url });
        }
        catch(error) {
            alert(error.message);
        }
    
        
        _TOTAL_PAGES = _PDF_DOC.numPages;
        
        
        document.querySelector("#pdf-loader").style.display = 'none';
        document.querySelector("#pdf-contents").style.display = 'block';
        document.querySelector("#pdf-total-pages").innerHTML = _TOTAL_PAGES;
    
        
        showPage(1);
    }
    
    
    async function showPage(page_no) {
        _PAGE_RENDERING_IN_PROGRESS = 1;
        _CURRENT_PAGE = page_no;
    
        
        document.querySelector("#pdf-next").disabled = true;
        document.querySelector("#pdf-prev").disabled = true;
    
        
        document.querySelector("#pdf-canvas").style.display = 'none';
        document.querySelector("#page-loader").style.display = 'block';
    
        
        document.querySelector("#pdf-current-page").innerHTML = page_no;
        
        
        try {
            var page = await _PDF_DOC.getPage(page_no);
        }
        catch(error) {
            alert(error.message);
        }
    
        
        var pdf_original_width = page.getViewport(1).width;
        
        
        var scale_required = _CANVAS.width / pdf_original_width;
    
        
        var viewport = page.getViewport(scale_required);
    
        
        _CANVAS.height = viewport.height;
    
        
        document.querySelector("#page-loader").style.height =  _CANVAS.height + 'px';
        document.querySelector("#page-loader").style.lineHeight = _CANVAS.height + 'px';
    
        var render_context = {
            canvasContext: _CANVAS.getContext('2d'),
            viewport: viewport
        };
            
        
        try {
            await page.render(render_context);
        }
        catch(error) {
            alert(error.message);
        }
    
        _PAGE_RENDERING_IN_PROGRESS = 0;
    
        
        document.querySelector("#pdf-next").disabled = false;
        document.querySelector("#pdf-prev").disabled = false;
    
        
        document.querySelector("#pdf-canvas").style.display = 'block';
        document.querySelector("#page-loader").style.display = 'none';
    }
    
    
    document.querySelector("#show-pdf-button").addEventListener('click', function() {
        this.style.display = 'none';
        showPDF('https://mozilla.github.io/pdf.js/web/compressed.tracemonkey-pldi-09.pdf');
    });
    
    
    document.querySelector("#pdf-prev").addEventListener('click', function() {
        if(_CURRENT_PAGE != 1)
            showPage(--_CURRENT_PAGE);
    });
    
    
    document.querySelector("#pdf-next").addEventListener('click', function() {
        if(_CURRENT_PAGE != _TOTAL_PAGES)
            showPage(++_CURRENT_PAGE);
    });
    

#### Browser Compatibility

The above code will work good in all major browsers, including IE 10+.

#### Enabling Text Selection ?

To enable text selection, some extra steps need to be followed. See [How to Enable Text Selection in PDF.JS](https://usefulangle.com/post/90/javascript-pdfjs-enable-text-layer) for more.

#### PDF Viewer Javascript Plugin

A premium responsive PDF Viewer plugin is also available. It has some advanced features like embedding multiple PDF files in a single page, viewing PDF files when a link is clicked, modal & full-screen mode, finding out whether user has fully viewed the PDF etc.

[![](https://usefulangle.com/img/posts/20-pdf-viewer-javascript-plugin.jpg)](https://1.envato.market/Qdxao)
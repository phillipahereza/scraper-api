## Scraping a JS-Rendered webpage

### Background Information
When a browser wants to access a webpage, it sends a request to the server on which the files that make up the webpage are located. 
The server then sends a response consisting of the page’s source code back to the browser. The browser then interprets the HTML, CSS, etc, in the source code, 
allows any Javascript to run, and displays the page.

Of the parts that comprise the source code of a webpage, the Javascript code is of particular interest to us in this article. 
When a page is loaded into a browser, it becomes a document object, whose HTML elements, or element nodes, Javascript can access. 
As it runs, Javascript can create new HTML elements and append them to the document. A page on which this occurs is called a page 
rendered by Javascript. The new elements will not be present in the original source code of the page, the code that you see when 
you right-click and press “view page source”; but they will be present in the code that you see if you download the page as an HTML 
document and open it in a text editor, or in the code in the “elements” tab in your browser’s developer tools. This HTML code, which 
can be retrieved by JavaScript using the DOM's innerHTMLproperty, constitutes the code of the completed webpage that the browser displays 
after the Javascript has finished running, and has all of the data that you need for scraping.

When scraping using python or any other language, a library like urllib or requests sends a request to the server, it receives the source code of the webpage,
just like a browser does. However, Python can not run the Javascript and allow it to create the elements that hold the content that you need to scrape. 
And that's where this app comes in, to scrape a JS rendered website;

```
POST /scrape/
```
*Request Body*
```
{
    "url": "https://google.com"
}
```
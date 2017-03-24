# Poo near you (Part 2)

So far, you have learnt how to mark a location on a map by finding its latitude and longitude, and you know how to customise the marker as an emoji. The data file we looked at contains a lot of data though, and typing lots of things in seems like it would take a long time. Let's get the computer to automatically retrieve the data and plot it on the map for us!

## Run a local web server

The open data we found was in a format called JSON (JavaScript Object Notation) which is easy to read and work with using JavaScript. You may find many other open data sources as JSON and you can access these using the methods we will show you. To be able to read the data automatically, you will need to run a web server on your computer. Fortunately, as long as you have Python 3 installed, you already have the capability to run a very basic web server!

**On some networks (for example in schools) the use of the command prompt and certain ports will be restricted, so you may need to ask for support from your network manager to be able to complete this part of the resource.**

### Running a web server

1. Open a terminal (Raspberry Pi, Mac) or Command Prompt (Windows):

    **Windows**

    ![Open a command prompt](images/command-prompt.png)

    **Raspberry Pi**

    ![Open a terminal on Raspberry Pi](images/terminal.png)

    **Mac**
    
    ![Open a terminal on Mac](images/mac-terminal.png)


1. Change to the directory your web page is saved in by typing `cd` followed by a space, then the path to the directory. An example directory is shown, but you may have saved your web page in a different location, so make sure you use the path to the directory you used.

    **Windows**

    ![Change to the directory](images/cd-to-directory.png)

    **Raspberry Pi**

    ```bash
    cd /home/pi/googlemaps
    ```

    **Mac**

    ```bash
    cd Documents/googlemaps
    ```

1. Type the following command to start the web server, which will serve files from the directory you were in when you started it.

    **Windows**

    ```bash
    python -m http.server
    ```

    **Raspberry Pi and Mac**

    ```bash
    python3 -m http.server
    ```

1. You should see a message which will be similar to this - `Serving HTTP on 0.0.0.0 port 8000 ...`

1. Open up a web browser. In the address bar, type in `http://localhost:8000/index.html` and press enter. You should see your map webpage appear, but this time it is being __served__ to you by the Python web server!

    ![Served page with map](images/local-server-map.png)


## Read the JSON file




## Why did we need to run a web server?

When data is hosted on the web, the website owners have to be careful that they do not open up their servers to attacks from hackers. You may have seen warnings before about cross site scripting attacks (or XSS for short) which can allow hijackers to put their own malicious code on normal, legitimate websites. To stop this from happening, web browsers operate a **same origin policy** which means that code on webpage 1 can only access data from webpage 2 if both pages are of the same origin (which very roughly means "are hosted on the same server").

So now we have a problem. Our script will not be running on the same server as the data.

**Idea 1 - Download the JSON file from the data source and save it as a file on my computer**

If you access the webpage by just opening it up in the web browser, the address will start with `file://`, as will the address of the JSON file if you download it.

  ![Open the file in a browser](images/file-in-browser.png)

For security reasons, JavaScript doesn't allow you to access local files (files on the same computer) so this approach won't work.

**Idea 2 - Download the JSON file and run a web server**

This is the method we used, and here's why it works. By running the simple Python web server, you are making your computer pretend to "serve" up the pages to your web browser. When you visit `http://localhost:8000` it is similar to when you visit a real website - you are making a request to a server which then sends you back the page you asked for.

If you put your `index.html` file on your web server, and then access it as `http://localhost:8000/test.html`, its **origin** is `http://localhost:8000`. If you also send your JSON file via the web server, it can be accessed at `http://localhost:8000/penalties.json` and so its **origin** is __also__ `http://localhost:8000`. This satisfies the same origin rule, and so we are able to access the JSON data in our JavaScript.


##

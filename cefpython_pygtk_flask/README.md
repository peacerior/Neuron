# CEF Python, PyGTK, Flask
This variation uses the following:  
PyGTK -- Windowing  
CEF Python -- Portable browser  
Flask -- Local webserver  
Tornado -- Launches Flask - Threading issues with Flask caused the need for Tornado  
Tkinter -- Folder selection  
Bootstrap - Web UI  
xmlhttprequest - Communication with Flask to update UI  

# How to Use

## Get Started

### Download
Create a directory for new your project  
Download the contents of this folder into your directory

### Setup Environment
(This step is optional but recommended)  
Create new virtual environment `CMD HERE`  
Install requirements `CMD HERE`

### Test Application
Start the application to make sure everything is working `python neuron.py`  
The application comes with a sample GUI with some interactions with the backend.  
The data you see is loaded dynamically from the backend then javascript loads them into the form.  
You can modify the data in the form and click `Save`. Then an AJAX call will be made to send it to the backend and
printed in the terminal.  
The included HTML and Javascript functions are a sample of how actions can be performed.

## Understanding Structure

### neuron.py
Starts the application.  It is a `cefpython` (portable chrome browser) application, and the windowing system.  
It calls a function called `find_port()` which finds an open port on the local machine.  
It then calls the function `start_cyclone()` which imports from `cyclone.py`

### cyclone.py
This file is used to run `Tornado` which handles running Flask and the incoming connections from your web gui.  
There were threading issues with Flask and this was an easy solution to that problem.  
Cyclone is importing the Flask application from `app.py`

### app.py
This is the Flask application.  This is were routing for http calls will be, creating the HTML, and the backend of  
the application.  
This is where main part of the application is handled. 

### Templates directory
Contains the HTML files for the application

### Static directory
Contains the resources for the HTML files. Fonts, images, javascript libraries etc.

### Locales directory
Language for `cefpython`

### Everything else
The other files in the directory are for executing cefpython/neuron.py

## Rebrand Project

### Windowing and Icons
Open `neuron.py` and go to the `PyGTKExample` class and in the `__init__` function you can modify 
`self.mainWindow.set_title('Neuron')` to rename your application.  
Then edit `icon.ico` and `icon_big.ico` to your application's icon.

### Main Logic and Visuals
Modifying `app.py` will change the main logic of your application.  
Changing the files in the `templates` and `static` directory is where the GUI aspect of your application resides.

## Create Windows Executable with PyInstaller
Coming Soon....
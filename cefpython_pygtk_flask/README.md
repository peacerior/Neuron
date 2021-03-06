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

[Python 2.7](https://www.python.org/downloads/)  
[PyGTK All In One for Python 2.7](http://ftp.gnome.org/pub/GNOME/binaries/win32/pygtk/2.24/)  
`pip install flask`  
`pip install tornado`  
`pip install cefpython3`  
`pip install pyinstaller`  

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

## Modifying the Application
After rebranding the project, development on the new application can begin.

### Main Program Logic
`app.py` is the Flask application that controls the main logic of the application.  
Sample AJAX functions are included in the HTML to communicate with the backend Flask application.

### GUI
`Bootstrap` is used for the HTML.  This is not required, any HTML can be used.  
Modifying the files in the `templates` and `static` directories will allow you change the GUI.  
You call run `python app.py` and go to `localhost:5000` in your browser to work on your application without having 
to execute `neuron.py`

## Create Windows Executable with PyInstaller
The following must be executed on a 32bit Windows machine with 32bit Python  
Execute `pyinstaller neuron_installer.spec`  
Two directories will be created, `dist` and `build`  
`build` contains the temporary files used to create the executable  
`dist` contains the files that need to be distributed  
Manually copy the folders `static` and `templates` into `dist/Neuron`  
You can modify `neuron_installer.spec` to match the name of the new application

# References
[CEFPython](https://github.com/cztomczak/cefpython) - Python bindings for the Chromium Embedded Framework  
[Flask](http://flask.pocoo.org/) - Python microframework  
[Bootstrap](http://getbootstrap.com/) - Web Front-End Framework  
[PyInstaller](http://www.pyinstaller.org/) - Turn Python projects into executables  

# Screenshot
![Neuron Screenshot](screen_shot.png)
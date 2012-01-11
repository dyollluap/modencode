A Flask app serving the homepage of the modENCODE project

## Requirements:
- Flask
- CherryPy WSGI Server (for production)

## Installation:
Make sure these are installed:

- Flask <code>easy_install flask</code>
- CherryPy <code>easy_install cherrypy</code>

## Setup

- Run the install script <code>python install.py</code> and choose the **port** the app will run at
- Configure **SMTP** and other settings in <code>config.py</code>
- Modify site constants as needed in <code>models/constants.py</code>

## Running
### Flask/Werkzeug Server (for development)
The app can be run through the Werkzeug WSGI server that comes with Flask. To run it, execute <code>python flask_app.py</code>.
Provided you have set <code>DEBUG = True</code> in your <code>config.py</code> file, this option will give you an interactive debugger and your app will be reloaded if changes to source files are detected.

### CherryPy WSGI Server (for production)
1. Run <code>./start_server.sh</code>. This will launch <code>cherryd</code> with settings coming from <code>cherrypy.conf</code> that uses an 'in-between' script <code>create_flask_app.py</code> to attach the Flask Object to the server
2. A file, <code>cherrypy.pid</code> will be created that has the id of the process running
3. Calling <code>./stop_server.sh</code> will read the .pid file and kill the process waiting for child threads to terminate

### Update from GitHub
Run <code>./github_update.sh</code> to stop the running server, run a git pull and start the server again.

## FAQ
### How do I show a server down message?
1. Have an RSS feed ready where the last item has the message you want to display in the title with a special trigger-tag in the message
 that modENCODE should look for.
2. Look at <code>constants.py</code> file and modify the <code>MESSAGING_RSS_URL</code> constant to point to your RSS feed looking for
 a trigger-tag defined in <code>MESSAGING_RSS_TAG</code>.

### How do I stop showing a server down message?
1. Publish a new item in the RSS feed that will NOT have a trigger-tag in its title.
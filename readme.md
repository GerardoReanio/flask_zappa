
1.virtualenv iland-env --python=python3.8

2.source env-iland/bin/activate

3.pip install flask==2.0.1


4. nano env-iland/bin/activate

    agregar

    export FLASK_APP=app
    export FLASK_ENV=development

5. deactivate y luego source env-iland/bin/activate

6.touch app.py
    add hw for flask

7. test up flask app with flask run

8. mkdir static
    mkdir templates

9. reemplazar las rutas de los archivos estaticos 

    ejemplo : 

    <link rel="stylesheet" href="css/animate.css">

    <link rel="stylesheet" href="{{ url_for('static', filename='css/animate.css') }} ">

10. pip install zappa==0.53.0

11. flask run 

Si se lanza un error al ejecutar nuevamente el flask run 

Traceback (most recent call last):
  File "/Users/workstation/Desktop/Publicaciones/flask+zappa/env-iland/bin/flask", line 5, in <module>
    from flask.cli import main
  File "/Users/workstation/Desktop/Publicaciones/flask+zappa/env-iland/lib/python3.9/site-packages/flask/__init__.py", line 7, in <module>
    from .app import Flask as Flask
  File "/Users/workstation/Desktop/Publicaciones/flask+zappa/env-iland/lib/python3.9/site-packages/flask/app.py", line 19, in <module>
    from werkzeug.local import ContextVar
ImportError: cannot import name 'ContextVar' from 'werkzeug.local' (/Users/workstation/Desktop/Publicaciones/flask+zappa/env-iland/lib/python3.9/site-packages/werkzeug/local.py)

12. pip uninstall werkzeug
    pip install werkzeug==2.0.1


13. flask run OK 

 * Serving Flask app 'app' (lazy loading)
 * Environment: development
 * Debug mode: on
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 864-880-344

14. zappa init

zappa init

███████╗ █████╗ ██████╗ ██████╗  █████╗
╚══███╔╝██╔══██╗██╔══██╗██╔══██╗██╔══██╗
  ███╔╝ ███████║██████╔╝██████╔╝███████║
 ███╔╝  ██╔══██║██╔═══╝ ██╔═══╝ ██╔══██║
███████╗██║  ██║██║     ██║     ██║  ██║
╚══════╝╚═╝  ╚═╝╚═╝     ╚═╝     ╚═╝  ╚═╝

Welcome to Zappa!

Zappa is a system for running server-less Python web applications on AWS Lambda and AWS API Gateway.
This `init` command will help you create and configure your new Zappa deployment.
Let's get started!

Your Zappa configuration can support multiple production stages, like 'dev', 'staging', and 'production'.
What do you want to call this environment (default 'dev'): dev

AWS Lambda and API Gateway are only available in certain regions. Let's check to make sure you have a profile set up in one that will work.
We found the following profiles: default, orbis, gerardo, and cbg. Which would you like us to use? (default 'default'): cbg

Your Zappa deployments will need to be uploaded to a private S3 bucket.
If you don't have a bucket yet, we'll create one for you too.
What do you want to call your bucket? (default 'zappa-hwm73co5d'): iland-bucket

It looks like this is a Flask application.
What's the modular path to your app's function?
This will likely be something like 'your_module.app'.
We discovered: app.app
Where is your app's function? (default 'app.app'): 

You can optionally deploy to all available regions in order to provide fast global service.
If you are using Zappa for the first time, you probably don't want to do this!
Would you like to deploy this application globally? (default 'n') [y/n/(p)rimary]: n

Okay, here's your zappa_settings.json:

{
    "dev": {
        "app_function": "app.app",
        "profile_name": "cbg",
        "project_name": "1-flask-zappa",
        "runtime": "python3.8",
        "s3_bucket": "iland-bucket"
    }
}

Does this look okay? (default 'y') [y/n]: 

Done! Now you can deploy your Zappa application by executing:

        $ zappa deploy dev

After that, you can update your application code with:

        $ zappa update dev

To learn more, check out our project page on GitHub here: https://github.com/Zappa/Zappa
and stop by our Slack channel here: https://zappateam.slack.com

Enjoy!,
 ~ Team Zappa!

 15. zappa deploy dev

Creating 1-flask-zappa-dev-ZappaLambdaExecutionRole IAM Role..
Creating zappa-permissions policy on 1-flask-zappa-dev-ZappaLambdaExecutionRole IAM Role.
Downloading and installing dependencies..
 - pyyaml==5.4.1: Downloading
100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████| 662k/662k [00:00<00:00, 2.10MB/s]
 - markupsafe==2.0.1: Downloading
100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████| 30.6k/30.6k [00:00<00:00, 816kB/s]
Packaging project as zip.
Uploading 1-flask-zappa-dev-1632466630.zip (7.8MiB)..
100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████| 8.15M/8.15M [00:10<00:00, 775kB/s]
Scheduling..
Scheduled 1-flask-zappa-dev-zappa-keep-warm-handler.keep_warm_callback with expression rate(4 minutes)!
Oh no! An error occurred! :(

==============

Traceback (most recent call last):
  File "/Users/workstation/Desktop/Publicaciones/flask+zappa/iland-env/lib/python3.8/site-packages/zappa/cli.py", line 3422, in handle
    sys.exit(cli.handle())
  File "/Users/workstation/Desktop/Publicaciones/flask+zappa/iland-env/lib/python3.8/site-packages/zappa/cli.py", line 588, in handle
    self.dispatch_command(self.command, stage)
  File "/Users/workstation/Desktop/Publicaciones/flask+zappa/iland-env/lib/python3.8/site-packages/zappa/cli.py", line 630, in dispatch_command
    self.deploy(self.vargs["zip"], self.vargs["docker_image_uri"])
  File "/Users/workstation/Desktop/Publicaciones/flask+zappa/iland-env/lib/python3.8/site-packages/zappa/cli.py", line 952, in deploy
    template = self.zappa.create_stack_template(
  File "/Users/workstation/Desktop/Publicaciones/flask+zappa/iland-env/lib/python3.8/site-packages/zappa/core.py", line 2417, in create_stack_template
    self.cf_template.add_description("Automatically generated with Zappa")
AttributeError: 'Template' object has no attribute 'add_description'


16. pip install troposphere==2.7.1

 ERROR: Command errored out with exit status 1:
     command: /Users/workstation/Desktop/Publicaciones/flask+zappa/iland-env/bin/python -c 'import io, os, sys, setuptools, tokenize; sys.argv[0] = '"'"'/private/var/folders/pk/rpqbgv7n5y51srp__p414d7h0000gn/T/pip-install-ldm5xxkh/troposphere_3aa84eabb63f461f97e8462613beb98b/setup.py'"'"'; __file__='"'"'/private/var/folders/pk/rpqbgv7n5y51srp__p414d7h0000gn/T/pip-install-ldm5xxkh/troposphere_3aa84eabb63f461f97e8462613beb98b/setup.py'"'"';f = getattr(tokenize, '"'"'open'"'"', open)(__file__) if os.path.exists(__file__) else io.StringIO('"'"'from setuptools import setup; setup()'"'"');code = f.read().replace('"'"'\r\n'"'"', '"'"'\n'"'"');f.close();exec(compile(code, __file__, '"'"'exec'"'"'))' egg_info --egg-base /private/var/folders/pk/rpqbgv7n5y51srp__p414d7h0000gn/T/pip-pip-egg-info-b7davptx
         cwd: /private/var/folders/pk/rpqbgv7n5y51srp__p414d7h0000gn/T/pip-install-ldm5xxkh/troposphere_3aa84eabb63f461f97e8462613beb98b/
    Complete output (1 lines):
    error in troposphere setup command: use_2to3 is invalid.
    ----------------------------------------
WARNING: Discarding https://files.pythonhosted.org/packages/a7/f5/b066cea6022142792207d356d9183b3812d01e27910023438f354aa98b43/troposphere-2.7.1.tar.gz#sha256=ea2e5f2f82c224eaa1414a008b1939aae124c3e3e1dd993301968f155b333bd7 (from https://pypi.org/simple/troposphere/) (requires-python:>=2.7, !=3.0.*, !=3.1.*, !=3.2.*, !=3.3.*). Command errored out with exit status 1: python setup.py egg_info Check the logs for full command output.
ERROR: Could not find a version that satisfies the requirement troposphere==2.7.1 (from versions: 0.1.2, 0.2.0, 0.3.0, 0.3.2, 0.3.3, 0.3.4, 0.4.0, 0.5.0, 0.6.0, 0.6.1, 0.6.2, 0.7.0, 0.7.1, 0.7.2, 1.0.0, 1.1.0, 1.1.1, 1.1.2, 1.2.0, 1.2.1, 1.2.2, 1.3.0, 1.4.0, 1.5.0, 1.6.0, 1.7.0, 1.8.0, 1.8.1, 1.8.2, 1.9.0, 1.9.1, 1.9.2, 1.9.3, 1.9.4, 1.9.5, 1.9.6, 2.0.0, 2.0.1, 2.0.2, 2.1.0, 2.1.1, 2.1.2, 2.2.0, 2.2.1, 2.2.2, 2.3.0, 2.3.1, 2.3.2, 2.3.3, 2.3.4, 2.4.0, 2.4.1, 2.4.2, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 2.4.8, 2.4.9, 2.5.0, 2.5.1, 2.5.2, 2.5.3, 2.6.0, 2.6.1, 2.6.2, 2.6.3, 2.6.4, 2.7.0, 2.7.1, 3.0.0, 3.0.1, 3.0.2, 3.0.3)
ERROR: No matching distribution found for troposphere==2.7.1

17. SOLVE point 16
pip install setuptools==57.5.0
pip install troposphere==2.7.1

18.zappa deploy dev
(Werkzeug 2.0.1 (/Users/workstation/Desktop/Publicaciones/flask+zappa/iland-env/lib/python3.8/site-packages), Requirement.parse('Werkzeug<1.0'), {'zappa'})
Calling deploy for stage dev..
Creating flask-zappa-dev-ZappaLambdaExecutionRole IAM Role..
Creating zappa-permissions policy on flask-zappa-dev-ZappaLambdaExecutionRole IAM Role.
Downloading and installing dependencies..
 - pyyaml==5.4.1: Downloading
100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 662k/662k [00:00<00:00, 1.40MB/s]
 - markupsafe==2.0.1: Downloading
100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 30.6k/30.6k [00:00<00:00, 754kB/s]
Packaging project as zip.
Uploading flask-zappa-dev-1632468232.zip (8.1MiB)..
100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 8.44M/8.44M [00:12<00:00, 663kB/s]
Scheduling..
Scheduled flask-zappa-dev-zappa-keep-warm-handler.keep_warm_callback with expression rate(4 minutes)!
Uploading flask-zappa-dev-template-1632468259.json (1.6KiB)..
100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 1.62k/1.62k [00:00<00:00, 3.16kB/s]
Waiting for stack flask-zappa-dev to create (this can take a bit)..
 75%|███████████████████████████████████████████████████████████████████████████████████████████████▎                               | 3/4 [00:14<00:04,  4.72s/res]
Deploying API Gateway..
Deployment complete!: https://6o5bw0rh5c.execute-api.eu-west-1.amazonaws.com/dev
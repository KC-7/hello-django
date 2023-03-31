# Django Todo App

This is a Django-based todo app that allows users to add, edit, delete, and toggle items on their to-do list (CRUD). It has been built using Django version 3.2.3.

**Live Link:** [kc-django-todo-app.herokuapp.com](https://kc-django-todo-app.herokuapp.com/)


## README Contents

| [Main Files](#main-files)                              |                                                             |
|--------------------------------------------------------|-------------------------------------------------------------|
| [manage.py](#managepy)                                 | [urls.py](#urlspy-)                                         |
| [views.py](#viewspy)                                   | [apps.py](#appspy)                                          |
| [models.py](#modelspy)                                 | [todo_list.html](#todo-listhtml-1)                          |
| [forms.py](#formspy)                                   | [edit_item.html](#edit-itemhtml)                            |
| [admin.py](#adminpy)                                   | [add_item.html](#add-itemhtml)                              |
| [todo_list.html](#todo-listhtml)                       | [settings.py](#settingspy)                                  |

| [Additional Files](#additional-files)                  |                                                             |
|--------------------------------------------------------|-------------------------------------------------------------|
| [requirements.txt](#requirementstxt)                   | [.gitignore](#gitignore)                                    |
| [env.py](#envpy)                                       | [Procfile](#procfile)                                       |

| [Python Testing Files](#python-testing-files)          |                                                             |
|--------------------------------------------------------|-------------------------------------------------------------|
| [test_views.py](#test-viewspy)                         | [test_forms.py](#test-formspy)                              |
| [test_models.py](#test-modelspy)                       | [Testing Coverage Report: 100%](#testing-coverage-report--100-)|

| [Hosting and Deployment](#hosting-and-deployment)      |                                                             |
|--------------------------------------------------------|-------------------------------------------------------------|

| [Gitpod Reminders](#gitpod-reminders)                  |                                                             |
|--------------------------------------------------------|-------------------------------------------------------------|

| [Credits](#credits)                                    |                                                             |
|--------------------------------------------------------|-------------------------------------------------------------|


# Main Files

## manage.py
This file is a command-line utility provided by Django for administrative tasks such as running the development server, creating database tables, and creating a new app. It sets the environment variable DJANGO_SETTINGS_MODULE to point to the settings file for the project and then runs the execute_from_command_line() function of the django.core.management module.

## views.py
This file contains all the view functions for the app. These functions interact with the models and templates to handle user requests and generate responses.

get_todo_list(request): This function retrieves all items in the database and sends them to the todo/todo_list.html template to be rendered.

add_item(request): This function adds a new item to the database when a user submits a form with a POST request.

edit_item(request, item_id): This function updates an existing item in the database when a user submits a form with a POST request.

toggle_item(request, item_id): This function toggles the done field of an item in the database.

delete_item(request, item_id): This function deletes an item from the database.

## models.py
This file contains the database model for the app. It defines a single model, Item, which has two fields: name (a CharField) and done (a BooleanField). The Item class also includes a __str__() method that returns the name of the item.

## forms.py
This file contains the form used for adding and editing items. It is based on the Item model and includes fields for name and done.

## admin.py
This file is used to register the Item model with Django's admin site. This allows administrators to view, add, edit, and delete items through the Django admin interface.

## todo_list.html
This file is a Django template that is used to render the to-do list on the home page of the app. It includes a loop that iterates over all items in the database and displays them in a table. Each row of the table includes buttons to toggle, edit, and delete the item, as well as a link to add a new item.

## settings.py
The settings.py file contains the Django project settings, which configure the web application. It imports the os and Path modules and sets the BASE_DIR variable to the root directory of the project. It imports the env.py file if it exists, which contains environment variables. The SECRET_KEY variable stores a secret key for the project, and the DEBUG variable is set to True for development mode. The ALLOWED_HOSTS variable lists the domains that the app can run on. The INSTALLED_APPS variable lists the apps that the project includes. The MIDDLEWARE variable lists the middleware classes that handle requests and responses. The ROOT_URLCONF variable specifies the URL routing configuration. The TEMPLATES variable contains the configuration for the project's templates. The WSGI_APPLICATION variable specifies the application callable for the project. The DATABASES variable sets up the database configuration for the project, using the dj_database_url module to parse the DATABASE_URL environment variable. The AUTH_PASSWORD_VALIDATORS variable contains the password validation settings for the authentication system. The LANGUAGE_CODE, TIME_ZONE, USE_I18N, USE_L10N, and USE_TZ variables set up internationalization and time zone settings. The STATIC_URL variable specifies the URL path for static files, such as CSS and JavaScript files. The DEFAULT_AUTO_FIELD variable sets the default primary key field type for models.

## urls.py:

The urlpatterns list is the central routing mechanism in a Django project. It maps URLs to views, which are Python functions or classes that process HTTP requests and generate HTTP responses.

Each path() function in the urlpatterns list takes at least two arguments: a URL pattern (as a string) and a view function (or a class-based view). The URL pattern can contain named groups, optional groups, and regular expressions, allowing for complex URL matching.

The name parameter is optional but highly recommended, as it allows you to refer to the URL in other parts of the project using the {% url %} template tag.

Django also provides the include() function, which allows you to include other URLconfs. This is useful for breaking up large URLconfs into smaller, modular ones that can be reused across multiple projects.

For more information on Django URL routing, see the official documentation at https://docs.djangoproject.com/en/3.2/topics/http/urls/.

## apps.py 
The apps.py file contains a TodoConfig class that extends the AppConfig class from Django. It sets the default auto field to BigAutoField and specifies the name of the application as todo.

## todo_list.html
The todo_list.html file contains the HTML markup for the main content of the web page. It includes a heading, a table with a loop that displays the to-do items, and a link to add new items. The table element has rows and cells, and the cells display the to-do item names, toggle buttons, edit buttons, and delete buttons. The if statement inside the loop checks if the item is done, and if so, it applies a strike-through style to the item name. If there are no items to display, the table shows a message that there are no items to do.

## edit_item.html 
The edit_item.html file contains an HTML form that allows a user to edit a to-do item. It uses the POST method to submit the form and includes a CSRF token for security. It also includes a button to update the item.

## add_item.html
The add_item.html file contains an HTML form that allows a user to add a new to-do item. It uses the POST method to submit the form and includes a CSRF token for security. It also includes a button to add the item.

# Additional Files

## requirements.txt
The requirements.txt file contains a list of Python packages required for the Django project to run. It includes packages such as Django, Gunicorn, and psycopg2-binary.

## env.py 
The env.py file sets environment variables for the Django project, including the secret key, database URL, and Heroku hostname. This file should not be committed to version control, as it contains sensitive information.

## .gitignore
The .gitignore file specifies files and directories that should be ignored by Git when committing changes. This file includes patterns such as *.pyc and __pycache__ for Python bytecode files, node_modules/ for Node.js modules, and *.sqlite3 for SQLite database files.

## Procfile 
The Procfile specifies the command to run the Django project on a Heroku server. It uses Gunicorn to serve the project and specifies the location of the WSGI application.

# Python Testing Files

## test_views.py

The TestViews class contains test methods that use Django's built-in TestCase class to test the behavior of the views in the views.py module. Each test method sends an HTTP request to a specific URL and checks that the response has the expected status code and template name.

The test_can_add_item() method tests that a new todo item can be added to the database by submitting a POST request to the /add URL. It checks that the response is a redirect to the homepage (/) and that the new item has been added to the database.

The test_can_delete_item() method tests that a todo item can be deleted from the database by submitting a GET request to the /delete/<item_id> URL. It checks that the response is a redirect to the homepage (/) and that the item has been removed from the database.

The test_can_toggle_item() method tests that a todo item's done attribute can be toggled by submitting a GET request to the /toggle/<item_id> URL. It checks that the response is a redirect to the homepage (/) and that the item's done attribute has been updated in the database.

The test_can_edit_item() method tests that a todo item's name can be updated by submitting a POST request to the /edit/<item_id> URL. It checks that the response is a redirect to the homepage (/) and that the item's name has been updated in the database.

For more information on testing Django views, see the official documentation at https://docs.djangoproject.com/en/3.2/topics/testing/tools/#the-testcase-class.

## test_models.py

The TestModels class contains test methods that use Django's built-in TestCase class to test the behavior of the Item model in the models.py module.

The test_done_defaults_to_false() method tests that the done attribute of a new todo item defaults to False when no value is provided.

The test_item_string_method_returns_name() method tests that the __str__() method of the Item model returns the name of the item.

For more information on testing Django models, see the official documentation at https://docs.djangoproject.com/en/3.2/topics/testing/tools/#model-tests.

## test_forms.py

This file contains test cases for the ItemForm class in the forms.py module. The ItemForm class is a ModelForm that is used to render and process forms related to the Item model in the todo app.

The test_item_name_is_required method tests if the form is invalid when the name field is empty. It creates a form instance with an empty name field and checks if is_valid() returns False, and if the name field error message is set to 'This field is required.'.

The test_done_field_is_not_required method tests if the form is valid when only the name field is provided. It creates a form instance with a non-empty name field and checks if is_valid() returns True.

The test_fields_are_explicit_in_form_metaclass method tests if the Meta class of the ItemForm specifies the expected fields. It creates a form instance and checks if the Meta.fields attribute is set to ['name', 'done'].

## Testing Coverage Report: 100%

| Module                             | Statements | Missing | Excluded | Coverage |
|------------------------------------|------------|---------|----------|----------|
| todo/__init__.py                   | 0          | 0       | 0        | 100%     |
| todo/admin.py                      | 3          | 0       | 0        | 100%     |
| todo/apps.py                       | 4          | 0       | 0        | 100%     |
| todo/forms.py                      | 6          | 0       | 0        | 100%     |
| todo/migrations/0001_initial.py    | 5          | 0       | 0        | 100%     |
| todo/migrations/__init__.py        | 0          | 0       | 0        | 100%     |
| todo/models.py                     | 6          | 0       | 0        | 100%     |
| todo/test_forms.py                 | 14         | 0       | 0        | 100%     |
| todo/test_models.py                | 9          | 0       | 0        | 100%     |
| todo/test_views.py                 | 37         | 0       | 0        | 100%     |
| todo/views.py                      | 35         | 0       | 0        | 100%     |
| **Total**                          | **119**    | **0**   | **0**    | **100%** |

Note: coverage.py v7.2.2, created at 2023-03-30 18:54 +0000

# Hosting and Deployment

This Django web application was developed using Gitpod, an online integrated development environment that allowed for easy collaboration and code sharing. The code was then pushed to GitHub, a web-based hosting service for version control using git. GitHub was used to store the codebase and track changes to the application's source code.

The live site was deployed using Heroku, a cloud platform that allows for easy deployment, scaling, and management of web applications. The database used by the application is hosted on ElephantSQL, a PostgreSQL database hosting service.

This combination of tools provided a robust and scalable infrastructure for the live site, while Gitpod and GitHub facilitated the collaborative development of the application. With the use of these technologies, the application can easily be maintained, updated and scaled in the future.

# Gitpod Reminders

To run a frontend (HTML, CSS, Javascript only) application in Gitpod, in the terminal, type:

`python3 -m http.server`

A blue button should appear to click: _Make Public_,

Another blue button should appear to click: _Open Browser_.

To run a backend Python file, type `python3 app.py`, if your Python file is named `app.py` of course.

A blue button should appear to click: _Make Public_,

Another blue button should appear to click: _Open Browser_.

In Gitpod you have superuser security privileges by default. Therefore you do not need to use the `sudo` (superuser do) command in the bash terminal in any of the lessons.

To log into the Heroku toolbelt CLI:

1. Log in to your Heroku account and go to *Account Settings* in the menu under your avatar.
2. Scroll down to the *API Key* and click *Reveal*
3. Copy the key
4. In Gitpod, from the terminal, run `heroku_config`
5. Paste in your API key when asked

You can now use the `heroku` CLI program - try running `heroku apps` to confirm it works. This API key is unique and private to you so do not share it. If you accidentally make it public then you can create a new one with _Regenerate API Key_.

# Credits

The site was built following a Code Institue Walktrough Project. 

The site uses the CI Python Template. 

The README was partially created by passing sections of code into ChatGPT, please allow for its limiations. This was used to improve documentation for future reference.

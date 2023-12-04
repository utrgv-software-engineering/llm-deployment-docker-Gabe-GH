# AI Starter Kit

This project is a Django-based application that serves as a starter kit for AI Engineering. It includes features such as authentication & authorization, utilization of a sqlite3 database, unit tests and integration tests, proper environment variable and secret management, and an admin interface to manage users and other data.

## Prerequisites

- Python (version)
- Django (version)
- Node.js (version 14.0.0 or later)
- npm (version 6.0.0 or later)

## Dependencies

This project uses a number of Python, JavaScript, and other libraries to provide its functionality:

### Python Dependencies

- `openai`: This library is used to interact with the OpenAI API, which provides access to powerful AI models.
- `python-dotenv`: This library is used to manage environment variables, which are crucial for managing secrets and configuration in a secure manner.
- `chromadb`: This library is used to provide vector database and embedding search functionality.
- `vcrpy`: This library is used to record and replay HTTP interactions, which is useful for testing.
- `tenacity`: This library is used to add retry logic to the application, which can help it recover from temporary issues.
- `gunicorn`: This is a WSGI HTTP server for Python web applications.
- `django`: This is the main web framework used by the application.
- `whitenoise`: This library is used to serve static files efficiently.
- `djangorestframework`: This library is used to build APIs in Django.
- `markdown`: This library is used to render Markdown text.
- `beautifulsoup4`: This library is used to parse HTML and XML documents.

### JavaScript Dependencies

- `webpack`: This is used to bundle JavaScript files for production.
- `stimulus`: This is a JavaScript framework that works well with Django.
- `idiomorph`: This library is used to provide manipulation of the DOM that can be used to make page updating more seamless.
- `tailwindcss-stimulus-components`: This library provides Stimulus components for Tailwind CSS.
- `prismjs`: This library is used for syntax highlighting in the application. It is configured via the `.babelrc` file to support all languages, use the 'tomorrow' theme, and include line numbers.

### CSS and Icon Libraries

- `TailwindCSS`: This is a utility-first CSS framework that is loaded via CDN. It is used for styling the application.
- `FontAwesome`: This is an icon library that is also loaded via CDN. It is used to add icons to the application.

### Other Dependencies

- `Node.js`: This is a JavaScript runtime built on Chrome's V8 JavaScript engine. It is used to run the JavaScript code in this project.
- `npm`: This is the package manager for Node.js and is used to manage the JavaScript dependencies in this project.

## Setup

### Node.js and npm Setup

Before you can install the JavaScript dependencies, you need to install Node.js and npm. Here's how you can install them on different operating systems:

#### Windows and macOS

1. Download the Node.js installer from the [official Node.js website](https://nodejs.org/).
2. Run the installer and follow the prompts to install Node.js and npm.

#### Ubuntu

1. Update your package list:

    ```bash
    sudo apt update
    ```

2. Install Node.js and npm:

    ```bash
    sudo apt install nodejs npm
    ```

3. Verify the installation:

    ```bash
    node -v
    npm -v
    ```

    This should print the versions of Node.js and npm.

### JavaScript and Webpack Setup

1. In the root of your project, you should find a `package.json` file. This file contains all the necessary dependencies for the JavaScript part of your project.

2. Install the JavaScript dependencies by running:

    ```bash
    npm install
    ```

    This command will install all the dependencies listed in `package.json`.

3. To bundle your JavaScript files and make them ready for production, you can use the build script defined in `package.json`. Run the following command:

    ```bash
    npm run build
    ```

    This will create a bundled JavaScript file using Webpack, which you can include in your Django templates.


### Django Setup

1. Install the Python dependencies:

    ```bash
    pip install -r requirements.txt
    ```

2. Run the Django migrations:

    ```bash
    python manage.py migrate
    ```

3. Start the Django development server:

    ```bash
    python manage.py runserver
    ```

## Usage

Once you have set up the project following the instructions in the Setup section, you can start the Django development server to begin using the application.

### Starting the Server

To start the server, run the following command from the root directory of the project:

```
python manage.py runserver
```

This will start the Django development server on the default port 8000.

### Accessing the Application

After starting the server, you can access the main application by navigating to:

```
http://localhost:8000
```

This is the home page of your application, where you can interact with the features provided by the AI Starter Kit.

### Admin Panel

Django comes with a built-in admin panel that allows you to manage the application's data. To access the admin panel, go to:

```
http://localhost:8000/admin
```

Before you can use the admin panel, you'll need to create a superuser account. You can do this by running the following command and following the prompts:

```
python manage.py createsuperuser
```

Once you have created a superuser account, you can log in to the admin panel using the credentials you set up.

### Interacting with the Application

The application's functionality will be available through its user interface and API endpoints. You can create, read, update, and delete data as per the application's design. The admin panel provides a convenient way to manage users and other data models directly.

## Deployment

The project includes a deployment script that automates the process of deploying the application to Azure and setting up GitHub Actions secrets. The deployment script uses a YAML configuration file to manage deployment settings.

### Deployment Dependencies

Before running the deployment script, ensure that the following dependencies are installed and configured:

- `az`: The Azure CLI tool must be installed and available in your system's PATH. It is used to interact with Azure services.
- `docker`: Docker must be installed and running to build and push the Docker image.
- `pynacl`: This Python library is required for encryption operations used in the script. Install it using `pip install pynacl`.

### Initializing a `config/deploy.yml`

To initialize the deployment configuration, run the `init` command of the deployment script. This will create a `config/deploy.yml` file with a template that you can fill out with your specific deployment details.

Example command:
```
python rocketship.py init
```

### Setup Deployment

Once you have filled out the `config/deploy.yml` with your deployment details, you can proceed with setting up the deployment by running the `setup` command of the deployment script. This command performs several actions:

1. Logs into Azure using the Azure CLI.
2. Logs into the Docker registry.
3. Builds the Docker image and pushes it to the specified registry.
4. Creates and pushes necessary secrets to the GitHub repository for GitHub Actions.
5. Updates the Azure App Service settings with the necessary environment variables.

Before running the setup command, ensure that you have the following environment variables set:

- `GITHUB_TOKEN`: A GitHub token with the necessary permissions to create secrets in your repository.
- `AZURE_SUBSCRIPTION_ID`: Your Azure subscription ID.
- Any other environment variables referenced in your `config/deploy.yml`.

Example command:
```
python rocketship.py setup
```

Make sure to review and customize the `config/deploy.yml` file according to your deployment requirements. The deployment script is a powerful tool that simplifies the process of getting your application up and running in a production environment.
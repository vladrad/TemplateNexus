# Flask Template Cookiecutter

## Overview
This is a Cookiecutter template for generating Flask applications with Kubernetes deployment configurations, database setups, and Docker support.

## What is Cookiecutter?
Cookiecutter is a command-line utility that creates projects from project templates. It uses a templating system where variables in the format `{{ cookiecutter.variable_name }}` are replaced with values defined in `cookiecutter.json`.

## Template Variables
The template uses the following variables defined in `cookiecutter.json`:
```json
{
    "project_slug": "my-flask-app",
    "kubernetes_namespace": "my-namespace"
}
```


## How Variables are Used

### Project Structure
The template variables are used throughout the project in various ways:

1. **Directory Names**: 
   - The main project directory uses `{{ cookiecutter.project_slug }}`
   - Python package naming follows the project slug

2. **Kubernetes Configurations**:
   - Namespace and deployment configurations use both `project_slug` and `kubernetes_namespace`
   - Used in service names and deployment labels

3. **Docker Configuration**:
   - Workdir path in Dockerfile
   - Gunicorn command configuration

## Usage

1. Install Cookiecutter:
    ```bash
    pip install cookiecutter
    ```

2. Generate project: 
    ```python
    cookiecutter flask_template --no-input project_slug=vlad kubernetes_namespace=test
    ```


TL'DR: String replace `{{ cookiecutter.variable_name }}` with the desired value.
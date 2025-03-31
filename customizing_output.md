# Customizing Output in GPT Engineer

GPT Engineer provides several ways to customize its output and behavior. This guide will walk you through the various methods of customization, including modifying preprompts, adjusting AI parameters, and working with different project configurations.

## Modifying Preprompts

Preprompts are used to guide the AI's behavior when generating code. GPT Engineer uses two main preprompt files:

1. `generate`: Used for initial code generation
2. `improve`: Used for improving existing code

These files are located in the `gpt_engineer/preprompts/` directory. You can modify these files to customize the AI's output.

### Customizing the Generate Preprompt

The `generate` preprompt sets the initial instructions for code generation. To customize it:

1. Open `gpt_engineer/preprompts/generate`
2. Modify the content to suit your needs. For example, you can add specific coding standards or architectural preferences.

Example modification:

```
Think step by step and reason yourself to the correct decisions to make sure we get it right.
First lay out the names of the core classes, functions, methods that will be necessary, As well as a quick comment on their purpose.

Follow these additional guidelines:
- Use camelCase for function names
- Include type hints for all function parameters and return values
- Add docstrings for all classes and functions

FILE_FORMAT

...
```

### Customizing the Improve Preprompt

The `improve` preprompt guides the AI when improving existing code. To customize it:

1. Open `gpt_engineer/preprompts/improve`
2. Modify the content to focus on specific aspects of code improvement.

Example modification:

```
Think step by step and reason yourself to the correct decisions to make sure we get it right.
Make changes to existing code and implement new code in the unified git diff syntax. When implementing new code, First lay out the names of the core classes, functions, methods that will be necessary, As well as a quick comment on their purpose.

When improving code, focus on:
- Optimizing performance
- Enhancing readability
- Improving error handling

FILE_FORMAT

...
```

## Adjusting AI Parameters

GPT Engineer uses default AI parameters for code generation. To customize these parameters, you can modify the API calls in the codebase. However, this requires more advanced knowledge of the project structure and the AI model being used.

## Working with Project Configurations

GPT Engineer uses a `gpt-engineer.toml` configuration file for project-specific settings. This file allows you to customize various aspects of the project, including build commands, test commands, and file paths.

### Creating a Configuration File

To create a `gpt-engineer.toml` file:

1. Create a new file named `gpt-engineer.toml` in your project's root directory.
2. Add the desired configuration options.

Example `gpt-engineer.toml`:

```toml
[run]
build = "npm run build"
test = "npm run test"
lint = "quick-lint-js"

[paths]
base = "./frontend"
src = "./src"

[gptengineer-app]
project_id = "your-project-id"

[[gptengineer-app.openapi]]
url = "https://api.gptengineer.app/openapi.json"
```

### Configuration Options

The `gpt-engineer.toml` file supports the following sections and options:

1. `[run]`: Defines commands for various project tasks
   - `build`: Command to build the project
   - `test`: Command to run tests
   - `lint`: Command to run the linter
   - `format`: Command to format the code

2. `[paths]`: Specifies important directories in your project
   - `base`: Base directory to operate in (useful for monorepos)
   - `src`: Source directory from which context will be retrieved

3. `[gptengineer-app]`: Configuration for gptengineer.app
   - `project_id`: Your project ID on gptengineer.app
   - `openapi`: List of OpenAPI schemas to use as context for the AI

### Reading and Writing Configurations

GPT Engineer provides functions to read and write the configuration file programmatically. These functions are located in the `gpt_engineer/core/project_config.py` file.

To read a configuration file:

```python
from gpt_engineer.core.project_config import Config

config = Config.from_toml("path/to/gpt-engineer.toml")
```

To write a configuration file:

```python
from gpt_engineer.core.project_config import Config

config = Config()
config.paths.base = "./frontend"
config.run.build = "npm run build"
config.to_toml("path/to/gpt-engineer.toml")
```

By leveraging these customization options, you can tailor GPT Engineer's output to better suit your project's needs and coding standards.
# Quickstart Guide

This guide will help you quickly set up and start using gpt-engineer, a powerful tool that allows you to generate and improve code projects using AI.

## Installation

To install gpt-engineer, run the following command:

```bash
python -m pip install gpt-engineer
```

For development purposes, you can clone the repository and install it using poetry:

```bash
git clone https://github.com/gpt-engineer-org/gpt-engineer.git
cd gpt-engineer
poetry install
poetry shell
```

## Setting Up API Key

Before using gpt-engineer, you need to set up your OpenAI API key. Choose one of the following methods:

1. Export as an environment variable:
   ```bash
   export OPENAI_API_KEY=[your api key]
   ```

2. Add to a `.env` file:
   - Create a copy of `.env.template` named `.env`
   - Add your `OPENAI_API_KEY` to the `.env` file

## Basic Usage

### Creating a New Project

1. Create an empty folder for your project.
2. Create a file called `prompt` (without an extension) inside your new folder.
3. Fill the `prompt` file with instructions for your desired application.
4. Run the following command:
   ```bash
   gpte <project_dir>
   ```
   Replace `<project_dir>` with the relative path to your project folder.

### Improving Existing Code

1. Locate the folder with the code you want to improve.
2. Create a file called `prompt` inside the folder with instructions for improvements.
3. Run the following command:
   ```bash
   gpte <project_dir> -i
   ```
   The `-i` flag enables improve mode.

## Advanced Features

### Custom Preprompts

You can specify custom "identities" for the AI agent:

```bash
gpte <project_dir> --use-custom-preprompts
```

### Vision Capabilities

For models with vision capabilities, you can include image inputs:

```bash
gpte <project_dir> gpt-4-vision-preview --prompt_file prompt/text --image_directory prompt/images -i
```

### Open Source and Local Models

gpt-engineer supports various models, including open-source options like WizardCoder. Check the [documentation](https://gpt-engineer.readthedocs.io/en/latest/open_models.html) for setup instructions.

## Common Use Cases

1. **Rapid Prototyping**: Quickly generate a basic structure for a new application.
2. **Code Refactoring**: Use improve mode to enhance existing codebases.
3. **Learning Tool**: Analyze AI-generated code to learn new programming concepts or patterns.
4. **Problem Solving**: Describe a coding problem and get AI-generated solutions.

## Additional Resources

- [Full Documentation](https://gpt-engineer.readthedocs.io/)
- [GitHub Repository](https://github.com/gpt-engineer-org/gpt-engineer)
- [Community Discord](https://discord.gg/8tcDQ89Ej2)

Remember to review and test all AI-generated code before using it in production environments.
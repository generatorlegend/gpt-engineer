# GPT-Engineer Command-Line Interface

This document provides a comprehensive guide to using the gpt-engineer command-line interface (CLI). The CLI allows you to generate or improve software projects using AI-powered code generation.

## Basic Usage

The basic command to run gpt-engineer is:

```
gpt-engineer [OPTIONS] [PROJECT_PATH]
```

If no `PROJECT_PATH` is specified, the current directory (`.`) is used.

## Options and Flags

### General Options

- `--model`, `-m`: Specify the model ID string (default: environment variable MODEL_NAME or "gpt-4o")
- `--temperature`, `-t`: Control randomness in output (default: 0.1)
- `--verbose`, `-v`: Enable verbose logging for debugging
- `--debug`, `-d`: Enable debug mode for debugging
- `--use-cache`: Speed up computations by caching LLM responses
- `--no_execution`: Run setup without calling LLM or writing code (for testing)
- `--sysinfo`: Output system information for debugging

### Mode Options

- `--improve`, `-i`: Improve an existing project by modifying files
- `--lite`, `-l`: Run generation using only the main prompt
- `--clarify`, `-c`: Discuss specifications with AI before implementation
- `--self-heal`, `-sh`: Enable self-healing mode to fix code when it fails

### Input Options

- `--prompt_file`: Specify a relative path to a text file containing a prompt (default: "prompt")
- `--entrypoint_prompt`: Specify a relative path to a file with entrypoint requirements
- `--image_directory`: Specify a relative path to a folder containing images
- `--use-custom-preprompts`: Use project-specific custom preprompts

### Azure Options

- `--azure`, `-a`: Specify the endpoint for Azure OpenAI Service

### Improvement Options

- `--skip-file-selection`, `-s`: Skip interactive file selection in improve mode
- `--diff_timeout`: Set diff regexp timeout (default: 3 seconds)

### Advanced Options

- `--llm-via-clipboard`: Use clipboard to communicate with AI

## Examples

1. Generate a new project in the current directory:
   ```
   gpt-engineer .
   ```

2. Improve an existing project with custom temperature:
   ```
   gpt-engineer --improve --temperature 0.2 /path/to/project
   ```

3. Use Azure OpenAI Service with a specific model:
   ```
   gpt-engineer --azure https://your-endpoint.openai.azure.com --model your-model-name /path/to/project
   ```

4. Run in lite mode with a custom prompt file:
   ```
   gpt-engineer --lite --prompt_file custom_prompt.txt /path/to/project
   ```

5. Use self-healing mode with verbose logging:
   ```
   gpt-engineer --self-heal --verbose /path/to/project
   ```

## Notes

- The `OPENAI_API_KEY` must be set in the environment or provided in a `.env` file within the working directory.
- When using the `azure_endpoint` parameter, provide the Azure OpenAI service endpoint URL.
- Custom preprompts can be used by placing them in a `preprompts` directory within your project folder and using the `--use-custom-preprompts` flag.

For more detailed information about each option and its usage, refer to the inline help by running:

```
gpt-engineer --help
```

This will display a comprehensive list of all available options and their descriptions.
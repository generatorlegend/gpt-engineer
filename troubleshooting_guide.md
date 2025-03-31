# Troubleshooting Guide

This guide provides solutions for common issues you might encounter while using gpt-engineer. If you're experiencing problems, please refer to the sections below for help.

## Table of Contents

1. [API-Related Issues](#api-related-issues)
2. [Code Generation Errors](#code-generation-errors)
3. [Configuration Issues](#configuration-issues)
4. [Execution Environment Problems](#execution-environment-problems)
5. [Performance and Resource Issues](#performance-and-resource-issues)

## API-Related Issues

### OpenAI API Key Not Found

**Problem**: The OpenAI API key is not set or cannot be found.

**Solution**:
1. Ensure you have set the `OPENAI_API_KEY` environment variable.
2. If using a `.env` file, make sure it's in the correct directory (usually the project root).
3. Check the `.env` file content:

```
OPENAI_API_KEY=your_api_key_here
```

4. If using Azure, set the `OPENAI_API_VERSION` and provide the Azure endpoint:

```python
python -m gpt_engineer.main project_directory --azure https://your-azure-endpoint.com
```

### Rate Limit Errors

**Problem**: You're encountering rate limit errors from the OpenAI API.

**Solution**:
1. The code implements an exponential backoff strategy. Wait a few moments and try again.
2. If persistent, check your OpenAI account for any usage limits or billing issues.
3. Consider using a different model or reducing the frequency of API calls.

## Code Generation Errors

### Incomplete or Incorrect Code Generation

**Problem**: The generated code is incomplete, incorrect, or doesn't meet requirements.

**Solution**:
1. Refine your initial prompt to be more specific and detailed.
2. Use the improve mode to iteratively enhance the generated code:

```python
python -m gpt_engineer.main project_directory --improve
```

3. Check the `DEBUG_LOG_FILE` and `CODE_GEN_LOG_FILE` in the `logs` folder for insights.

### File Format Issues

**Problem**: Generated files are not in the expected format.

**Solution**:
1. Review the `file_format` and `file_format_diff` preprompts in the codebase.
2. Ensure your project requirements are clearly specified in the initial prompt.
3. If using custom preprompts, verify they're correctly formatted and placed in the `preprompts` folder.

## Configuration Issues

### Custom Preprompts Not Applied

**Problem**: Your custom preprompts are not being used.

**Solution**:
1. Ensure you're using the `--use-custom-preprompts` flag:

```python
python -m gpt_engineer.main project_directory --use-custom-preprompts
```

2. Verify that your custom preprompts are in the correct location (project_directory/preprompts).
3. Check file names and content format match the original preprompts.

### Model Selection Issues

**Problem**: Unable to use a specific AI model.

**Solution**:
1. Use the `--model` flag to specify your desired model:

```python
python -m gpt_engineer.main project_directory --model gpt-4-turbo
```

2. For Azure, ensure you've set the correct deployment name and endpoint.
3. Verify that you have access to the specified model in your OpenAI account.

## Execution Environment Problems

### Entrypoint Execution Failures

**Problem**: The generated entrypoint script fails to execute.

**Solution**:
1. Review the generated entrypoint script (usually named `run.sh`).
2. Ensure all dependencies are correctly installed.
3. Check execution permissions:

```bash
chmod +x run.sh
```

4. If using a custom execution environment, verify it's correctly implemented and configured.

### Dependency Installation Issues

**Problem**: Required dependencies fail to install.

**Solution**:
1. Check the generated requirements file or installation commands.
2. Ensure you have necessary system-level dependencies (e.g., python-dev, build-essential).
3. If using a virtual environment, make sure it's activated before installation.
4. For complex projects, consider using a containerized environment (e.g., Docker).

## Performance and Resource Issues

### High Token Usage

**Problem**: Projects are consuming more tokens than expected.

**Solution**:
1. Use the `TokenUsageLog` to monitor token consumption:

```python
print("Total api cost: $ ", ai.token_usage_log.usage_cost())
```

2. Consider using smaller models for initial drafts and gpt-4 for refinement.
3. Optimize prompts to be more concise while maintaining clarity.

### Slow Code Generation

**Problem**: Code generation is taking longer than expected.

**Solution**:
1. Use the `--use_cache` flag to enable LLM response caching:

```python
python -m gpt_engineer.main project_directory --use_cache
```

2. For large projects, break them down into smaller, manageable components.
3. Consider using `lite_mode` for quicker, less detailed generations:

```python
python -m gpt_engineer.main project_directory --lite
```

If you continue to experience issues after trying these solutions, please check the [GitHub repository](https://github.com/AntonOsika/gpt-engineer) for known issues or to report a new problem. Remember to include relevant log files and a detailed description of your setup when seeking help.
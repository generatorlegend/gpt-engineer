# Writing Effective Prompts for GPT-Engineer

## Introduction

This guide provides best practices and examples for writing effective prompts when using gpt-engineer. Well-crafted prompts are crucial for obtaining the best results from the AI-powered code generation system.

## Understanding the Prompt Structure

The gpt-engineer system uses a `Prompt` class to handle user inputs. This class has the following key attributes:

- `text`: The main content of the prompt (required)
- `image_urls`: Optional dictionary of image URLs
- `entrypoint_prompt`: An optional additional prompt for specifying the entry point

## Best Practices for Writing Prompts

1. **Be Specific and Detailed**
   Provide as much information as possible about the desired functionality, architecture, and any specific requirements.

   Example:
   ```
   Create a Python web scraper that extracts product information from an e-commerce website. The scraper should handle pagination, use async requests for improved performance, and store the data in a SQLite database.
   ```

2. **Use Clear and Concise Language**
   Avoid ambiguity and use precise terminology to describe your requirements.

   Example:
   ```
   Implement a RESTful API using Flask for a todo list application. Include CRUD operations for tasks, user authentication using JWT, and proper error handling.
   ```

3. **Specify the Technology Stack**
   If you have preferences for specific frameworks, libraries, or tools, mention them explicitly in your prompt.

   Example:
   ```
   Create a React Native mobile app for tracking daily water intake. Use Redux for state management, AsyncStorage for local data persistence, and integrate with a Firebase backend for user account synchronization.
   ```

4. **Include Desired Output Format**
   Mention any specific file structure, naming conventions, or code style preferences you have.

   Example:
   ```
   Generate a Node.js Express server with TypeScript. Follow the MVC pattern, use ESLint for code linting, and include a Dockerfile for containerization. Organize the project structure with separate directories for models, controllers, and routes.
   ```

5. **Specify Any External Dependencies**
   If your project requires integration with external services or APIs, include this information in your prompt.

   Example:
   ```
   Build a weather dashboard using Vue.js that fetches data from the OpenWeatherMap API. Implement geolocation for automatic location detection and allow users to search for weather information by city name.
   ```

6. **Request Documentation and Tests**
   If you need inline documentation or unit tests, explicitly mention this in your prompt.

   Example:
   ```
   Create a Python library for parsing and manipulating CSV files. Include comprehensive docstrings for all public methods, generate Sphinx documentation, and write pytest unit tests with at least 80% code coverage.
   ```

## Examples of Effective Prompts

### Web Application

```
Develop a full-stack web application for a recipe sharing platform using the MERN stack (MongoDB, Express, React, Node.js). Implement user authentication, CRUD operations for recipes, a search functionality with filters, and a responsive design. Use Redux for state management in the frontend and Mongoose for database modeling in the backend. Include proper error handling and input validation on both client and server sides.
```

### Command-Line Tool

```
Create a Python command-line tool for bulk image processing. The tool should accept input and output directories as arguments, support operations like resizing, cropping, and applying filters, and allow for batch processing of multiple images. Use the Pillow library for image manipulation, argparse for handling command-line arguments, and implement proper logging and error handling. Package the tool using setuptools for easy distribution.
```

### Mobile Application

```
Develop a cross-platform mobile app for habit tracking using Flutter. Implement features such as daily habit check-ins, streak tracking, progress visualizations, and customizable reminders. Use Provider for state management, SQLite for local data storage, and Firebase for user authentication and cloud sync. Design the UI following Material Design guidelines and ensure the app works offline with data syncing when a connection is available.
```

## Conclusion

By following these guidelines and using detailed, specific prompts, you can maximize the effectiveness of gpt-engineer and obtain high-quality code generation results. Remember to review and test the generated code to ensure it meets your requirements and standards.
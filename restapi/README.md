# `fabric`

...

## REST API

This REST API is part of the Fabric project, which provides various endpoints to interact with the Fabric system. The API is built using the Gin framework and includes endpoints for managing chat sessions, configurations, contexts, models, patterns, and sessions.

### Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Endpoints](#endpoints)
  - [Chat](#chat)
  - [Configuration](#configuration)
  - [Contexts](#contexts)
  - [Models](#models)
  - [Patterns](#patterns)
  - [Sessions](#sessions)
- [Contributing](#contributing)
- [License](#license)

### Installation

To install and run the Fabric REST API, follow these steps:

1. Clone the repository:
```markdown
    ```sh
    git clone https://github.com/iMelki/fabric.git
    ```

2. Navigate to the project directory:
    ```sh
    cd fabric/restapi
    ```

3. Install the dependencies:
    ```sh
    go mod download
    ```

4. Run the application:
    ```sh
    go run main.go
    ```

### Usage

To use the Fabric REST API, you can send HTTP requests to the endpoints defined in the API. Below are examples of how to interact with the API using `curl`.

### Endpoints

#### Chat

- **POST /chat**
  - **Description:** Submit chat prompts for processing.
  - **Example:**
     ```sh
     curl -X POST http://localhost:8080/chat \
       -H "Content-Type: application/json" \
       -d '{
         "prompts": [
           {
             "userInput": "Hello, how are you?",
             "vendor": "openai",
             "model": "gpt-3.5-turbo",
             "contextName": "default",
             "patternName": "greeting"
           }
         ],
         "temperature": 0.7,
         "topP": 1.0,
         "frequencyPenalty": 0.0,
         "presencePenalty": 0.0
       }'
     ```

#### Configuration

- **GET /config**
  - **Description:** Retrieve the current configuration settings.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/config
     ```

- **POST /config/update**
  - **Description:** Update the configuration settings.
  - **Example:**
     ```sh
     curl -X POST http://localhost:8080/config/update \
       -H "Content-Type: application/json" \
       -d '{
         "openai_api_key": "new_openai_key",
         "anthropic_api_key": "new_anthropic_key",
         "groq_api_key": "new_groq_key",
         "mistral_api_key": "new_mistral_key",
         "gemini_api_key": "new_gemini_key",
         "ollama_url": "new_ollama_url",
         "openrouter_api_key": "new_openrouter_key",
         "silicon_api_key": "new_silicon_key"
       }'
     ```

#### Contexts

- **GET /contexts**
  - **Description:** Retrieve a list of all contexts.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/contexts
     ```

- **GET /contexts/:name**
  - **Description:** Retrieve a specific context by name.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/contexts/exampleContext
     ```

- **GET /contexts/names**
  - **Description:** Retrieve names of all contexts.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/contexts/names
     ```

- **GET /contexts/exists/:name**
  - **Description:** Check if a specific context exists.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/contexts/exists/exampleContext
     ```

- **POST /contexts/:name**
  - **Description:** Create or update a specific context.
  - **Example:**
     ```sh
     curl -X POST http://localhost:8080/contexts/exampleContext \
       -H "Content-Type: application/json" \
       -d '{
         "key": "value"
       }'
     ```

- **DELETE /contexts/:name**
  - **Description:** Delete a specific context by name.
  - **Example:**
     ```sh
     curl -X DELETE http://localhost:8080/contexts/exampleContext
     ```

- **PUT /contexts/rename/:oldName/:newName**
  - **Description:** Rename an existing context.
  - **Example:**
     ```sh
     curl -X PUT http://localhost:8080/contexts/rename/oldContext/newContext
     ```

#### Models

- **GET /models/names**
  - **Description:** Retrieve a list of all model names.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/models/names
     ```

#### Patterns

- **GET /patterns**
  - **Description:** Retrieve a list of all patterns.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/patterns
     ```

- **GET /patterns/:name**
  - **Description:** Retrieve a specific pattern by name.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/patterns/examplePattern
     ```

- **GET /patterns/names**
  - **Description:** Retrieve names of all patterns.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/patterns/names
     ```

- **GET /patterns/exists/:name**
  - **Description:** Check if a specific pattern exists.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/patterns/exists/examplePattern
     ```

- **POST /patterns/:name**
  - **Description:** Create or update a specific pattern.
  - **Example:**
     ```sh
     curl -X POST http://localhost:8080/patterns/examplePattern \
       -H "Content-Type: application/json" \
       -d '{
         "pattern": "new_pattern_content"
       }'
     ```

- **DELETE /patterns/:name**
  - **Description:** Delete a specific pattern by name.
  - **Example:**
     ```sh
     curl -X DELETE http://localhost:8080/patterns/examplePattern
     ```

- **PUT /patterns/rename/:oldName/:newName**
  - **Description:** Rename an existing pattern.
  - **Example:**
     ```sh
     curl -X PUT http://localhost:8080/patterns/rename/oldPattern/newPattern
     ```

#### Sessions

- **GET /sessions**
  - **Description:** Retrieve a list of all sessions.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/sessions
     ```

- **GET /sessions/:name**
  - **Description:** Retrieve a specific session by name.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/sessions/exampleSession
     ```

- **GET /sessions/names**
  - **Description:** Retrieve names of all sessions.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/sessions/names
     ```

- **GET /sessions/exists/:name**
  - **Description:** Check if a specific session exists.
  - **Example:**
     ```sh
     curl -X GET http://localhost:8080/sessions/exists/exampleSession
     ```

- **POST /sessions/:name**
  - **Description:** Create or update a specific session.
  - **Example:**
     ```sh
     curl -X POST http://localhost:8080/sessions/exampleSession \
       -H "Content-Type: application/json" \
       -d '{
         "sessionData": "new_session_data"
       }'
     ```

- **DELETE /sessions/:name**
  - **Description:** Delete a specific session by name.
  - **Example:**
     ```sh
     curl -X DELETE http://localhost:8080/sessions/exampleSession
     ```

- **PUT /sessions/rename/:oldName/:newName**
  - **Description:** Rename an existing session.
  - **Example:**
     ```sh
     curl -X PUT http://localhost:8080/sessions/rename/oldSession/newSession
     ```

### Contributing

We welcome contributions to the Fabric project. To contribute, follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Make your changes.
4. Submit a pull request.

### License

This project is licensed under the MIT License. See the [LICENSE](../LICENSE) file for details.
```
### Testing

To run the tests, execute:

```sh
go test ./...
```

### Troubleshooting

If you encounter issues, check the logs for error messages and ensure all dependencies are installed correctly. For further assistance, please open an issue on the repository.

### Contact

For any questions or support, please contact [your.email@example.com](mailto:your.email@example.com).
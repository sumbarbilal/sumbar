

# English Chat Apps
This is an AI assistant application designed specifically for learning English. It aims to provide a comprehensive and interactive learning experience for users who want to improve their English language skills. The application uses advanced AI technologies to facilitate engaging and effective language learning through various interactive features.

## TechStack

English Chat App System uses a number of technology stack to work properly:
- [node.js] - Runtime for the lambda function
- [NextJS] - Progressive, incrementally-adoptable JavaScript framework
- [APIGateway] - Fast and modern bundler for building frontend apps.
- [Cognito] - asdasd
- [PostgresQL] - Powerful, open-source, relational database.

<hr>

## Font-End Setup
The root folder for Front-End projects is **client-apps**.
### Front-End Environment Variable

```sh
AUTH_SECRET="GENERATE_RANDOM_STRING_SECRET"
AUTH_URL="http://localhost:3000/"
NEXT_PUBLIC_COGNITO_CLIENT_ID="YOUR_COGNITO_APPS_CLIENT_ID"
NEXT_PUBLUC_COGNITO_ID_TOKEN_EXPIRED="YOUR_COGNITO_ID_TOKEN_EXPIRED_IN_MINUTES"
NEXT_PUBLIC_API_GATEWAY_URL="YOUR_API_GATEWAY_URL"
```

### Project Setup

```sh
npm install
```

#### Compile and Hot-Reload for Development

```sh
npm run dev
```

#### Type-Check, Compile and Minify for Production

```sh
npm run build
```

You can use **check page** (`http://FRONTEND_HOST/check`) to check connection to backend endpoint, you need to sign in to access this endpoint.
<hr>

## Backend Setup

### API Endpoint
You can read API Endpoint spesification for `/conversations` on **API Gateway** in Document detail.

### **LLM API Endpoint**
> ### List Models
```sh
GET /api/tags
```
List models that are available in LLM server. **Example Request** :
```sh
curl http://SERVER_HOST:11434/api/tags
```

> ### Pull Models
```sh
POST /api/pull
```
Download a model from the ollama library. Cancelled pulls are resumed from where they left off, and multiple calls will share the same download progress.

#### Parameters
- `name`: name of the model to pull
- `insecure`: (optional) allow insecure connections to the library. Only use this if you are pulling from your own library during development.
- `stream`: (optional) if `false` the response will be returned as a single response object, rather than a stream of objects
#### Example Request
```sh
curl http://SERVER_HOST:11434/api/pull -d '{
  "name": "orca-mini"
}'
```

> ### Generate Embedding
```sh
POST /api/embed
```
Generate embeddings from a model

### Parameters
- `model`: name of model to generate embeddings from
- `input`: text or list of text to generate embeddings for

#### Example Request
```sh
curl http://localhost:11434/api/embed -d '{
  "model": "nomic-embed-text",
  "input": "Why is the sky blue?"
}'
```
# ML Web Server

This is a simple web server built with Hapi.js that serves a machine learning model using TensorFlow.js. The server allows users to upload an image, and it predicts whether the image represents "rock", "paper", or "scissors" based on the trained model.

## Features

- **Upload an image**: Users can upload an image via a `POST` request to the `/predicts` endpoint.
- **Model prediction**: The server uses a pre-trained TensorFlow.js model to classify the uploaded image into one of three categories: "rock", "paper", or "scissors".
- **Model file storage**: The model is stored in the `models` folder and is loaded into the server at runtime.

## Technologies Used

- [Hapi.js](https://hapi.dev/): Web framework for building the server.
- [TensorFlow.js](https://www.tensorflow.org/js): JavaScript library for training and running machine learning models in the browser and Node.js.
- [Node.js](https://nodejs.org/): JavaScript runtime used for server-side development.

## Setup

To get started with this project locally, follow these steps:

### 1. Clone the repository

```bash
git clone https://github.com/your-username/ml-web-server.git
```

### 2. Install dependencies

```bash
cd ml-web-server
npm install
```
   
### 3. Prepare the model files:

Make sure to place the model files (from your trained model) in the models directory. The required files are:

- `group1-shard1of7.bin`
- `group1-shard2of7.bin`
- `group1-shard3of7.bin`
- `group1-shard4of7.bin`
- `group1-shard5of7.bin`
- `group1-shard6of7.bin`
- `group1-shard7of7.bin`
- `model.json`

### 4. Run the application

To start the server in development mode, run:

```bash
npm run start
```

For production mode, use:

```bash
npm run start-prod
```

The server will start at `http://localhost:3000`.

### 5. Test the model prediction endpoint

Send a `POST` request to `/predicts` with a file upload:

```bash
curl -X POST http://localhost:3000/predicts -F "image=@path/to/your/image.jpg"
```
The response will return the prediction result:

```json
{
  "result": "rock"
}
```

## Folder Structure

```markdown
- models/
  - group1-shard1of7.bin      # Model file parts
  - group1-shard2of7.bin
  - group1-shard3of7.bin
  - group1-shard4of7.bin
  - group1-shard5of7.bin
  - group1-shard6of7.bin
  - group1-shard7of7.bin
  - model.json                # Model metadata
- src/
  - app.js                    # Hapi.js server configuration
  - inference.js              # TensorFlow.js inference functions
- .gitignore                  # Git ignore file
- package.json                # Project metadata and dependencies
- README.md                   # Project documentation
```

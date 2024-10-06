# Egg Classification Project

This project demonstrates how to classify different types of eggs using a machine learning model deployed on Roboflow. The classification is based on images of eggs, showcasing how to utilize the Roboflow API for inference in a Python environment.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Important Note on API Key](#important-note-on-api-key)
- [Contributing](#contributing)
- [License](#license)

## Overview

Eggs can vary in appearance based on various factors. This project uses a trained model to classify eggs into several categories, including:
- White Egg
- Brown Egg
- Dirt Stain Egg
- Blood Stain Egg
- Calcium Deposited Egg

## Features
- Classifies images of eggs using a machine learning model.
- Utilizes Roboflow's API for inference.
- Secure handling of API keys with environment variables.

## Requirements
- Python 3.x
- Jupyter Notebook
- `python-dotenv` for managing environment variables
- `inference-sdk` for interacting with the Roboflow API

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/AmaanAhmad2025/Egg_Classification.git
   ```

2. Navigate to the project directory:
   ```bash
   cd Egg_Classification
   ```

3. Install required packages:
   ```bash
   pip install python-dotenv inference-sdk
   ```

4. Create a `.env` file in the project directory and add your Roboflow API key:
   ```plaintext
   ROBLOFLOW_API_KEY=your_api_key_here
   ```

## Usage

1. Place the image you want to classify in the project directory.
2. Open the Jupyter Notebook (`egg_classification.ipynb`).
3. Run the notebook cells to perform inference on the image.
4. The predicted classes for the eggs will be displayed as output.

## How It Works

- The project uses the `dotenv` library to load environment variables from a `.env` file, ensuring that sensitive information like the API key is not hard-coded into the scripts.
- The image file is sent to the Roboflow model using the `InferenceHTTPClient`.
- The predicted classes for the eggs are retrieved and presented as the output of the inference process.

## Contributing

Contributions are welcome! If you have suggestions for improvements, please feel free to fork the repository, make your changes, and submit a pull request.

## License

This project is licensed under the MIT License. See the LICENSE file for more information.

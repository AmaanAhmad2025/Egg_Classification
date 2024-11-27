# Egg Classification using Roboflow API

## Overview

This project uses the Roboflow API to classify images of eggs into different categories (e.g., White Egg, Brown Egg, Dirt Stain Egg, Blood Stain Egg, Calcium Deposited Egg). The project loads an image, performs classification using a machine learning model hosted on Roboflow, visualizes the prediction with bounding boxes and confidence scores, and saves the annotated image.

## Requirements

Before running the code, ensure you have the following dependencies installed:

1. Python 3.x
2. `opencv-python`
3. `numpy`
4. `matplotlib`
5. `python-dotenv`
6. `inference_sdk`
7. `requests` (for API calls)

You can install the necessary libraries using pip:

```bash
pip install opencv-python numpy matplotlib python-dotenv requests inference_sdk
```

## Setup Instructions

1. **Get your Roboflow API Key:**
   - Sign up or log in to [Roboflow](https://roboflow.com/).
   - Create or use an existing project for egg classification.
   - Obtain your API key from the Roboflow Dashboard.

2. **Create a `.env` file:**
   In your project directory, create a `.env` file and add the following content:

   ```bash
   ROBLOFLOW_API_KEY=your_roboflow_api_key
   ```

   Replace `your_roboflow_api_key` with your actual Roboflow API key.

## Code Walkthrough

### 1. Loading Environment Variables

```python
from dotenv import load_dotenv

load_dotenv()  # Loads environment variables from the .env file
```

This loads the API key stored in the `.env` file.

### 2. Initialize the Roboflow Client

```python
from inference_sdk import InferenceHTTPClient

api_key = os.getenv("ROBLOFLOW_API_KEY")

CLIENT = InferenceHTTPClient(
    api_url="https://detect.roboflow.com",
    api_key=api_key
)
```

Here, we initialize the `InferenceHTTPClient` with the Roboflow API URL and API key.

### 3. Image Inference

```python
result = CLIENT.infer(r"C:\path_to_image\Capture.jpg", model_id="egg-classification-xppva/4")
```

The `infer` function sends an image to the Roboflow API for classification, and returns a prediction result.

### 4. Image Processing and Visualization

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load and annotate the image
image = cv2.imread(image_path)
# Perform object detection and draw a rectangle around the egg
cv2.rectangle(image, (x1, y1), (x2, y2), color, thickness)
# Annotate with prediction
cv2.putText(image, text, (text_x, text_y), font, font_scale, color, font_thickness)

# Display image with Matplotlib
plt.imshow(image_rgb)
plt.axis('off')
plt.title("Egg Classification")
plt.show()
```

This section uses OpenCV to load the image, draw a bounding box, and annotate the detected egg type and confidence score. The image is displayed using Matplotlib.

### 5. Save Annotated Image

```python
output_path = r"C:\Users\Hp\Desktop\Capture_Annotated.jpg"
cv2.imwrite(output_path, image)
print(f"Annotated image saved at {output_path}")
```

After the prediction and annotation, the image is saved to the specified path.

## Running the Code

1. Ensure that your `.env` file is properly set up with the correct Roboflow API key.
2. Run the script, making sure to update the image path to point to the local image you want to classify.
3. The script will perform the inference, draw bounding boxes, display the image, and save the annotated result.

## Notes

- Ensure that the `model_id` corresponds to the correct project in Roboflow.
- This code assumes you are working with egg images. If you are working with a different dataset, you will need to update the model and prediction handling code accordingly.
- You can modify the code to handle more complex visualizations, such as multiple predictions or different annotation styles.

## License

This project is open-source and available under the MIT License. Feel free to fork and modify the code.


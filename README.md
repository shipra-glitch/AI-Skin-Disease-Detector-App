# AI-Skin-Disease-Detection-App
# SkinScan - AI Skin Disease Detection Application

SkinScan is a desktop-based application designed to detect skin diseases from images using machine learning and provide intelligent guidance using a large language model. The system integrates computer vision, deep learning, and conversational AI to assist users in understanding potential skin conditions and recommended next steps.

---

## 1. Overview

The application allows users to either upload an image or capture one using a webcam. The image is processed through a trained TensorFlow Lite model to classify the skin condition. Based on the prediction and confidence score, the system provides structured suggestions, including symptoms, home care, and when to seek medical attention.

An integrated chat assistant enables users to describe symptoms in natural language and receive AI-generated responses for additional guidance.

---

## 2. Key Features

- Image-based skin disease detection using a trained machine learning model  
- Real-time image capture using webcam integration (OpenCV)  
- Upload support for multiple image formats (JPG, PNG, BMP)  
- Confidence score visualization for predictions  
- AI-powered assistant for symptom-based interaction  
- Structured medical guidance including:
  - Condition overview  
  - Symptoms  
  - Home care recommendations  
  - When to consult a doctor  
- Fallback system using predefined suggestions if AI service is unavailable  
- Scan history tracking with timestamps  

---

## 3. Technology Stack

### Frontend
- JavaFX (UI framework)
- FXML (layout design)
- CSS (styling)

### Backend
- Java (application logic)
- Maven (build and dependency management)

### Machine Learning
- TensorFlow Lite model for classification
- Python script for inference execution

### Computer Vision
- OpenCV for webcam integration

### AI Integration
- Groq API (LLM-based response generation)

---

## 4. Project Structure

SKIN_DISEASE_DETECT/

src/main/java/com/example/skindisease/
- App.java  
- MainController.java  
- CameraController.java  
- ChatController.java  
- ChatService.java  
- GeminiService.java  
- PythonClassifier.java  
- SuggestionHelper.java  
- SymptomData.java  
- ChatMessage.java  

resources/com/example/skindisease/
- main.fxml  
- chat.fxml  
- camera.fxml  
- styles.css  

models/
- skin_model.tflite  
- labels.txt  

predict.py  
pom.xml  

---

## 5. Installation and Setup

### Prerequisites

- Java Development Kit (JDK 17 or later)  
- Maven  
- Python 3.x  
- Required Python libraries:
  - tensorflow  
  - numpy  
  - pillow  
- OpenCV (Java binding)  

---

### Steps to Run

1. Clone the repository:
git clone https://github.com/shipra-glitch/AI-Skin-Disease-Detector-App.git  
cd skin-disease-detect  

2. Set the API key:

On Windows (PowerShell):
setx GROQ_API_KEY "your_api_key_here"  

Restart your IDE after setting the variable.

Alternatively, you can temporarily hardcode the key in ChatService.java and GeminiService.java for testing.

3. Build the project:
mvn clean install  

4. Run the application:
mvn javafx:run  

---

## 6. How It Works

1. The user selects or captures an image.  
2. The image is passed to a Python script (predict.py).  
3. The TensorFlow Lite model processes the image and returns:
   - Predicted disease  
   - Confidence score  
   - Top predictions  
4. The Java application displays the result.  
5. The detected condition is sent to the AI service for structured suggestions.  
6. If the AI service fails, predefined suggestions are used as fallback.  

---

## 7. Model Details

The skin disease classification model used in this application is based on the MobileNet architecture, a lightweight convolutional neural network optimized for efficient image classification tasks. The model has been converted to TensorFlow Lite format for faster inference and integration within the application.

### Supported Classes

- Acne  
- Actinic Keratosis  
- Basal Cell Carcinoma  
- Chickenpox  
- Dermatofibroma  
- Dyshidrotic Eczema  
- Melanoma  
- Nail Fungus  
- Nevus  
- Normal Skin  
- Pigmented Benign Keratosis  
- Ringworm  
- Seborrheic Keratosis  
- Squamous Cell Carcinoma  
- Vascular Lesion  

### Model Characteristics

- Architecture: MobileNet  
- Format: TensorFlow Lite (.tflite)  
- Input: Preprocessed skin image  
- Output:
  - Predicted class label  
  - Confidence score  
  - Top predictions  

### Notes

- Performance depends on image quality, lighting, and dataset diversity.  
- Some visually similar conditions may result in misclassification.  

---

## 8. API Integration

The application uses the Groq API for generating responses.

- Endpoint:  
  https://api.groq.com/openai/v1/chat/completions  

- Model (recommended):  
  llama-3.1-8b-instant  

- Request format follows OpenAI-compatible messages structure.  

---

## 9. Limitations

- Predictions depend on the quality and training of the model  
- Not all skin conditions are covered  
- AI responses are informational and not clinically verified  
- Requires internet connection for AI features  

---

## 10. Disclaimer

This application is intended for educational and research purposes only. It is not a medical diagnostic tool. Users should consult a qualified dermatologist for professional diagnosis and treatment.

---

## 11. Author

Shipra Prashanth  
B.E. Student with interests in Artificial Intelligence, Machine Learning, and Full Stack Development  

---

## 12. Future Improvements

- Improve model accuracy with larger datasets  
- Add support for more skin conditions  
- Deploy as a web or mobile application  
- Enable real-time video-based detection  
- Integrate cloud-based model inference  
- Add user authentication and data storage  

# Cloud devops learing journey -Day 49
Date:27.08.25

## 🔹 AWS AI & ML Overview

Amazon Web Services (AWS) provides a wide range of cloud-based AI and ML tools. They are broadly divided into:

Pre-trained AI Services (No ML expertise required)

Directly use APIs for AI tasks like vision, speech, language, recommendations, etc.

ML Services (Build, train, and deploy models)

For developers and data scientists who want more control.

ML Frameworks & Infrastructure (For experts)

Deep learning frameworks (TensorFlow, PyTorch, MXNet, etc.) with scalable infrastructure.

##  1. Pre-Trained AI Services (API-based)
These are ready-made AI services you can integrate without building your own model:

Amazon Rekognition – Image & video analysis (face detection, object recognition, moderation).

Amazon Polly – Text-to-speech (convert text into lifelike speech).

Amazon Transcribe – Speech-to-text (transcribe audio files).

Amazon Translate – Language translation.

Amazon Comprehend – NLP (analyze text, sentiment, entity recognition).

Amazon Lex – Build chatbots (like Alexa).

Amazon Textract – Extract text & data from documents (OCR).

Amazon Personalize – Personalized recommendations (like Netflix/Amazon product recommendations).

Amazon Forecast – Time-series forecasting (sales, demand prediction).

Amazon Kendra – Intelligent search across enterprise data.

## 2 ML Services
For developers and data scientists to build ML models:

Amazon SageMaker – End-to-end ML service:

Build, train, tune, and deploy ML models.

Provides Jupyter notebooks, AutoML, and model monitoring.

Integrates with frameworks like TensorFlow, PyTorch, and Scikit-learn.

Amazon SageMaker Autopilot – AutoML (build models automatically from data).

Amazon SageMaker Studio – Web-based IDE for ML development.


 ##  ML Frameworks & Infrastructure
For ML experts needing high-performance computing:

AWS Deep Learning AMIs – Preconfigured VMs with TensorFlow, PyTorch, MXNet.

AWS Inferentia – Custom chip for ML inference (faster predictions).

AWS Trainium – Custom chip for training ML models at scale.

Elastic Inference – Attach GPU acceleration at lower cost.

🔹 Example Use Cases
Healthcare → Detect diseases from medical images (Rekognition + SageMaker).

E-commerce → Personalized recommendations (Personalize).

Banking → Fraud detection (Forecast + SageMaker).

Education → Auto-translate learning material (Translate + Polly).

Customer Support → Smart chatbots (Lex + Comprehend).

⚡ In short:

Just want AI features? → Use pre-trained AI APIs.

Want to build ML models? → Use SageMaker.

Need custom deep learning? → Use frameworks + infrastructure.
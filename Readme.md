# 🌊 Water-Borne Diseases Outbreak Detection

A prototype system for **early detection of water-borne disease risks** using AI + real-time monitoring.  
This project combines a **machine learning model** (hosted on [Hugging Face Spaces](https://huggingface.co/spaces)) with **Firebase** for data storage, alerts, and notifications.  

---

## 🚀 Prototype Workflow
1. **User Input**  
   - A simple **web form** (GitHub Pages frontend) allows users to enter water quality parameters  
     *(e.g., pH, turbidity, dissolved oxygen, E. coli count, etc.)*.  
   - Submitted values are stored in **Firebase Realtime Database**.  

2. **Model Inference**  
   - Every **5 seconds**, the model (running on Hugging Face Spaces) fetches the latest data from Firebase.  
   - It produces a **risk score** and classifies the entry as **LOW / MEDIUM / HIGH** risk.  

3. **Alerts**  
   - Results are written back to Firebase.  
   - If risk ≥ MEDIUM, the system triggers **real-time notifications** via Firebase Cloud Messaging (FCM).  

4. **Visualization**  
   - The GitHub-hosted dashboard displays submitted data and prediction results.  
   - Updates are automatic — no manual refresh required.  

---

## 🏗️ System Architecture
```mermaid
flowchart LR
    A[User Form (GitHub Pages)] -->|Submits data| B[Firebase Database]
    B -->|Data Fetch (5s)| C[AI Model - Hugging Face Spaces]
    C -->|Predictions| B
    B --> D[Notifications (FCM)]
    B --> E[Web Dashboard (GitHub Pages)]
```
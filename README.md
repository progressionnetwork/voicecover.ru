# voicecover.ru
This repository contains the model card and API specifications for the Voicecover AI Video Translation tool. The service offers advanced features for translating videos into multiple languages, complete with voice cloning and lip synchronization.

---
license: apache-2.0
language:
- en
- ru
- it
- tr
---

# Voicecover AI Launches Video Translation Tool

Voicecover AI has introduced an AI-powered video translation tool that features voice cloning and lip sync capabilities. This platform enables creators to translate videos into 14 languages, including Arabic, Mandarin, and Spanish, while matching the speaker's lip movements to the translated audio.

This tool aims to reduce localization costs for businesses in marketing, entertainment, and social media. Voicecover's proprietary model, Localizer v3, powers this feature, which is accessible through Voicecover Studio and its API.

A model card repository for the video-to-video translation model and API specifications for web service usage will be available soon. Videos can range from 10 seconds to 55 minutes, with a maximum file size of 2GB, and work best with a single subject facing the camera.

### API Specification for Video Translation Service

#### Overview
The Voicecover API allows developers to integrate video translation capabilities into their applications, enabling seamless localization and voice cloning.

#### Base URL
```
https://api.voicecover.ai/v1
```

#### Authentication
- **Method:** Bearer Token
- **Header:** `Authorization: Bearer <your_access_token>`

#### Endpoints

1. **Translate Video**
   - **Endpoint:** `/translate`
   - **Method:** POST
   - **Description:** Submits a video for translation.
   - **Request Body:**
     ```json
     {
       "video_url": "string",
       "target_languages": ["string"],
       "voice_cloning": true,
       "lip_sync": true
     }
     ```
   - **Response:**
     ```json
     {
       "job_id": "string",
       "status": "pending"
     }
     ```

2. **Check Translation Status**
   - **Endpoint:** `/status/{job_id}`
   - **Method:** GET
   - **Description:** Retrieves the status of a translation job.
   - **Response:**
     ```json
     {
       "job_id": "string",
       "status": "completed",
       "download_url": "string"
     }
     ```

3. **Get Supported Languages**
   - **Endpoint:** `/languages`
   - **Method:** GET
   - **Description:** Lists all supported translation languages.
   - **Response:**
     ```json
     {
       "languages": ["string"]
     }
     ```

#### Rate Limits
- **Requests:** 100 requests per minute
- **Video Length:** Up to 55 minutes
- **File Size:** Max 2GB

---

### Model Specification for Video Translation

#### Model Name
**Localizer v3**

#### Model Type
- **Architecture:** Deep Learning (Convolutional Neural Networks for video, Recurrent Neural Networks for audio)

#### Input Specifications
- **Video Format:** MP4, AVI, MOV
- **Audio Format:** AAC, MP3
- **Resolution:** Up to 1080p

#### Output Specifications
- **Translated Video:** MP4 format with synchronized audio and lip movements
- **Supported Languages:** 30 languages including Arabic, Mandarin, Japanese, Hindi, Spanish, and French

#### Performance Metrics
- **Translation Accuracy:** 95% (based on internal benchmarks)
- **Lip Sync Accuracy:** 90% (measured against human dubbing)

#### Use Cases
- Marketing videos
- Educational content
- Entertainment localization

#### Limitations
- Supports only one subject in the frame
- Best results with face fully visible and facing the camera

---

This specification provides a comprehensive overview of the API and model functionalities for integrating and utilizing the Voicecover video translation service.

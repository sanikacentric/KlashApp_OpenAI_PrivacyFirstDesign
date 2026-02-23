# KlashApp — OpenAI Privacy-First Design

A privacy-first AI application built using OpenAI APIs, demonstrating how to architect GenAI applications with data minimization, PII protection, zero-retention policies, and on-premise/private deployment patterns.

## Description

As AI applications handle increasingly sensitive user data, privacy-first design becomes a core architectural requirement rather than an afterthought. This repository demonstrates how to build the KlashApp using OpenAI APIs while adhering to privacy-by-design principles: no storing of user inputs, PII detection before API calls, data minimization, and transparent user consent.

## Features

- **PII Detection & Redaction** — Scan user inputs for personally identifiable information before sending to OpenAI
- - **Zero Data Retention Mode** — Configure the application to not log or store any user conversations
  - - **Data Minimization** — Only send the minimum necessary context to the LLM API
    - - **User Consent Management** — Explicit opt-in/opt-out controls for data processing
      - - **Anonymization Pipeline** — Replace PII with pseudonymous tokens before API calls, then de-anonymize responses
        - - **Audit Trail** — Privacy-preserving audit logs that record actions without capturing content
          - - **OpenAI Zero Data Retention API** — Use OpenAI's ZDR endpoints for enterprise privacy compliance
            - - **On-Premise Deployment Option** — Architecture patterns for hosting LLMs locally instead of using cloud APIs
             
              - ## Privacy Architecture
             
              - ```
                User Input
                    ↓
                [PII Detection Layer]
                  - Email, phone, SSN, names detection
                    ↓
                [Anonymization]
                  - Replace PII with tokens: {USER_EMAIL_1}, {USER_NAME_1}
                    ↓
                [OpenAI API Call] (ZDR endpoint)
                  - Anonymized prompt sent
                    ↓
                [De-anonymization]
                  - Restore original PII in response (client-side only)
                    ↓
                [Zero Storage]
                  - No logs, no persistence
                    ↓
                User Response
                ```

                ## Tech Stack

                | Component | Technology |
                |---|---|
                | Language | Python 3 |
                | LLM API | OpenAI GPT-4 / GPT-3.5 |
                | PII Detection | Presidio / spaCy NER |
                | Framework | FastAPI / Flask |
                | Notebook | Jupyter (Google Colab) |

                ## Setup Instructions

                ### Prerequisites

                - Python 3.8+
                - - OpenAI API key (with zero data retention if available)
                 
                  - ### Installation
                 
                  - ```bash
                    git clone https://github.com/sanikacentric/KlashApp_OpenAI_PrivacyFirstDesign.git
                    cd KlashApp_OpenAI_PrivacyFirstDesign
                    pip install openai presidio-analyzer presidio-anonymizer spacy jupyter
                    python -m spacy download en_core_web_lg
                    ```

                    ### Configuration

                    ```bash
                    export OPENAI_API_KEY=your-openai-api-key
                    ```

                    ### Running the Notebook

                    ```bash
                    jupyter notebook
                    ```

                    ## Privacy Compliance

                    This design pattern supports compliance with GDPR Article 25 (Data Protection by Design and by Default), CCPA, and HIPAA privacy requirements for AI-powered applications.

                    ## License

                    Open source — for educational and privacy engineering purposes.

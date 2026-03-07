# PRD: DISE AI Agent (Style 1: Clean Pro)

## 1. Product Overview
DISE AI Agent is a precision analysis platform for Drug-Induced Sleep Endoscopy (DISE). It provides ENT physicians with quantitative, AI-driven data to standardize airway obstruction diagnosis and evaluate therapeutic options.

## 2. Background & Problem Statement
The clinical evaluation of obstruction sites during sleep endoscopy currently relies on subjective manual interpretation. This subjectivity leads to reporting variability, making it difficult for physicians to establish a consistent baseline for clinical diagnosis and subsequent treatment planning.

## 3. Target Users
ENT physicians and sleep specialists who require objective, pixel-level metrics to enhance the accuracy of clinical examinations and patient diagnostic reports.

## 4. Goals & Success Metrics (KPIs)
- **Diagnostic Consistency**: Standardize severity reporting via objective VOTE grading across different clinicians.
- **Efficiency**: Reduce the time required for quantitative video review by 70%.
- **Treatment Accuracy**: Provide a higher-fidelity data foundation for non-surgical and surgical treatment evaluation.

## 5. User Flow
1. **Video Ingestion**: User uploads the endoscopic recording (MP4).
2. **Analysis Window**: User defines a specific 10-90s segment for detailed scanning.
3. **Anatomical Selection**: AI prompts the user to focus on either the Velum (V) or Oropharynx (O) site.
4. **Automated Analysis**: AI segments the lumen and calculates obstruction area percentages.
5. **Validation (Conditional Loop)**: 
    - AI results are presented with Max/Min area images and VOTE scores.
    - **Correction**: If the user identifies anatomical tracking errors, they manually adjust anchor points. The system sends data to the AI model to generate updated Max/Min area images, obstruction percentage data (%), and VOTE scores.

## 6. User Stories
- **As a Physician**, I want the AI to calculate the exact VOTE score (0/1/2) automatically, **so that** I have an objective metric for patient diagnosis.
- **As a Clinical Specialist**, I want to manually override AI-generated polygons *only when necessary*, **so that** the final diagnostic report remains 100% accurate despite video quality variance.

## 7. Functional Requirements
- **VOTE Scoring Engine**:
    - **Level 0 (<50%)**: Normal or mild obstruction.
    - **Level 1 (50-75%)**: Moderate obstruction.
    - **Level 2 (>75%)**: Severe obstruction.
- **Optional Interactive Correction**: Toolset for manual vertex manipulation of AI-generated segmentation masks.
- **AI Model Comparison**: Following anchor point adjustment, data is sent to the AI model for comparison to provide updated Max/Min area images, obstruction percentage data (%), and VOTE scores.

## 8. Non-Functional Requirements
- **Clinical Constraints**: Hard limit of 10s minimum and 90s maximum for any single analysis task.
- **Security**: Medical-grade encryption for all processed video data and patient-related metrics.

## 9. Edge Cases
- **Occluded View**: The AI model considers this state as having no reference basis (no reference).

## 10. Risks & Assumptions
- **Video Pre-requisite**: Assumes standard endoscopic lighting and resolution for initial AI landmark detection.

## 11. Out of Scope
- Real-time live video processing or automated generation of clinical billing codes.

# Technical Specification: DISE AI Agent (Style 2: Blueprint)

## 1. System Vision
A quantitative diagnostic analysis engine designed to standardize VOTE grading for sleep endoscopy examinations.

## 2. Technical Focus
Transitioning from subjective "visual estimation" to objective "pixel-area calculation" to support clinical diagnosis and treatment evaluation.

## 3. User Personas
Otolaryngologists and Sleep Specialists focused on high-accuracy diagnostic workflows.

## 4. Key Metrics & Standards
- **Severity Standard**: VOTE Classification mapping (0: <50%, 1: 50-75%, 2: >75%).
- **Operational Window**: 10s - 90s per analysis segment.
- **Latency**: < 200ms for mask recalculation during interactive refinement.

## 5. Logic Flow
- **Step 1: Upload**: POST `/api/v1/clinical-ingest` (MP4/MOV).
- **Step 2: Configuration**: Set window `[t1, t2]` where `t2-t1` is between 10s and 90s.
- **Step 3: Site Selection**: User response to AI prompt for localized analysis (V-site vs O-site).
- **Step 4: AI Analysis**: U-Net based lumen segmentation and VOTE score derivation.
- **Step 5: Clinical Validation (Optional)**: 
    - Default: Physician confirms AI-generated result.
    - Override: If AI confidence is low, user toggles manual refinement mode to shift vertices.
    - Recalculate: Instant update of Max/Min areas upon polygon commit.

## 6. Functional Requirements
- `REQ-GRAD-01`: Automatic VOTE grading based on cross-sectional area reduction.
- `REQ-IMG-01`: Display and export of Max/Min area frames with overlaid segmentation masks.
- `REQ-UI-01`: Interactive vertex manipulation toolset available as a conditional override.

## 7. Non-Functional Specifications
- **Data Privacy**: Medical-grade (HIPAA compliant) encryption or local processing.
- **Performance**: Scan completion time proportional to segment duration (<2x video length).

## 8. Error Handling (Edge Cases)
- `ANATOMY_LOSS`: Prompt user for manual ROI definition if AI loses tracking of the airway.

## 9. Assumptions & Constraints
- Only supports MP4/MOV formats.
- Limited to Velum and Oropharynx sites in Version 1.

## 10. Non-Goals
- Automated surgical robotics integration or long-term longitudinal patient data tracking.

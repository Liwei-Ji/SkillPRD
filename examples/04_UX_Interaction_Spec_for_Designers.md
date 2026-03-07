# UX Specification: DISE AI Agent (Style 4: UX Spec)

## 1. UX Mission: Diagnostic Speed & Clinical Accuracy
The interface is designed to support a rapid diagnostic workflow while maintaining clinical oversight of AI-generated metrics.

## 2. Operative Sequence (Examination Flow)
1. **Intake**: Drag-and-drop clinical video files.
2. **Setup**: Selection of timeframe (Min 10s, Max 90s) to focus the analysis.
3. **Directed Analysis**: AI Agent interacts with the physician to select the target anatomical site (Velum vs. Oropharynx).
4. **Data Visualization**: 
   - Visual display of Max and Min obstruction frames.
   - Obstruction percentage data (%).
   - Categorization of severity via VOTE scores (0/1/2).
5. **Quality Control (Optional Correction)**:
   - If the AI analysis is affected by recording quality, the physician activates manual mode.
   - Physician adjusts anchor points; the system sends data to the AI model for comparison and provides updated Max/Min area images, obstruction percentage data (%), and VOTE scores.

## 3. Interaction Principles
- **Clarity over Clutter**: Prioritize high-fidelity area images and the final score.
- **AI Model Feedback**: Following anchor point adjustment, data is sent to the AI model for comparison to provide updated Max/Min area images, obstruction percentage data (%), and VOTE scores.
- **Review over Repetition**: The AI handles the bulk of the work; the human focus is solely on final validation.

## 4. Visual States
- **Scanning State**: Dynamic progress indicator during video segmentation. If occluded, the AI model identifies the state as having no reference basis.
- **Grading Feedback**: Color-coded indicators for VOTE scores (Green, Amber, Red).
- **Edit Mode**: Active visual cues when anchor points are being adjusted.

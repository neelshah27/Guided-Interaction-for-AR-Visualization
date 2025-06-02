# Guided-Interaction-for-AR-Visualization
> **Confidential – DO NOT SHARE OR DISTRIBUTE (for re-submission only)**  

![To be resubmiited | Do Not Share or Distribute](https://img.shields.io/badge/To_be_resubmitted–Do_Not_Share_or_Distribute-red)
![Code will be released soon](https://img.shields.io/badge/Code_will_be_released_soon-yellow)

---
## Demo Video

[![Watch the 5-minute demo](https://img.youtube.com/vi/FWT4_I4quno/0.jpg)](https://youtu.be/FWT4_I4quno)  


## Overview  
ViaLab is a mobile AR prototype enabling guided, collaborative exploration of high-dimensional data. Across three interactive modes—Scatterplot, t-SNE, and 3D Model—users can place, annotate, and revisit “bookmarks” in AR space, manage occlusion, and receive scagnostic-driven guidance on viewpoints of interest. Bookmarks and session reports can be exported (JSON/PDF) to support asynchronous collaboration and provenance tracking .

## Features  
1. **Multi-Mode AR Visualization** :  
   - **Scatterplot Mode**: Renders 3D scatterplots (e.g., Adult Mortality dataset) with interactive point selection, ring-based viewing history, and scagnostic highlights of informative attribute pairs .  
   - **t-SNE Mode**: Displays 3D t-SNE projections (e.g., MNIST) where users can rotate, scale, and annotate clusters; up to 12 color classes distinguish different groups :  
   - **3D Model Mode**: Loads arbitrary 3D models (e.g., bicycle), allowing users to annotate design features and receive expert training guidance .  

2. **Guided Exploration & Provenance**   
   - **Bookmarks**: Capture device pose (position + orientation) and attach semi-transparent screenshots plus text/audio notes. Each bookmark is visualized as a “viewing cone” guiding the user back to the exact angle :  
   - **Ring-Based Viewing History**: Encodes 360° of explored angles using 3600 spheres around the visualization; spheres fade when visited, while scagnostic-suggested segments glow orange to highlight potential insights.  
   - **Export/Import**: Serialize bookmarks to JSON for sharing; generate PDF session reports (via PDFKit) containing all bookmarks, annotations, and scagnostic summaries to facilitate cross-device collaboration.

3. **Occlusion Management & Interaction**   
   - **Tap/Scrub-to-Hide**: Tapping a data point reduces its transparency to resolve occlusion; “scrub-to-hide” allows sliding across multiple points to hide them rapidly.  
   - **Pan/Zoom/Rotate**:  
     - **Panning**: Horizontal panning moves the visualization left/right; vertical panning changes behavior depending on device pitch (translate vs. move toward/away).  
     - **Rotation**: Buttons enable horizontal and vertical rotation to access difficult viewing angles (e.g., top-down).  
     - **Pinch-to-Scale**: Pinch gestures scale visualizations up/down for closer inspection. 

## Implementation Details  
- **Platform & Frameworks**
  - **iOS (iPhone/iPad)** using **Swift**, **ARKit** (for plane detection), and **SceneKit** (for 3D rendering).  
  - **Data Preprocessing**: Python (scikit-learn) for t-SNE embeddings and Power Transform normalization; R (scagnostics) to compute scatterplot diagnostics offline. 
  - **Metadata & Reporting**: Bookmarks serialized as JSON; session reports generated via **PDFKit** include embedded screenshots and metadata for offline sharing.   

- **Data Sets & Models**
  - **Adult Mortality**: Countries colored by continent; attributes: Adult Mortality Rate (X), Body Mass Index (Y), GDP (Z).  
  - **MNIST (10% sample)**: 1,000 handwritten digits reduced to 3D via t-SNE.  
  - **3D Model**: Publicly available off-road bicycle mesh.  

- **Expert Evaluation & Feedback**  
  - Pilot sessions with Mathematics (t-SNE/Scatterplot) and HCI (3D Model) PhD experts.  
  - Quantitative logging of interaction events (e.g., rotation angles, bookmark revisit times).  
  - Updates: Added “scrub-to-hide” and selective transparency strategies to address occlusion; batched SceneKit rendering to sustain 60 FPS on iPad.  

## Demo  
A **5-minute video demonstration** is included. It showcases:  
1. Loading a data set (CSV) into Scatterplot Mode.  
2. Using scagnostic-driven ring segments to locate an anomalous cluster.  
3. Creating a bookmark with text annotation and revisiting it.  
4. Exploring t-SNE Mode annotations (imported JSON bookmarks).  
5. Viewing and annotating the 3D bicycle model, then exporting a session report.  
 



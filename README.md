
# Bayesian Optimisation for CTA Button Color
**Course:** ELEC-E7852 – Computational Design and Interaction  
**Assignment:** A2a – Bayesian Optimisation  
**Student:** Varun Sangwan  
**Student Number:** 101768733

---

## Overview
This project applies **Bayesian Optimisation (BO)** to a **user-centered interface design problem**: finding the optimal color for a **Call To Action (CTA)** button on a website hero section.  
The optimisation is performed **with a designer in the loop**, where human feedback directly guides the optimisation process.

The goal is to identify a button color that maximizes visibility, visual appeal, and user engagement while maintaining harmony with surrounding UI elements.

---

## Problem Context
The CTA button is located prominently in the **hero section** of a webpage.  
Color choice is critical because it affects:
- Visibility and contrast
- Readability
- User attention
- Click-through likelihood

Color selection is inherently subjective and multi-dimensional (RGB / hue, saturation, lightness), making **Bayesian Optimisation** a suitable approach.

---

## Why Bayesian Optimisation?
Bayesian Optimisation is well-suited for this task because:
- The search space is continuous and large (RGB color space)
- Evaluations are expensive and subjective (human feedback)
- It efficiently balances **exploration** (trying new colors) and **exploitation** (refining promising ones)
- It converges faster than random search

---

## Methodology

### Designer-in-the-Loop Setup
- A UI component containing:
  - Heading
  - Subheading
  - CTA Button
- Background: White
- Heading color: Fixed blue (to add contrast challenge)
- CTA color: Variable (RGB)

The designer rates each proposed color on a **1–5 suitability scale**, where higher scores indicate better visual performance.

---

### Objective Function
- Input: RGB color values
- Output: Designer suitability score (1–5)
- The score is inverted internally to allow maximization within the BO framework

---

### Optimisation Framework
- **Library Used:** `GPyOpt`
- **Model:** Gaussian Process (GP)
- **Acquisition Function:** Expected Improvement (EI)

Expected Improvement was chosen because it:
- Encourages exploration of new colors
- Exploits colors with higher previous ratings

---

## Optimisation Process
1. Initialize Bayesian Optimiser with RGB bounds
2. Generate a CTA color suggestion
3. Render the UI using `matplotlib`
4. Collect designer feedback (1–5 rating)
5. Update the Gaussian Process model
6. Repeat for multiple iterations
7. Plot acquisition function progress after 5 samples

---

## Visualisation
- UI renderings for each iteration show evolving CTA colors
- Acquisition function plots illustrate improvement over time
- Graphs display:
  - Iteration number
  - Negative suitability score
  - Convergence trend

---

## Results
- The optimiser consistently improved suitability scores over iterations
- Early iterations explored diverse colors
- Later iterations focused on high-performing color regions
- The final selected CTA color received the **highest suitability score**
- The method required significantly fewer trials than random search

---

## Comparison to Random Search
Compared to a random color search approach:
- Faster convergence
- Fewer evaluations needed
- More stable improvement
- Better integration of human feedback

---

## Final Outcome
- A visually effective CTA button color was identified
- The solution balances contrast, readability, and aesthetic appeal
- Demonstrates successful human–AI collaboration

---

## Limitations
- Highly subjective preferences may not converge to a single “best” color
- Designer feedback variance can affect optimisation stability
- Bayesian Optimisation may struggle when no universally optimal solution exists

---

## Technical Notes
- Initial attempt using `botorch` failed due to library issues
- Switched to `GPyOpt` after further study
- The change did not affect conceptual validity of the approach

---

## Conclusion
This project demonstrates that **Bayesian Optimisation with a human-in-the-loop** is an effective strategy for subjective design problems.  
It reduces experimental cycles, incorporates real-time feedback, and outperforms random search in efficiency and convergence—making it well-suited for UI/UX optimisation tasks.

---

## Files
- `Assignment 2a.pdf` – Detailed report and figures
- `Bayesian Optimisation.ipynb` – Implementation notebook
- `README.md` – Project summary (this file)


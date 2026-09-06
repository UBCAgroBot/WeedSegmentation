# Plant Instance Segmentation

## Goal

Build a model that detects and segments individual plants in images, producing a separate mask for each plant. The model should distinguish between crops and weeds and work well enough for the output to be used by the AgroBot simulation platform.

## Starting point

Two papers to read first:

* **Accurate fine-grained weed instance segmentation amidst dense crop canopies using CPD-WeedNet**, 2025. [Paper](https://www.frontiersin.org/journals/plant-science/articles/10.3389/fpls.2025.1632684/full)
* **Zero-shot Hierarchical Plant Segmentation via Foundation Segmentation Models and Text-to-image Attention**, Xing et al., WACV 2026. [Paper](https://openaccess.thecvf.com/content/WACV2026/html/Xing_Zero-shot_Hierarchical_Plant_Segmentation_via_Foundation_Segmentation_Models_and_Text-to-image_WACV_2026_paper.html)

Not blueprints to copy, its just a starting point for how people have approached plant segmentation.

## Model paths

There are several possible directions for solving the problem. Some starting points are:

* **Mask R-CNN**: a classic instance segmentation approach.
* **YOLO segmentation**: a more modern approach designed with speed in mind.
* **Transformer-based segmentation models**: a more advanced direction worth exploring.
* **SAM / foundation models**: newer models that can be adapted for segmentation tasks.

You **do not** need to try all of these. Pick an approach that makes sense for the problem and focus on making it work well.

## Project premise

The main challenge is not simply getting a model to segment plants. The model should work with difficult field conditions such as:

* Overlapping plants
* Partial occlusion
* Different plant sizes
* Similar-looking crops and weeds
* Different lighting conditions

The final system should be able to take an image, produce individual plant masks, identify crops and weeds, and provide a useful target for the AgroBot simulation.

## Definition of done

By the end of the core project, the team should be able to show:

* A working instance segmentation model that produces a separate mask for each plant.
* The model correctly distinguishing between crops and weeds, with appropriate segmentation metrics reported.
* An analysis of how the model performs on difficult cases such as overlapping or partially hidden plants.
* The trained model successfully onboarded and running in the simulation platform, with a short recorded demo.

## Timeline

* **9 weeks** (you are free to split it up as you wish)

### General example (you are free to modify):

1. **Foundations:** Environment + sim access set up, papers read, dataset found and plant classes/problem scope chosen.
2. **Build:** Instance segmentation pipeline built and a first working model trained and evaluated.
3. **Improve & apply:** Investigate difficult cases, improve the model, and onboard it into the simulation platform.
4. **Wrap-up:** Final testing, error analysis, polish, final report and demo ready.

### 12-week extension

If you are powering ahead, use the extra time to make the system more robust rather than starting a separate project. For example, you could explore:

* Better handling of overlapping and occluded plants.
* Generalizing to different fields, lighting, or plant growth stages.
* Using simulation data to improve performance on real images.
* Improving the model's speed and reliability for robotic use.

# dataset-ErrP-coadaptation

**Dataset: Human-agent co-adaptation using error-related potentials (ErrP)**

This repository contains the dataset accompanying the publication:

> **Ehrlich, S. K., & Cheng, G. (2018).**  
> *Human-agent co-adaptation using error-related potentials.*  
> **Journal of Neural Engineering, 15, 066014.**  
> https://doi.org/10.1088/1741-2552/aae069

The dataset supports research on **error-related potentials (ErrP)** as an implicit feedback signal for **interactive learning and co-adaptation** in human–robot interaction (HRI). The study demonstrates a two-party co-adaptive system where:

- the **human** adapts by learning to interpret the robot’s behavior, and  
- the **robot** adapts its policy using **ErrPs decoded online** from EEG as reinforcement feedback. 

---

## Repository structure

```text
dataset-ErrP-coadaptation/
├── data_coadaptation/        # open-loop calibration and closed-loop co-adaptation session data
│   ├── s03/                      
│   ├── s04/                       
│   └── ...
├── data_cursor/              # open-loop calibration and closed-loop co-adaptation session data
│   ├── s01/                      
│   ├── s02/                       
│   └── ...
├── Dataset documentation Co-adaptation.pdf            # protocol, variable definitions, file formats, markers
└── README.md
```

## Study description (brief)

### Human-agent co-adaptation task (NAO gaze-based guessing game)

**Purpose:** provide EEG recordings that enable analysis and decoding of **observed error-related potentials (ErrP)** in a human–robot interaction scenario where **mutual adaptation** is expected and required.

**Design:** A subject and a humanoid robot (**NAO**) repeatedly played a **guessing game**. In each trial, the robot covertly selected one of three objects (its intention/goal), then executed a **gaze pattern** (a sequence of head turns) toward objects and the participant. The human’s task was to infer which object the robot had selected based on its gaze behavior. The robot then revealed its choice via a perceptually salient **LED cue**, triggering either a **match (non-error)** or **mismatch (error)** response in the participant’s EEG.

The experiment consisted of two phases:
- **CALIB (open-loop calibration):** the robot gaze policy was fixed (non-adaptive) and designed to be relatively interpretable; false feedback was introduced to control error-event frequency.
- **CORL (closed-loop co-adaptation):** the robot gaze policy started as uniformly random and was updated trial-by-trial based on **online ErrP decoding**, yielding emergent robot behavior aligned with the human’s interpretation.

**Key technical properties relevant for dataset use:**
- **EEG:** 32 channels (actiChamp, Brain Products), **1024 Hz**, average mastoid reference (TP9/TP10), **EOG channels included**. 
- **Online classification:** rLDA using temporal mean features in several post-feedback windows.
- **Robot policy model:** probabilistic state policy over gaze states (selected object, other objects, human), updated using a reward from decoded ErrPs (**+1 non-error**, **−1 error**) with episode-based update strategy.

---

## About the dataset

### Intended use
This dataset supports research in:
- error-related potentials (ErrP) decoding and single-trial classification
- passive BCI as implicit feedback in HRI
- co-adaptation / interactive learning systems (human adapts + robot adapts)
- EEG-informed reinforcement learning and policy updates
- evaluation of robustness of ErrP decoding in realistic interaction paradigms

### Modalities and measures (overview)
Depending on the provided files and sessions, the dataset may include:
- **EEG recordings** (with EOG channels)
- trial-level **event markers** aligned to feedback onset (LED reveal)
- session metadata: **CALIB vs. CORL**, run index, trial index
- labels suitable for supervised learning: **error vs. non-error**
- logs of robot action sequences / gaze transitions and policy states (if exported)

For exact file formats, EEG montage, event codes, and label definitions, consult the repository documentation.

---

## Citation

```bibtex
@article{ehrlich2018coadaptation,
  title   = {Human-agent co-adaptation using error-related potentials},
  author  = {Ehrlich, Stefan K. and Cheng, Gordon},
  journal = {Journal of Neural Engineering},
  volume  = {15},
  pages   = {066014},
  year    = {2018},
  doi     = {10.1088/1741-2552/aae069}
}

# dataset-ErrP-coadaptation

**Dataset: Human-agent co-adaptation using error-related potentials (ErrP)**

This repository contains the dataset accompanying the publication:

> **Ehrlich, S. K., & Cheng, G. (2018).**  
> *Human-agent co-adaptation using error-related potentials.*  
> **Journal of Neural Engineering, 15, 066014.**  
> https://doi.org/10.1088/1741-2552/aae069 :contentReference[oaicite:1]{index=1}

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

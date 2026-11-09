# Automatic Background Person Removal

Undergraduate thesis project, B.Sc. in Computer Science and Engineering
**Khulna University of Engineering & Technology (KUET), Bangladesh**

- **Author:** Nakib Ahsan
- **Supervisor:** Abdul Aziz
- **Year:** 2025
- **Full report:** [`thesis_report.pdf`](https://drive.google.com/file/d/1cT2LA3cioCJJ1c_ERlLSmYHqf4Cejx5C/view?usp=sharing)

---

## Overview

Photos taken in crowded places often include unwanted people in the background. This project presents an automatic pipeline that detects every person in an image, identifies the **main (foreground) person**, and removes all **background persons**, filling the removed regions realistically.

The system combines three state-of-the-art models with custom logic for deciding who counts as the foreground person.

## Pipeline

```
Input image
    │
    ▼
1. Detection      YOLOv11 (fine-tuned on custom dataset)
    │             → bounding boxes for all persons
    ▼
2. Selection      Two custom algorithms
    │             → separate the foreground person from background persons
    ▼
3. Segmentation   SAM (Segment Anything Model)
    │             → precise masks for background persons
    ▼
4. Inpainting     LaMa
                  → removes masked regions and reconstructs the background
    ▼
Output image
```

| Stage | Method | Purpose |
|---|---|---|
| Detection | YOLOv11 | Locate all persons in the image |
| Foreground selection | Two custom algorithms | Decide which person is the subject |
| Segmentation | SAM | Generate accurate person masks |
| Inpainting | LaMa | Fill removed regions naturally |

## Dataset

- A **custom dataset of 771 images**, collected and annotated manually for this project.
- Used to fine-tune the YOLOv11 detector.
- Annotation format: [e.g., YOLO format / COCO]
- Train / validation / test split: [e.g., 70 / 20 / 10]
- Dataset link: [link, or "available on request"]

## Results

[Add your actual evaluation results here. Examples of what to include:]

| Metric | Value |
|---|---|
| Detection precision | [value] |
| Detection recall | [value] |
| mAP@0.5 | [value] |
| Foreground selection accuracy | [value] |

Sample outputs:

| Input | Output |
|---|---|
| ![input](./examples/input_1.jpg) | ![output](./examples/output_1.jpg) |


## Technologies

Python, PyTorch, YOLOv11 (Ultralytics), Segment Anything Model (SAM), LaMa, OpenCV, NumPy

## Limitations and Future Work

- [e.g., performance in very dense crowds or heavy occlusion]
- [e.g., inpainting quality on complex backgrounds]
- [e.g., real-time or video support]

## References

- Ultralytics YOLO11
- Kirillov et al., *Segment Anything*, 2023
- Suvorov et al., *Resolution-robust Large Mask Inpainting with Fourier Convolutions (LaMa)*, 2022

## Acknowledgements

Thanks to my supervisor Assisstant Professor Md. Abdul Aziz and the Department of Computer Science and Engineering, KUET, for their guidance and support.

## License

## Contact

Nakib Ahsan, ahsannakib335@gmail.com

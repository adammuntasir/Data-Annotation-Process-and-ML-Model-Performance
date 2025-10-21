# The Influence of Data Annotation Process Requirements on ML Model Performance

This repository contains the code and thesis document for a Bachelor of Science thesis exploring the impact of data annotation process requirements on the performance criteria of Machine Learning (ML) models. It is designed to allow recruiters to explore the topic and enable other researchers and practitioners to replicate the work.

## Table of Contents

*   [Project Overview](#project-overview)
*   [Key Takeaways](#key-takeaways)
*   [Thesis Document](#thesis-document)
*   [Codebase: `experiment_data_annotation_influence.ipynb`](#codebase-experiment_data_annotation_influenceipynb)
*   [How to Replicate the Experiments](#how-to-replicate-the-experiments)
    *   [Prerequisites](#prerequisites)
    *   [Step-by-step Replication](#step-by-step-replication)
*   [Folder Structure for Darknet](#folder-structure-for-darknet)
*   [Experimental Results and Visualizations](#experimental-results-and-visualizations)
*   [Future Work](#future-work)
*   [License](#license)
*   [Contact](#contact)

## Project Overview

The data annotation process is a critical step in the development of ML models. This thesis investigates how different data annotation process requirements influence ML model performance. Through experimental evaluation, it compares ML model performance using various annotated datasets and process requirements, utilizing metrics such as average precision, precision, recall, and F1-score. The findings highlight the substantial influence of annotation requirements on ML model performance, offering valuable insights for both academic research and industry practices.

## Key Takeaways

*   **Critical Role of Data Annotation:** The data annotation process is a fundamental and critical step in the development of effective Machine Learning models.
*   **Significant Impact on Performance:** Requirements imposed on the data annotation process have a substantial influence on the performance criteria of ML models, including metrics like average precision, precision, recall, and F1-score.
*   **Insights for Research and Industry:** The findings provide valuable insights for both academic researchers and industry professionals, emphasizing the importance of well-defined data annotation processes.
*   **Foundation for High-Performance Models:** Addressing the knowledge gap regarding the impact of annotation requirements is crucial for developing high-performance ML models.

## Thesis Document

The full thesis document, titled "The influence of data annotation process requirements on performance criteria of ML models," provides a detailed analysis of the research, methodology, results, and conclusions.

*   **[View Thesis PDF](Resources/CSE%2023-02%20MA%20MM.pdf)**

## Codebase: `experiment_data_annotation_influence.ipynb`

The `experiment_data_annotation_influence.ipynb` Jupyter Notebook contains the executable code used for the experimental evaluation. It demonstrates the process of:

*   **Environment Setup:** Cloning the Darknet repository and mounting Google Drive.
*   **Data Preparation:**
    *   Downloading the COCO dataset using FiftyOne.
    *   Generating various datasets with controlled parameters for size and label error rates.
    *   Splitting datasets into training, validation, and testing sets.
    *   Converting datasets to YOLOv4 format.
*   **Darknet Configuration:** Setting up `obj.data`, `yolo-obj.cfg`, and `yolo-obj-test.cfg` files.
*   **Model Training:** Training YOLOv4 models with different dataset configurations.
*   **Model Testing & Evaluation:** Evaluating trained models using various performance metrics.

The notebook is designed to be run in a Google Colab environment, leveraging its GPU capabilities for efficient model training.

## How to Replicate the Experiments

To replicate the experiments described in the thesis, follow these steps:

### Prerequisites

Before you begin, ensure you have:

*   A **Google Colab account** for running the Jupyter Notebook.
*   Basic understanding of **Python** and **Jupyter Notebooks**.
*   Familiarity with **object detection concepts** (e.g., YOLOv4, Darknet) is beneficial.

### Step-by-step Replication

1.  **Open the Jupyter Notebook:** Access `experiment_data_annotation_influence.ipynb` in a Google Colab environment.
2.  **Run Setup Cells:** Execute the initial cells to clone the Darknet repository, mount Google Drive (for saving/loading data), and install necessary libraries like FiftyOne.
3.  **Configure Dataset Parameters:** Modify variables such as `class_name`, `max_samples`, `size`, `resplit_precent`, and `error_rate` to generate datasets corresponding to the different experiments (E1, E2, E3) detailed in the thesis.
4.  **Prepare Data:** Run the cells for downloading, splitting, and converting the dataset to YOLOv4 format.
5.  **Configure Darknet Files:** Ensure the `obj.data` and `.cfg` files are correctly configured based on the number of classes and experiment parameters. The notebook includes commands to modify these files.
6.  **Download Pre-trained Weights:** Download the `yolov4.conv.137` pre-trained weights.
7.  **Build Darknet:** Compile Darknet with GPU and OpenCV enabled.
8.  **Train Models:** Execute the training command, specifying the paths to your `obj.data` and custom `.cfg` files.
    ```bash
    !./darknet detector train <path to obj.data> <path to custom config> yolov4.conv.137 -dont_show -map
    ```
    *   **Note:** For long training sessions in Colab, consider using the provided JavaScript snippet in the notebook to prevent disconnection due to inactivity.
9.  **Test Models:** After training, use the testing commands to evaluate the model's performance on the test dataset.
    ```bash
    !./darknet detector map <path to obj.data> <path to custom config> <path to weights file>
    ```
10. **Analyze Results:** Review the output metrics and visualizations generated during testing.

## Folder Structure for Darknet

The notebook assumes a specific folder structure for Darknet data. This is crucial for the scripts to function correctly.

```sh
data
├── obj.names
├── obj.data
├── train.txt
├── test.txt
├── obj
     ├── train
          ├── image1.jpg
          ├── image2.jpg
          ├── ...
     ├── test
          ├── image1.jpg
          ├── image2.jpg
          ├── ...
     ├── obj.data
     ├── obj.names
     ├── backup
          ├── yolov4_last.weights
          ├── ...
```

## Experimental Results and Visualizations

The `Images/` directory contains various plots and figures summarizing the experimental results, including:

*   AP and average IoU by Models (E1, E2, E3)
*   Precision, Recall, and F1-score by Models (E1, E2, E3)
*   Main performance indicators by Models

These visualizations provide a quick overview of the key findings from the experiments.

## Future Work

The thesis identifies several promising avenues for future research:

*   **Alternative ML Models:** Explore the performance of different object detection models (e.g., Faster R-CNN, SSD) under various data annotation scenarios to compare their robustness.
*   **Deeper Process Requirement Analysis:** Conduct further investigations into how specific process requirements impact model performance, aiming for a more granular understanding.
*   **Diverse Datasets:** Replicate experiments using alternative datasets beyond Microsoft COCO to assess the generalizability of the findings.
*   **Additional Scenarios:** Introduce new experimental scenarios to further explore the relationship between data annotation and ML model performance, potentially leading to more refined insights.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For any questions or further information, please contact:
*   **Muntasir Adam** (gusadammu@student.gu.se)
*   **Maab Mohammedali** (gusmaamo@student.gu.se)

# Project-3-DS-4002

Contains Project 3 Work for DS4002 Group 5 Fall 2026

Members: Inmar Chavarria (L), Angelika Baloy, Samuel Bromberg

## Classifying Paintings By Artistic Movement

We are using painting images collected from publicly available WikiArt: Visual Art Encyclopedia, which provides artwork organized by artist, artistic movement, and style.

WikiArt, “Artists by art movement,” WikiArt.org. [Online]. Available: https://www.wikiart.org/en/artists-by-art-movement.

## Software and Platform

- Software: Python 3 (`01_Paintings_Project_Dataset_Creation.ipynb`, `02_EDA_Paintings_Project.ipynb`, and `03_Analysis_Paintings_Project.ipynb`)
- Platform: Google Colab
- Python Version: Colab runtime; the version is not pinned in the notebooks

| Package | Version | Used for |
|---|---|---|
| pandas | 2.2.3 | Loading and organizing the painting metadata and model results |
| NumPy | 2.4.6 | Handling image labels, arrays, and numerical operations |
| Pillow | 11.3.0 | Opening, resizing, and saving painting images |
| PyTorch | 2.14.1+cpu | Creating datasets and training the ResNet-18 model |
| Torchvision | 0.29.1+cpu | Image transformations and pretrained ResNet-18 weights |
| scikit-learn | 1.6.1 | Grouped data splitting and model evaluation metrics |
| Matplotlib | 3.10.0 | Plotting class counts, training history, metrics, and confusion matrices |

## Documentation

This repository contains:

- `README.md`
  - Project overview, software and platform information, file locations, and instructions for reproducing the analysis.
- `LICENSE`
  - License information for the project.
- `Data/`
  - `README.md` describes the WikiArt dataset and links to the Google Drive folder containing the data files.
  - The dataset folder contains `wikiart_paintings.csv` and `wikiart_images_complete.zip`, which are used by the notebooks.
- `Scripts/`
  - `01_Paintings_Project_Dataset_Creation.ipynb` collects painting metadata and images.
  - `02_EDA_Paintings_Project.ipynb` explores the dataset and painting image dimensions.
  - `03_Analysis_Paintings_Project.ipynb` prepares the images, trains the ResNet-18 model, and evaluates its performance.
- `Outputs/`
  - `Conclusion.md` summarizes the analysis findings.
  - `class_counts_by_split.csv` and `class_counts_by_split.png` show the number of images in each movement across the data splits.
  - `model_comparison.csv` compares the baseline and trained model.
  - `training_history.csv` and `training_history.png` record and plot training performance.
  - `test_classification_report.csv` and `per_class_metrics.csv` contain test-set and per-class evaluation metrics.
  - `per_class_metrics.png` visualizes the per-class results.
  - `confusion_matrix_counts.png` and `confusion_matrix_normalized.png` show the model’s classification errors.
  - `test_predictions.csv` contains the model’s test-set predictions.
  - `confidence_by_correctness.png` compares prediction confidence for correct and incorrect predictions.
  - `prediction_examples.png` and `gradcam_example.png` provide visual examples of model predictions and image attention.

## File Locations

- `Data/`
  - `README.md` describes the WikiArt dataset, its fields, and data provenance.
  - `WikiArt Data` links to the Google Drive folder containing the dataset files used by the notebooks, including `wikiart_paintings.csv` and `wikiart_images_complete.zip`.
- `Scripts/`
  - `01_Paintings_Project_Dataset_Creation.ipynb` collects WikiArt painting metadata and images.
  - `02_EDA_Paintings_Project.ipynb` explores the dataset and image dimensions.
  - `03_Analysis_Paintings_Project.ipynb` cleans the images, creates artist-separated data splits, trains ResNet-18, and evaluates the model.
- `Outputs/` contains the saved analysis results, plots, and `Conclusion.md`. The notebook writes generated files to a local `Output/` folder in Colab; after downloading the output ZIP, place the extracted files in this repository folder.
- `LICENSE` contains the project license.
- `README.md` contains the project overview, file locations, and reproduction instructions.

## Instructions for Reproducing Results

Follow these steps to reproduce the full project, from collecting the data through evaluating the ResNet-18 model. If you are using the prepared CSV and image archive in `Data/WikiArt Data`, you can skip steps 1–7.

### Dataset creation

1. Access the first script in the `Scripts` folder: `01_Paintings_Project_Dataset_Creation.ipynb`. Open it in Google Colab or download it.

2. Read the description at the top of the notebook, titled “WikiArt Painting Dataset.” Run **code cell 1** to install the required dependencies.

3. **Imports and settings:** Run **code cell 2**. This loads the libraries, chooses the six movement classes, sets the per-class target to 100, and configures a two-second delay and automatic retries for temporary request failures.

4. **Find and select Artists:** Run **code cell 3** to find and select artists. Save the list so it is clear which artists were available to the image-collection pass.

5. **Define collection helpers:** Run **code cell 4**. These functions find artwork pages, read image, style, and medium metadata, filter for paintings, and save accepted images.

6. **Collect the full dataset once:** Run **code cell 5**. For each class, the notebook collects paintings from the selected artists until the target is reached or the available artist and artwork pages are exhausted. It saves the results as `wikiart_paintings.csv` and saves any request errors as `collection_errors.csv`.

7. **Package and download results:** Run **code cell 6** to create a ZIP archive containing the images referenced by the CSV, then download the artist list, painting metadata, and image archive from Colab. The creation notebook names its archive `wikiart_images.zip`. Before using it in the analysis notebook, rename it to `wikiart_images_complete.zip`, which is the filename expected by the analysis notebook.

### Exploratory data analysis

8. Access the second script in the `Scripts` folder: `02_EDA_Paintings_Project.ipynb`. Open it in Google Colab or download it.

9. Load the data from the previous steps by running **code cell 1**. This also imports the required packages and previews the data.

10. **Select a random painting:** Run **code cell 2** to display a randomly selected painting.

11. **Dataset overview:** Run **code cell 3** to display the dataset shape, column names, data types, missing values, duplicate rows, and duplicate image paths.

12. Run **code cell 4** to create a bar chart showing the number of paintings in each artistic movement.

13. **Image Dimensions and Aspect Ratios:** Run **code cell 5** to calculate the width, height, and aspect ratio of each painting.

14. **Image Dimension Distributions:** Run **code cell 6** to create plots of image widths, heights, and aspect ratios. These plots show why the images need consistent dimensions before model training.

### ResNet-18 analysis

15. Access `Scripts/03_Analysis_Paintings_Project.ipynb` and open it in Google Colab or download it.

16. Upload `wikiart_paintings.csv` and `wikiart_images_complete.zip` to the Colab session. The notebook expects these files at `/content/wikiart_paintings.csv` and `/content/wikiart_images_complete.zip`.

17. Run the **Imports** cell. It loads the packages used for image processing, ResNet-18 training, evaluation, and plotting, and creates an `Output` folder for generated results.

18. Run **Image & Data Cleaning**. This extracts the image archive, resizes readable images to 224 × 224 pixels, and removes images that cannot be opened. Expected output: 550 usable paintings and 0 unreadable images.

19. Run **Apply Training, Test, & Validation Splits to Data**. The notebook uses `StratifiedGroupKFold` to keep each artist in only one split. Review the resulting movement-by-split table and chart to see the class counts.

20. Run **Create PyTorch Dataset & DataLoader** to prepare image batches for training, validation, and testing. Then run **Establish Majority Class Baseline** to calculate the baseline test accuracy and macro-F1.

21. Run **Setup ResNet-18 Model for Analysis** and **Train ResNet-18 Model**. The notebook loads pretrained ImageNet weights, fine-tunes the final ResNet block and classifier, trains for 8 epochs, and keeps the model version with the highest validation accuracy.

22. Run the training-history cell after training. It saves the epoch-by-epoch metrics and plots training loss, validation accuracy, and validation macro-F1.

23. Run **Evaluate Best Version of the Model on the Untouched Test Set**. This reports test accuracy, macro-F1, and per-class results. It also saves the classification report, per-class metrics, test predictions, and count and normalized confusion matrices.

24. Run **Example Predictions** to display correct and incorrect test predictions. Then run the confidence plot and **Grad-CAM Visualization** cells to examine prediction confidence and the image regions associated with one model prediction.

25. Run **Final Model Comparison with Baseline** to compare ResNet-18 with the majority-class baseline.

26. Run **Download Outputs** to download `project3_outputs.zip`. Extract its files into the repository’s `Outputs/` folder. The notebook creates a Colab folder named `Output`; the repository folder is named `Outputs`.

The analysis outputs include `model_comparison.csv`, `per_class_metrics.csv`, `test_classification_report.csv`, `test_predictions.csv`, `training_history.csv`, `class_counts_by_split.csv`, and the corresponding plots. Training results may vary between runs because model initialization and training-batch order are not fixed.

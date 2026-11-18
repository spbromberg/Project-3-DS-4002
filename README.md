# Project-3-DS-4002

Contains Project 3 Work for DS4002 Group 5 Fall 2026

Members: Inmar Chavarria (L), Angelika Baloy, Samuel Bromberg

## Classifying Paintings By Artistic Movement

We are using painting images collected from publicly available WikiArt: Visual Art Encyclopedia, which provides artwork organized by artist, artistic movement, and style.

WikiArt, “Artists by art movement,” WikiArt.org. [Online]. Available: https://www.wikiart.org/en/artists-by-art-movement.

## Software and Platform
- Software: Python 3 (notebooks: [INSERT NAMES HERE])
- Platform: Google Colab
- Python Version: [INSERT VERSION HERE[

| Package | Version | Used for |
| ------- | ------- | ----------|
|         |          |          | 
|         |          |          |
|         |          |          | 
|         |          |           |

## Documentation

[INSERT DOCUMENTATION MAP HERE]

## File Locations

[INSERT FILE LOCATIONS HERE]

## Instructions for Reproducing Results

[INSERT INTRUCTIONS HERE: MAKE SURE TO INCLUDE SPECIFIC LOCATIONS, TABLES, CODE CELLS, TITLES, ETC. I RECOMMEND CLAUDE]
1. Access the first script in the scripts folder:
   01_Paintings_Project_Dataset_Creation.ipynb by opening the file in Google Colab or by downloading the file.
2. Read the description at the top of the notebook titled, "WikiArt Painting Dataset." Install dependencies by running **code cell 1**.
3. Imports and settings: Run **code cell 2**. This loads the libraries, chooses the six movement classes, and sets the per-class goal to 100. It also configures a polite two-second delay plus automatic retries for temporary request failures.
4. Find and select Artists: Run **code cell 3** to find and and select artists. Saving this list makes it clear which artists were available to the image-collection pass.
5. Define collection helpers: Run **code cell 4**. These functions find artwork pages, read the image/style/medium metadata, filter for paintings, and save each accepted image.
6. Collect the full dataset once: Run **code cell 5** to collect image data. For each class, walk through the selected artists and keep collecting until the target is reached or the available artist/work pages are exhausted. Save the one-pass results and any request errors for review. This creates a file named "wikiart_paintings.csv" in the output folder. Any errors are saved to "collection_errors.csv"
7. Package and download results: Run **code cell 6** to build a zip file containing only the image files referenced by the CSV, then download the artist list, painting metadata, and image archive from Colab. The zip created is named "wikiart_images.zip" in the output folder.

   


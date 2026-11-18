# DS4002 Project 3 Data: WikiArt Metadata

## Data Summary 
The data is collected from WikiArt: Visual Art Encyclopedia [1], which provides artwork organized by artist, artistic
movement, and style. The dataset contains 550 paintings across six categories: Renaissance, Baroque, Romanticism, 
Impressionism, Cubism, and "Other", which includes paintings from varying movements across history. The paintings 
were organized into a CSV file containing information such as painting titles, artist names, artistic movements, 
and image URLs. We will use the painting images for classification and the CSV labels to identify their correct 
artistic movements. 

## Provenance
Each observation represents one painting and includes its title, artist name, artistic movement, specific art style, 
medium, artwork URL, image URL, and local image path. The images will serve as the primary input for our CNN model, 
while the artistic movement labels will be used to train and evalluate its predictions. 

## License 
The painting images are publicly accessible through the WikiArt website. We wil use the images for educational and 
research purposes only while providing proper credit to WikiArt and the original artists. 

## Ethical Statements
Our data is open access and the paintingas are available in the public domain. Images are not bound by copyright and 
permission to use these images is not required. We will not be recreating any painter's work for this project, we will 
simply classify their works into art movements. 

## Data Dictionary 
| Feature | Type | Meaning | Uncertainty |
| --- | --- | --- | --- |
| Title | Categorical / string | The title of the artwork, as listed on WikiArt | Titles may have alternate translations or spellings |
| Artist Name | Categorical / string | The full name of the artist associated with the artwork | Based on WikiArt's attribution; could be incorrect |
| Artist Slug | Categorical / string | WikiArt's URL-friendly identifier for the artist | Present for all entries; useful for matching works to artists |
| Movement | Categorical / string | The dataset's class label (Renaissance, Baroque, Romanticism, Impressionism, Cubism, or Other | Artist-level label, not a classification for each individual artwork. "Other" combines several art movements | 
| Artwork Style | Categorical / string | WikiArt's assigned style or styles. Multiple styles are separated by semicolons | WikiArt metadata; only one record in CSV has no style listed | 
| Medium | Categorical / string | The materials listed for the artwork. Multiple mediums are separated by semicolons | Based on WikiArt metadata; may use inconsistent wording | 
| Artwork URL | URL string | The WikiArt webpage for the individual artwork | The link identifies the source page, but pages may change or become unavailable | 
| Image URL | URL string | The URL from which the image was downloaded | The image is hosted externally and may later move |
| Image Path | Categorical / string | The path to the downloaded image in the dataset folder | Usable when the image folder or ZIP is extracted with the same folder structure | 
| Image Archive | ZIP file | ZIP archive of downloaded artwork image files | Analysis must ensure that the ZIP images correspond to the CSV artworks | 

## Explanatory Plots 

<img width="989" height="390" alt="image" src="https://github.com/user-attachments/assets/048ec307-da7d-471d-bd4f-513ecad361d0" />

<img width="1589" height="390" alt="image" src="https://github.com/user-attachments/assets/3969b341-9d10-41b1-b44d-bed2172282b6" />

## References 

[1] 	 WikiArt, “Artists by art movement,” WikiArt.org. [Online]. Available: https://www.wikiart.org/en/artists-by-art-movement.

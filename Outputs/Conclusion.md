# Conclusion

This study used a dataset of 550 WikiArt paintings to classify artworks into six artistic movements: Baroque, Cubism, Impressionism, Other, Renaissance, and Romanticism. All 550 images were readable and resized for the analysis. We split the data by artist so that artists in the training, validation, and test sets did not overlap. This tested whether the model could classify paintings by artists it had not seen during training.

## Model results:

We trained a pretrained ResNet-18 model, fine-tuning its final layer and classifier. The model achieved its highest validation accuracy of 43.5% during training. On the held-out test set of 84 paintings, it achieved 40.5% accuracy and a macro-F1 score of 0.380. This was higher than the majority-class baseline, which achieved 6.0% accuracy and a macro-F1 score of 0.019 on the same test set. However, the model did not meet the project's initial goal of 85% accuracy.

Performance varied by movement. The model performed best on Impressionism, with an F1 score of 0.63, and had an F1 score of 0.53 for Renaissance. It did not correctly classify any of the seven test paintings labeled Other. Results for Baroque and Cubism should be interpreted cautiously because the test set contained only five Baroque paintings and three Cubist paintings. The uneven test-set counts also make the majority-class baseline a limited comparison.

Overall, ResNet-18 learned some useful visual patterns, but its test performance shows that classifying artistic movements remains difficult with this dataset and model. The results suggest that additional paintings, especially for underrepresented test classes, would help provide a more reliable evaluation.

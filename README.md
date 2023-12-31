# CosSIF: Cosine Similarity-based Image Filtering

Suppose we are presented with two categories of skin lesions: benign and malignant. Our objective is to sift out benign images that bear resemblance to malignant ones, and similarly, malignant images that bear resemblance to benign ones.

```python
from cossif import cossif
```

```python
csf = cossif.CosSIF()
```

```python
# Filter benign images
csf.calculate_and_filter(
    target_path=cls_benign,              # Path to the folder that contains benign images.
    secondary_path=cls_malignant,        # Path to the folder that contains malignant images.
    filtered_path=cls_benign_filtered,   # Path to the folder that will contain filtered benign images.
    removed_path=cls_benign_removed,     # Path to the folder that will contain removed benign images.
    record_save_path=save_path,          # Save path of the similarity calculation record.
    record_keep=False,                   # Chose whether to keep the similarity calculation record or not.
    file_name='t_benign_x_s_malignant',  # Name of the similarity calculation record file.
    filter_type='dissimilar',            # Type of filtering. Can be either "similar" or "dissimilar".
    filter_range=0.85,                   # The filtering ratio. A value of 0.85 means that 15% of the images will be removed.
)
```

<p align="left">
<img src="https://github.com/mominul-ssv/cossif-package/raw/main/plots/github/benign.png" alt="image_description" style="padding: 5px" width="100%">
</p>
<p align="left">
<img src="https://github.com/mominul-ssv/cossif-package/raw/main/plots/github/benign_filtered.png" alt="image_description" style="padding: 5px" width="100%">
</p>
<p align="left">
<img src="https://github.com/mominul-ssv/cossif-package/raw/main/plots/github/benign_removed.png" alt="image_description" style="padding: 5px" width="100%">
</p>

```python
# Filter malignant images
csf.calculate_and_filter(
    target_path = cls_malignant,
    secondary_path = cls_benign,
    filtered_path=cls_malignant_filtered,
    removed_path=cls_malignant_removed,
    record_save_path = save_path,
    record_keep=False,
    file_name = 't_malignant_x_s_benign',
    filter_type = 'similar',
    filter_range = 0.85,
)
```

<p align="left">
<img src="https://github.com/mominul-ssv/cossif-package/raw/main/plots/github/malignant.png" alt="image_description" style="padding: 5px" width="100%">
</p>
<p align="left">
<img src="https://github.com/mominul-ssv/cossif-package/raw/main/plots/github/malignant_filtered.png" alt="image_description" style="padding: 5px" width="100%">
</p>
<p align="left">
<img src="https://github.com/mominul-ssv/cossif-package/raw/main/plots/github/malignant_removed.png" alt="image_description" style="padding: 5px" width="100%">
</p>
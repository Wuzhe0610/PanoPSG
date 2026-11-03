# PanoPSG

English | [简体中文](README_zh-CN.md)

**High-resolution panoramic imagery for panoptic segmentation and panoptic scene graph generation.**

PanoPSG combines pixel-level scene annotations with semantic relations in equirectangular projection (ERP) panoramas. It brings together scene entities and their interactions within a full 360° observation, supporting research on panoramic scene parsing and relational understanding.

The dataset described in the accompanying manuscript contains **340 panoramas**, each at **11,968 × 5,984 pixels**, with **10,571 entity nodes** and **6,632 directed relation triplets**. The object vocabulary follows the 133-class COCO Panoptic taxonomy, of which 82 categories are observed, and relations use 21 predicate categories.

## Highlights

- **High-resolution 360° scenes.** Each panorama contains approximately 71.62 million pixels, providing detailed visual content across streets, campuses, parks, and related environments.
- **Panoptic scene representation.** Thing instances and stuff regions form the entity nodes of a shared scene representation.
- **Entity-linked semantic relations.** Directed subject–predicate–object triplets connect the annotated entities, with multiple predicates supported for an ordered pair.
- **Panoramic identity handling.** Source grouping links visible regions of an instance across the ERP left–right seam to one entity identity.
- **Manual annotation and review.** Trained annotators produced the annotations, followed by review of masks, relation endpoints, duplicate triplets, and mask–relation alignment.

## Dataset statistics

The following statistics describe the dataset reported in the manuscript.

| Property | Statistics |
| --- | ---: |
| ERP panoramas | 340 |
| Resolution per panorama | 11,968 × 5,984 |
| Pixels per panorama | 71.62 million |
| Predefined object categories | 133 |
| Observed object categories | 82 |
| Entity nodes | 10,571 |
| Directed relation triplets | 6,632 |
| Predicate categories | 21 |
| Mean nodes per panorama | 31.09 |
| Mean relations per panorama | 19.51 |
| Training / validation panoramas in the manuscript | 272 / 68 |

## Collection and annotation

Images were captured by the dataset creator. Blurred, duplicate, and incorrectly stitched images were excluded during collection curation.

Panoptic masks were manually annotated in CVAT. Recognizable regions were assigned object categories, while unrecognizable regions were marked as ignore. Same-category stuff regions are aggregated into one node per image. For a thing instance crossing the ERP seam, a shared source group links its visible parts to one entity and one segment ID.

A dedicated relation annotation platform associates mask regions with stable entity identities. Relations can connect thing–thing, thing–stuff, and stuff–stuff pairs. Spatial annotations refer to scene relationships, including interactions between entities that appear on opposite sides of the ERP image. All annotations underwent review, including checks of endpoint validity and consistency between segmented entities and relation endpoints.

## Data availability

**Only original images are being made public at this stage. All annotation files will be released after the paper is accepted**, including panoptic masks and metadata, relation annotations, category vocabularies, ID mappings, and data split lists.

| Component | Availability |
| --- | --- |
| Original ERP images | [Download from Alipan](https://www.alipan.com/s/TMgsspy42Cc), extraction code: `30qg` |
| Panoptic masks and accompanying JSON | To be released after paper acceptance |
| Relation annotations | To be released after paper acceptance |
| Category vocabularies, ID mappings, and split lists | To be released after paper acceptance |

The 340-image release list is provided in [image_files_340.txt](image_files_340.txt). The original images are distributed separately from the annotations.

## License and attribution

PanoPSG images and annotations are licensed under **Creative Commons Attribution 4.0 International (CC BY 4.0)**. See [LICENSE](LICENSE) and the [license summary](https://creativecommons.org/licenses/by/4.0/).

Use of licensed material requires appropriate credit, a license link, and an indication of changes. Suggested attribution: **PanoPSG dataset, Wuzhe0610**, with a link to [this repository](https://github.com/Wuzhe0610/PanoPSG).

## Contact

For dataset questions and feedback: **25600003160101@st.sdju.edu.cn**. GitHub Issues may also be used to report problems.

# PanoPSG

English | [简体中文](README_zh-CN.md)

**High-resolution panoramic imagery for panoptic segmentation and panoptic scene graph generation.**

PanoPSG combines pixel-level scene annotations with semantic relations in equirectangular projection (ERP) panoramas. Within a full 360° observation, panoptic masks describe the regions occupied by scene entities, while subject–predicate–object triplets describe semantic connections between those entities. The two annotation components share entity identities, linking image regions, scene nodes, and relational edges in a common representation.

This organization supports research on panoramic scene parsing and relational understanding. Panoptic segmentation addresses which entities are present and where their visible regions lie; scene graph generation extends that representation by describing how the entities relate to one another. PanoPSG brings these complementary descriptions together within the same panoramic scenes.

PanoPSG contains **340 panoramas**, each at **11,968 × 5,984 pixels**, with **10,571 entity nodes** and **6,632 directed relation triplets**. The object vocabulary follows the 133-class COCO Panoptic taxonomy, of which 82 categories are observed, and relations use 21 predicate categories. Together, the image content, entity masks, object labels, and semantic predicates describe both the spatial extent of scene entities and their connections within each panorama.

## Highlights

- **High-resolution 360° scenes.** Each panorama contains approximately 71.62 million pixels, providing detailed visual content across streets, campuses, parks, and related environments. The panoramic view places individual entities within their surrounding scene, combining local visual detail with the context available across the full view.
- **Panoptic scene representation.** Thing instances and stuff regions form the entity nodes of a shared scene representation. This includes both individual objects and broader scene regions, so the graph can connect different types of entities represented by the segmentation annotations.
- **Entity-linked semantic relations.** Directed subject–predicate–object triplets connect the annotated entities, with multiple predicates supported for an ordered pair. Relation endpoints refer to the same identities as the segmented entities, maintaining a direct correspondence between the graph and its image regions.
- **Panoramic identity handling.** Source grouping links visible regions of an instance across the ERP left–right seam to one entity identity. The visible parts can occupy separate regions of the rectangular image while remaining a single node in the scene representation.
- **Manual annotation and review.** Trained annotators produced the annotations, followed by review of masks, relation endpoints, duplicate triplets, and mask–relation alignment. These checks examine both the segmentation component and its correspondence with the relation annotations.

## Dataset statistics

Image-level quantities summarize the visual collection, node and triplet counts summarize the annotated scene graphs, and the category counts describe the object and predicate vocabularies used in those annotations.

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
| Training / validation panoramas | 272 / 68 |

## Collection and annotation

Images were captured by the dataset creator and organized as ERP panoramas at a common resolution of 11,968 × 5,984 pixels. The collection includes streets, campuses, parks, and related environments. During curation, blurred, duplicate, and incorrectly stitched images were excluded from the image collection used for the dataset.

Panoptic masks were manually annotated in CVAT. Recognizable regions were assigned object categories, while unrecognizable regions were marked as ignore. Thing annotations distinguish individual object instances, and same-category stuff regions are aggregated into one node per image. Each resulting node therefore connects a semantic category with its corresponding visible image region or regions.

For a thing instance crossing the ERP seam, a shared source group links its visible parts to one entity and one segment ID. This preserves a common identity when the rectangular ERP representation places the object's visible parts at opposite image boundaries. The segmentation representation and subsequent relation endpoints both refer to that same entity.

A dedicated relation annotation platform associates mask regions with stable entity identities. A relation is recorded by selecting a subject, a predicate, and an object from the corresponding scene entities. Relations can connect thing–thing, thing–stuff, and stuff–stuff pairs, and an ordered pair can carry multiple predicates. The resulting graph expresses semantic connections over the entities already described by the panoptic masks.

Spatial annotations refer to scene relationships, including relationships between entities that appear on opposite sides of the ERP image. Their interpretation follows the depicted scene rather than treating the rectangular image boundary as a physical separation. Stable entity identities keep relation endpoints associated with the intended segmented entities.

All annotations underwent review. Mask review examined the panoptic regions; endpoint checks examined whether relation subjects and objects referred to valid entities; duplicate-triplet checks identified repeated entries. Mask–relation alignment checks examined whether the graph endpoints corresponded to the intended segmented entities, bringing the two annotation components into the same review process.

## Data availability

**Only original images are being made public at this stage. All annotation files will be released after the paper is accepted**, including panoptic masks and metadata, relation annotations, category vocabularies, ID mappings, and data split lists. The table below distinguishes the material currently available for download from the annotation components scheduled for the later release.

| Component | Availability |
| --- | --- |
| Original ERP images | [Download from Alipan](https://www.alipan.com/s/TMgsspy42Cc), extraction code: `30qg` |
| Panoptic masks and accompanying JSON | To be released after paper acceptance |
| Relation annotations | To be released after paper acceptance |
| Category vocabularies, ID mappings, and split lists | To be released after paper acceptance |

The 340-image release list is provided in [image_files_340.txt](image_files_340.txt), allowing readers to identify the filenames included in the original-image collection. The images are distributed separately from the annotations. Use the Alipan link and extraction code above to access the currently public image files; the remaining components follow the release schedule stated in the table.

## License and attribution

PanoPSG images and annotations are licensed under **Creative Commons Attribution 4.0 International (CC BY 4.0)**. See [LICENSE](LICENSE) and the [license summary](https://creativecommons.org/licenses/by/4.0/).

Use of licensed material requires appropriate credit, a license link, and an indication of changes. Suggested attribution: **PanoPSG dataset, Wuzhe0610**, with a link to [this repository](https://github.com/Wuzhe0610/PanoPSG).

## Contact

For dataset questions and feedback: **25600003160101@st.sdju.edu.cn**. GitHub Issues may also be used to report problems.

# YOLOv11n Cat Classifier 


Custom YOLOv11n model for distinguishing between two cats (Mousse and Sherbert) as part of the Smart Cat Feeder project.
## Overview

This pipeline processes raw cat images/videos, generates training labels using a pretrained YOLO model, and trains a custom binary classifier to distinguish between two individual cats.
## Model Details

- **Base Model**: YOLOv11n (pretrained by Ultralytics)
- **Classes**: 2 (Mousse: 0, Sherbert: 1)
- **Training Images**: 1000+ labeled images
- **Train/Val Split**: 80/20
- **Image Size**: 640x640
- **Epochs**: 100
## Directory Structure
```
yolo-project/
├── datasets/
│   ├── input_images/          # Raw images before processing
│   ├── train/
│   │   ├── images/            # Training images
│   │   └── labels/            # Training labels (.txt)
│   └── val/
│       ├── images/            # Validation images
│       └── labels/            # Validation labels (.txt)
├── video/                     # Source videos for frame extraction
├── runs/                      # Training outputs
│   └── detect/
│       └── train*/
│           └── weights/
│               └── best.pt    # Best model weights
└── cat_data.yaml              # Dataset configuration
```
## Utility Functions

### Data Processing
- `video_to_frames()` - Extract frames from video files
- `rename_files()` - Batch rename with custom patterns
- `rename_jpg_to_lowercase()` - Standardize file extensions

### Label Management
- `folder_to_array()` - Load all files from directory into array
- `create_lables()` - Generate YOLO format labels from images
- `reclassify_lables()` - Remap class IDs based on filename
- `remove_empty_labels()` - Delete empty label files

### Data Cleaning
- `clean_imgs_and_lables()` - Match images to labels, move orphans
- `is_file_empty()` - Check if file is empty
- `move_file()` - Batch move files to destination
- `reset()` - Reset all training data to initial state

- note that file paths are formatted for Linux OS and may be different on a Windows computer and will need to be configured to reflect that
  
## License

MIT License
## Acknowledgments

- Ultralytics for YOLOv11
- OpenCV for video processing
- The cats (Mousse and Sherbert) for being excellent models

---

**Note**: This model is specifically trained on two individual cats and is not a general cat detector. Performance on other cats will vary.

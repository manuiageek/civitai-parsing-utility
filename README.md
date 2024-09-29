# Civitai Parsing Utility

These PENTAHO transformations were created with the intention of being used with the ComfyUI node: [ComfyUI-Custom-Scripts](https://github.com/pythongosssss/ComfyUI-Custom-Scripts). 
This allows the LoRA loader to contain the necessary keywords in a file format available alongside the LoRA file.

This script is a set of **Pentaho transformations (v9)** that monitor a directory for incoming files.

The expected files are **safetensors (LoRA)** and should follow this naming convention:
CF.AnimeName-CharacterName.XXXXX

- `CF` is a fixed prefix.
CF : Character Female 
CM : Character Male
ENV : environment
STYLE : for styles
whateveryouwant : whateveryouwant ^^ 
- `AnimeName` is the name of the anime.
- `CharacterName` is the name of the character.
- `XXXXX` is a number corresponding to the model ID on the Civitai website.

### Example

For the model found at: [https://civitai.com/models/757074](https://civitai.com/models/757074)

The file should be named: CF.SkeletonKnight-Ariane.757074


The script will process these files once they are detected in the directory.

## Program Workflow

The script consists of two main Pentaho transformations:

1. **1_PREPARE_TODO_FILES.ktr**:
    - This transformation retrieves information from the Civitai website.
    - It parses the model's page using the provided model ID (XXXXX).
    - Generates a `TODO_FILES.csv` file, which contains all the necessary information for processing.

2. **2_PROCESSING_TODO_FILES.ktr**:
    - This transformation uses the `TODO_FILES.csv` file.
    - It renames the safetensor files and updates the keywords with the parsed information from Civitai for each file.

By following this process, the utility ensures that all files are correctly named and annotated with relevant metadata, making them ready for use with the ComfyUI node.




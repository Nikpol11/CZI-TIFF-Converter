# CZI to TIFF Converter

A simple Python-based conversion tool to transform Zeiss `.czi` images into 16-bit RGB `.tiff` files.

## Overview

This repository contains a Jupyter Notebook (`CZI_to_TIFF_Converter.ipynb`) implementing:
- `.czi` image reading via `pylibCZIrw`
- Format validation (Bgr48 / 2D plane expectations)
- Optional batch conversion mode
- Optional single-file preview + export mode
- Optional dynamic range stretching for better visual results
- Threaded processing with `multiprocessing.Pool`

## Prerequisites

- Python 3.13.x (noted by the notebook as required)
- `pip`

## Usage

1. Open `CZI_to_TIFF_Converter.ipynb` in Jupyter Notebook or JupyterLab.
2. Run cells in order.
3. Select mode:
   - Directory Batch Mode
   - Single File Mode
4. For Batch Mode, select input / output folders and naming options.
5. In Single File Mode, choose an input file and output TIFF path.
6. Run conversion cell.

### Output behavior
- Batch mode:
  - If "Use original filenames" is selected, output names are the same as input (with `.tiff`).
  - If custom filename prefix is selected, output is `{prefix}{index}.tiff`.
- Single mode outputs one TIFF at chosen location.

## Programatic Configuration options in notebook

- `STRECH_DYNAMIC_RANGE`: `True` (default) or `False`
- `MULTITHREADED`: `True` or `False`
- `MAX_THREADS`: number of worker processes in batch mode

## Important Notes

- Conversion may overwrite existing TIFF output files in the destination path.
- The script was written/tested for Bgr48 input images and assumes single-plane T/Z/C in the first position.
- The preview cell only runs in single-file mode.

## Troubleshooting

- "No option selected" or file dialog cancelled: rerun notebook cell after selecting mode/path.
- Incompatible format or pixel type: confirm with the format-check cell.
- Memory issues on big files: set `MULTITHREADED = False` or reduce `MAX_THREADS`.

## Project files

- `CZI_to_TIFF_Converter.ipynb` - main conversion notebook

## License

Use as-is. No explicit license provided.

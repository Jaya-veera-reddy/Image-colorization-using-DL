# Colorful Image Colorization

This repository provides an implementation for image colorization, including automatic colorization functionality based on the research presented in:

- **[Colorful Image Colorization (ECCV 2016)]**
- **[Real-Time User-Guided Image Colorization with Learned Deep Priors (SIGGRAPH 2017)]**

---

## Installation

To get started, clone the repository and install the required dependencies:

**requirements.txt contains:**
- torch
- skimage
- numpy
- matplotlib
- argparse
- PIL

---

## Usage

The `demo_release.py` script allows you to colorize an image using the pretrained models.

To colorize an image, run:

```bash
python demo_release.py -i imgs/temples.jpg
```

- Replace `imgs/temples.jpg` with your desired image path.
- To utilize a GPU for faster processing, add the `--use_gpu` flag:

```bash
python demo_release.py -i imgs/temples.jpg --use_gpu
```

- The script saves two output images:  
  - Colorized using the **ECCV 2016** model  
  - Colorized using the **SIGGRAPH 2017** model  
- By default, outputs are saved as `saved_eccv16.png` and `saved_siggraph17.png` in the current directory.
- Change the save prefix using the `-o` or `--save_prefix` argument.

---

## Example Outputs

| ECCV 2016 Output | SIGGRAPH 2017 Output |
|------------------|---------------------|
| ![ECCV 16 Output](https://github.com/Jaya-veera-reddy/Image-colorization-using-DL/blob/master/imgs_out/forest_eccv16.png) | ![SIGGRAPH 17 Output](https://github.com/Jaya-veera-reddy/Image-colorization-using-DL/blob/master/imgs_out/forest_siggraph17.png) |

---

## Model Loading in Python

You can also load the pretrained colorizers directly in your Python code:

```python
import colorizers

colorizer_eccv16 = colorizers.eccv16(pretrained=True).eval()
colorizer_siggraph17 = colorizers.siggraph17(pretrained=True).eval()
```

The `demo_release.py` script provides further details on the pre and post-processing steps involved:  
- Converting to Lab color space  
- Resizing to 256x256  
- Colorizing  
- Concatenating with the original full-resolution L channel  
- Converting back to RGB

---

## Original Implementation (Caffe branch)

---

## Citation

If you find these models useful for your research, please cite the following papers:

```bibtex
@inproceedings{zhang2016colorful,
  title={Colorful Image Colorization},
  author={Zhang, Richard and Isola, Phillip and Efros, Alexei A},
  booktitle={ECCV},
  year={2016}
}
```

```bibtex
@article{zhang2017real,
  title={Real-Time User-Guided Image Colorization with Learned Deep Priors},
  author={Zhang, Richard and Zhu, Jun-Yan and Isola, Phillip and Geng, Xinyang and Lin, Angela S and Yu, Tianhe and Efros, Alexei A},
  journal={ACM Transactions on Graphics (TOG)},
  volume={9},
  number={4},
  year={2017},
  publisher={ACM}
}
```

---

## About the Models

This repository leverages two distinct models for image colorization:

- **ECCV 2016 Model (Colorful Image Colorization):**  
  Focuses on automatic colorization. Learns to produce vibrant and plausible colorizations for grayscale images without human intervention.

- **SIGGRAPH 2017 Model (Real-Time User-Guided Image Colorization with Learned Deep Priors):**  
  Extends automatic colorization with real-time user-guidance capabilities. While primarily designed for interactive use, it also offers robust automatic colorization.

Both models are loaded as `eccv16` and `siggraph17` respectively within the `colorizers` module and are used in evaluation mode (`.eval()`) for inference.

---


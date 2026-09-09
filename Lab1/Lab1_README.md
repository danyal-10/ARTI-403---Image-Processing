# ARTI 403 – Image Processing
## Lab 1 — Basics of Programming with Python

**Student ID:** 2240002713

---

## Objective

Explain how digital images are represented and manipulated in a computer. This lab
introduces the Python and NumPy fundamentals needed for image processing, then shows
how to load, display, save, and inspect grayscale images as numerical arrays using
OpenCV and Pillow (PIL).

---

## Tasks Completed

The notebook `Lab1_ARTI403_solution.ipynb` completes the following:

- **Task 1 — Python and NumPy basics:** short warm-up covering Python lists, sorting,
  list comprehensions, and core NumPy operations (array creation with `arange`/`reshape`,
  shape, sum, column means, scalar multiplication, and transpose).
- **Task 2 — Loading and visualizing images:**
  - Loads `cameraman.tif` with **OpenCV** (`cv2.imread`), which returns the pixel data as
    a NumPy array, and displays it. A note explains that OpenCV reads channels in BGR
    order, and a faithful grayscale version is shown using `cv2.IMREAD_GRAYSCALE`.
  - Loads `lena_gray_256.tif` with **PIL** (`Image.open`) and displays it with a
    grayscale colormap.
- **Task 3 — Image storing:** saves the images back to disk as JPEG using
  `cv2.imwrite('new_image.jpg', ...)` (OpenCV) and `img2.save('new_image2.jpg')` (PIL).
- **Task 4 — Display image as an array:** prints `.shape` and a block of pixel values for
  both images, showing that a digital image is a NumPy array of intensities.
- **Assessment — NumPy operations on the image array:** applied to the Lena array —
  inspection (shape, ndim, size, dtype), statistics (min, max, mean, std),
  indexing and slicing, photographic negative (`255 - img`), brightness increase of +50
  with clipping, binary threshold at 128, center crop (128×128), horizontal and vertical
  flips, transpose, and a pixel-intensity histogram.

---

## Libraries Used

- **OpenCV** (`cv2`) — reading, displaying, and saving images
- **NumPy** — array representation and operations
- **Matplotlib** — displaying images and the histogram
- **Pillow (PIL)** — reading and saving images
- **scikit-image** — used only to obtain `cameraman.tif` if it is not already present in
  the `images/` folder

---

## Folder Structure

```
Lab1/
├── Lab1_ARTI403_solution.ipynb   # the solved notebook
├── README.md                     # this file
└── images/
    ├── lena_gray_256.tif         # input image (provided)
    └── cameraman.tif             # input image (auto-created if missing)
```

After the notebook runs, two output files are also produced in the `Lab1/` folder
(see "Generated Output Files").

---

## How to Run

1. Install the required libraries (Anaconda already includes most of them):

   ```
   pip install opencv-python numpy matplotlib pillow scikit-image
   ```

2. Launch the notebook from inside the `Lab1` folder so the relative `images/...` paths
   resolve correctly:

   ```
   cd Lab1
   jupyter notebook Lab1_ARTI403_solution.ipynb
   ```

3. Run every cell in order (see the note below).

---

## Required Input Images

- `images/lena_gray_256.tif` — required; used with PIL.
- `images/cameraman.tif` — required; if it is not found, the notebook creates it once in
  `images/` using scikit-image.

---

## Generated Output Files

- `new_image.jpg` — saved by OpenCV (`cv2.imwrite`), written to the `Lab1/` folder.
- `new_image2.jpg` — saved by PIL (`img2.save`), written to the `Lab1/` folder.
- `images/cameraman.tif` — created only if it was not already present.

---

## Note

All cells must be executed in order, from top to bottom. In Jupyter, use
**Kernel → Restart Kernel and Run All** to reproduce every output cleanly.

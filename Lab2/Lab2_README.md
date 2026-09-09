# ARTI 403 – Image Processing
## Lab 2 — Digital Image Fundamentals (Sampling, Quantization & Image Operations)

**Student ID:** 2240002713

---

## Objective

Explain how digital images are represented and manipulated in a computer. This lab covers
spatial sampling and intensity quantization, arithmetic operations between images, and
set/logical operations on binary images, using OpenCV, NumPy, Matplotlib, and Pillow.

---

## Tasks Completed

The notebook `Lab2_ARTI403_solution.ipynb` completes the following:

### Part 1 — Image Sampling and Quantization
- **Image Sampling:** downsamples `lena_gray_256.tif` using nearest-neighbour
  interpolation (`cv2.resize`) with factors **2, 4, 8, and 14**. The real pixel
  dimensions of each result are printed and displayed.
- **Image Quantization:** reduces the number of gray levels to **2, 4, 8, 9, and 16**.
  A corrected formula maps each pixel to one of `levels` bins and spreads the bins evenly
  across the 0–255 range, so the output contains **exactly** the requested number of
  distinct levels (verified by printing the count of unique values).
- **Effect of changing parameters:** brief notes explain that increasing the sampling
  factor keeps fewer pixels (smaller, blockier image, loss of spatial detail), while
  reducing the number of quantization levels collapses intensities into a few values,
  producing visible banding (false contours).

### Part 2 — Arithmetic Operations
- **Subtract two images:** `lena_gray_256.tif` and `cameraman.tif` are converted to
  grayscale, resized to the same dimensions, and subtracted with `cv2.subtract`, which
  saturates negative results to 0 (no underflow wrap-around).
- **Add a constant value of 175 with overflow prevention:** performed two equivalent ways
  — `cv2.add` (saturates at 255) and NumPy `np.clip(..., 0, 255)` — with a check that both
  methods produce identical results and that no value exceeds 255.

### Part 3 — Sets and Logical Operations
- Operations on the binary images `A.png` and `B.png` (converted to grayscale, resized to
  the same dimensions, and thresholded to strictly 0/255):
  - **Union** (`cv2.bitwise_or`)
  - **Intersection** (`cv2.bitwise_and`)
  - **Set difference** A \\ B (`cv2.bitwise_and(A, cv2.bitwise_not(B))`)
  - **Symmetric difference** (`cv2.bitwise_xor`)
- The white-pixel counts are printed for each result, with a consistency check that the
  union equals the intersection plus the symmetric difference.

Throughout the notebook, original images and results are displayed with Matplotlib, and
shapes, dtypes, and key values are printed for verification.

---

## Libraries Used

- **OpenCV** (`cv2`) — resizing/sampling, arithmetic and bitwise operations, thresholding
- **NumPy** — array representation and the quantization formula
- **Matplotlib** — displaying images and results
- **Pillow (PIL)** — image support

No other libraries are used.

---

## Folder Structure

```
Lab2/
├── Lab2_ARTI403_solution.ipynb   # the solved notebook
├── README.md                     # this file
└── images/
    ├── lena_gray_256.tif         # input image (provided)
    ├── cameraman.tif             # input image (provided)
    ├── A.png                     # binary image (auto-created if missing)
    └── B.png                     # binary image (auto-created if missing)
```

---

## How to Run

1. Install the required libraries (Anaconda already includes most of them):

   ```
   pip install opencv-python numpy matplotlib pillow
   ```

2. Launch the notebook from inside the `Lab2` folder so the relative `images/...` paths
   resolve correctly:

   ```
   cd Lab2
   jupyter notebook Lab2_ARTI403_solution.ipynb
   ```

3. Run every cell in order (see the note below).

---

## Required Input Images

- `images/lena_gray_256.tif` — required; used for sampling, quantization, and arithmetic.
- `images/cameraman.tif` — required; used as the second image in the arithmetic operations.
- `images/A.png` and `images/B.png` — used for the set/logical operations. If they are not
  present, the notebook **automatically creates them** as simple binary images (a filled
  circle and a filled square that overlap) using OpenCV and saves them into `images/`.

---

## Generated Output Files

- `images/A.png` and `images/B.png` — created only if they were not already present.

All other results (sampled, quantized, subtracted, added, and set-operation images) are
displayed inside the notebook and are not written to disk.

---

## Note

All cells must be executed in order, from top to bottom. In Jupyter, use
**Kernel → Restart Kernel and Run All** to reproduce every output cleanly.

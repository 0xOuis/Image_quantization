# 🎨 Color Histogram & Image Quantization in C

This project implements a memory-efficient **color histogram** and a **color quantization algorithm** for PPM images using the C programming language.

It was developed as part of the *Foundations of Computer Science* project at **ENSICAEN**.

**Team member:** Omama El M'rabet

## 📌 Features

- Efficient RGB color histogram computation
- Optimized data structure using a 2D array of linked lists
- Fast color frequency lookup
- Iterator-based traversal of histogram data
- Command-line histogram visualization tool
- Image color quantization using the **popularity algorithm**
- Pixel mapping to the nearest representative colors

## 🧠 How It Works

### 🔹 Color Histogram

Instead of using a large 3D array (`256 × 256 × 256`), the histogram uses a **256 × 256 array** indexed by red (R) and green (G) values.

Each array cell contains a **linked list of blue (B) values**. Each node stores:

- The blue value (`B`)
- The color frequency
- A pointer to the next node

This approach significantly reduces memory usage for images with relatively few distinct colors while maintaining efficient access by red and green components.

### 🔹 Histogram Operations

The project supports:

- Creating and initializing a histogram from an image
- Inserting colors and updating their frequencies
- Deallocating histogram memory
- Querying the frequency of any RGB triplet
- Traversing the complete histogram with a custom iterator

### 🔹 Histogram CLI Tool

To display a PPM image's color histogram, run:

```bash
./ppmhist image.ppm
```

Each entry is displayed in the following format:

```text
(R, G, B, luminance, occurrences)
```

The luminance value used by the tool is calculated as:

```text
luminance = (R + G + B) / 3
```

### 🔹 Color Quantization

The project reduces an image to **K dominant colors** using the **popularity algorithm**:

1. Compute the image's color histogram.
2. Select the **K most frequent colors**.
3. Build a representative color palette.
4. Replace each pixel with the closest color in the palette.
5. Generate a new quantized image.

## ⚙️ Installation & Compilation

Make sure **GCC** is installed.

Compile the histogram tool:

```bash
gcc -o ppmhist ppmhist.c histogram.c image.c -Wall
```

Compile the quantization tool:

```bash
gcc -o quantification quantification.c histogram.c image.c -Wall
```

## 🚀 Usage

### 1. Compute a Color Histogram

```bash
./ppmhist input.ppm
```

### 2. Quantize an Image

```bash
./quantification K input.ppm output.ppm
```

Arguments:

- `K`: Number of colors to keep
- `input.ppm`: Original PPM image
- `output.ppm`: Output image after quantization

## 📁 Project Structure

```text
.
├── histogram.c
├── histogram.h
├── quantification.c
├── ppmhist.c
├── image.c
├── image.h
└── README.md
```

## 🔧 Optional Improvements

- **Approximate color grouping:** Group similar colors according to the conditions:

  ```text
  R / 2 = R' / 2
  G     = G'
  B / 4 = B' / 4
  ```

- **Faster nearest-neighbor search:** Optimize the selection of the closest representative color.
- **Improved quantization quality:** Explore alternative strategies for palette selection and pixel mapping.

## 🎯 Learning Outcomes

This project explores:

- Advanced data structures: linked lists and iterators
- Memory-efficient data representation
- Fundamentals of image processing
- Algorithmic optimization
- Practical programming in C

## 📜 License

This project is for educational purposes.

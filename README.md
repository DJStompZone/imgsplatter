# imgsplatter

**imgsplatter** is a Python module that creates a splatter image by randomly placing and rotating images on a canvas. It's perfect for generating abstract backgrounds, artistic wallpapers, or creative collages from your own images.

## Features

- **Random Placement and Rotation**: Images are randomly resized, rotated, and placed on the canvas to create a unique splatter effect.
- **Multiple Input Images**: Use one or multiple input images to diversify the splatter.
- **Configurable Parameters**: Customize canvas size, number of iterations, scale factors, output quality, and more.
- **Command-Line Interface**: Easy to use with command-line arguments and real-time progress display using `tqdm`.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
  - [Command-Line Options](#command-line-options)
  - [Examples](#examples)
- [Notes](#notes)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Installation

### Prerequisites

- Python 3.6 or higher
- pip package manager

### Install via pip

You can install **imgsplatter** directly from PyPI:

```bash
pip install imgsplatter
```

## Usage

Run the `imgsplatter` module as a Python script from the command line:

```bash
python -m imgsplatter [options]
```

Alternatively, you can use `imgsplatter` as a command-line tool if installed accordingly.

### Command-Line Options

| Option                   | Short      | Description                                                                                                                                                          | Default                   |
|--------------------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------|
| `--width WIDTH`          | `-w WIDTH` | Width of the output image. If only width or height is specified, both dimensions will use that value.                                                                | `1920`                    |
| `--height HEIGHT`        | `-H HEIGHT`| Height of the output image. If only width or height is specified, both dimensions will use that value.                                                               | `1080`                    |
| `--input-image IMAGE`    | `-i IMAGE` | Input image(s) to use. At least one is required. Can be specified multiple times to include multiple images.                                                         | Required                  |
| `--iterations N`         |            | Number of iterations (images to place).                                                                                                                              | `750`                     |
| `--min-scale SCALE`      |            | Minimum scale factor for resizing images.                                                                                                                            | `0.15`                    |
| `--max-scale SCALE`      |            | Maximum scale factor for resizing images.                                                                                                                            | `0.325`                   |
| `--output-image FILE`    | `-o FILE`  | Output image filename. If not specified, defaults to `splatter-<timestamp>.jpg`.                                                                                     | `splatter-<timestamp>.jpg`|
| `--jpeg-quality QUALITY` |            | JPEG quality for the output image (1-95).                                                                                                                            | `95`                      |
| `--help`                 | `-h`       | Show help message and exit.                                                                                                                                          |                           |

### Examples

#### Basic Usage

Generate a splatter image using a single input image:

```bash
python -m imgsplatter -i image.png
```

#### Multiple Input Images

Use multiple images to create a more varied splatter:

```bash
python -m imgsplatter -i image1.png -i image2.png -i image3.png
```

#### Custom Canvas Size

Create a square canvas of `1024x1024` pixels:

```bash
python -m imgsplatter -w 1024 -i image.png
```

#### Custom Dimensions

Create a canvas with a width of `1920` pixels and a height of `1080` pixels:

```bash
python -m imgsplatter -w 1920 -H 1080 -i image.png
```

#### Adjusting Iterations and Scale

Customize the number of iterations and scale factors:

```bash
python -m imgsplatter -i image.png --iterations 1000 --min-scale 0.1 --max-scale 0.5
```

#### Specify Output File and Quality

Set a custom output filename and JPEG quality:

```bash
python -m imgsplatter -i image.png -o my_splatter.jpg --jpeg-quality 85
```

#### Full Example

Generate a `1920x1080` image with 500 iterations, scaling images between 15% and 30% of their original size, and save it as `output-image.jpg`:

```bash
python -m imgsplatter -w 1920 -H 1080 -i image1.png -i image2.png --iterations 500 --min-scale 0.15 --max-scale 0.3 -o output-image.jpg
```

## Notes

- **Canvas Size Defaults**: If neither width nor height is provided, the default canvas size is `1920x1080`.
- **Single Dimension Provided**: If only width or height is specified, both dimensions will use that value, resulting in a square canvas.
- **Scale Factors**: The `--min-scale` and `--max-scale` options determine the range for randomly resizing the input images. Scale factors are relative to the original image size.
- **Iterations**: The `--iterations` option determines how many images are randomly placed onto the canvas. More iterations result in a denser splatter.
- **JPEG Quality**: The `--jpeg-quality` option sets the quality of the output JPEG image. Higher values mean better quality but larger file sizes. The maximum recommended value is `95`.

## Importing in Python Scripts:
  If you wish to use `imgsplatter` within your own Python scripts, you can import the `splatter` function:

  ```python
  import argparse
  from imgsplatter.splatter.splatter import splatter

  # Prepare arguments as needed
  args = argparse.Namespace(
      width=1920,
      height=1080,
      input_image=['image1.png', 'image2.png'],
      iterations=500,
      min_scale=0.15,
      max_scale=0.3,
      output_image='output-image.jpg',
      jpeg_quality=95
  )

  splatter(args)
  ```

  Ensure that you import `argparse` if you are creating an `argparse.Namespace` object.

## Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the Repository**: Click the "Fork" button at the top right corner of the [GitHub repository](https://github.com/djstompzone/imgsplatter).

2. **Clone Your Fork**: Clone your forked repository to your local machine.

   ```bash
   git clone https://github.com/yourusername/imgsplatter.git
   ```

3. **Create a New Branch**: Create a new branch for your feature or bug fix.

   ```bash
   git checkout -b feature/your-feature-name
   ```

4. **Make Changes**: Implement your feature or bug fix.

5. **Commit Changes**: Commit your changes with a descriptive commit message.

   ```bash
   git commit -am "Add new feature"
   ```

6. **Push to GitHub**: Push your changes to your GitHub repository.

   ```bash
   git push origin feature/your-feature-name
   ```

7. **Submit a Pull Request**: Open a pull request to the `main` branch of the original repository.

## License

This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute this software in accordance with the terms of the license.

## Contact

For any questions or suggestions, please open an issue on the [GitHub repository](https://github.com/djstompzone/imgsplatter). Alternatively, you can join the [StompZone Discord](https://discord.stomp.zone) to message me directly.

---

*Happy splattering!*

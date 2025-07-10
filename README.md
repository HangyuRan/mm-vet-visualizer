# VCode on MM-Vet Visualizer

This is the official visualizer for the **VCode on MM-Vet** benchmark project. This interface provides an interactive way to explore and analyze the benchmark's results, focusing on the performance of Vision-Language Models (VLMs) when evaluated on original raster images versus synthetically reconstructed SVG images.

The visualizer is designed to be a simple, self-contained HTML file that runs entirely in the browser, making it easy to share and review results without any server-side setup.

## Features

This visualizer provides several key features to facilitate result analysis:

-   **Dual View Modes**: Dynamically switch between two powerful comparison modes:
    -   **By Method**: Compare different generator models (Claude, Gemini, etc.) under a single SVG conversion method.
    -   **By Generator**: Compare all conversion methods for a single generator model (e.g., see results for `Claude-Img2SVG` vs. `Claude-Img2Text2SVG`).
-   **Inference Model Selection**: Easily switch between different VLM reasoners, such as `Qwen2.5-VL-7B`, `Qwen2.5-VL-3B`, and `GPT-4o-mini`, to see how each performs on the various image types.
-   **Interactive Data Display**: Click on images, questions, answers, or predictions to view the full, unabbreviated content in a modal popup.
-   **Dynamic Search & Filter**: Instantly filter the entire table by any keyword or narrow down results by specific AI capabilities (OCR, Math, etc.).
-   **Color-Coded Scores**: Prediction scores are color-coded (green for correct, red for incorrect) for quick visual assessment.

## Project Structure

The project relies on a specific file and folder structure to correctly load all the necessary data.

```
/
├── index.html                  # The main application file
├── mm-vet.json                 # Core benchmark metadata (questions, answers)
│
├── images/                     # Original raster images
├── images_claude/              # SVG images by Claude (img2svg)
├── images_claude_from_text/    # SVG images by Claude (img2text2svg)
├── images_gemini/              # ...and so on for other generators
└── ...
│
├── prediction/                 # Root folder for all prediction files
│   ├── gpt4o-mini/
│   │   ├── pred_original.json
│   │   └── pred_claude.json ...
│   ├── qwen3b/
│   │   ├── pred_original.json
│   │   └── pred_claude.json ...
│   └── qwen7b/
│       ├── pred_original.json
│       └── pred_claude.json ...
│
├── score/                      # Root folder for all score files
│   ├── gpt4o-mini/
│   │   ├── score_original.json
│   │   └── score_claude.json ...
│   ├── qwen3b/
│   │   └── ...
│   └── qwen7b/
│       └── ...
│
└── README.md                   # This file
```

## How to Use

1.  Ensure all your data files and folders (`prediction/`, `score/`, `images/`, etc.) are placed in the correct locations as described in the Project Structure.
2.  Open the `index.html` file in any modern web browser.
3.  Use the "View Mode" and its corresponding dropdown to select your primary comparison axis.
4.  Use the "Model" dropdown to select which VLM's reasoning results you want to see.

The application will dynamically load the relevant data and render the comparison table.
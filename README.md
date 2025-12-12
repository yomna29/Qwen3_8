
# Document OCR and Structuring with Vision-Language Model

This notebook provides a robust solution for converting various document types (PDFs and images) into structured Markdown text using a powerful Vision-Language Model (VLM). Leveraging the `Qwen/Qwen3-VL-8B-Instruct` model from Hugging Face Transformers, it performs Optical Character Recognition (OCR) and intelligently extracts document structure, tables, and visual descriptions.

## Features:

*   **Multi-format Input**: Process entire PDF documents or single image files (`.jpg`, `.png`, etc.).
*   **Structured Markdown Output**: Generates clean, well-formatted Markdown, preserving headings, lists, and converting tables into Markdown pipe tables. It also includes descriptive 'Visual:' lines for non-text elements like diagrams and charts.
*   **Configurable Inference Quality**: Easily adjust inference parameters (DPI, image `long_side`, `max_new_tokens`) via `Quality` settings (FAST, BASELINE, ACCURATE) to balance speed and output quality.
*   **Batch Processing**: Efficiently processes multiple pages of a PDF in batches to optimize performance.
*   **Custom Prompt Engineering**: Utilizes a carefully crafted system prompt to guide the VLM in producing high-quality, structured output, and robust post-processing to clean up model echoes and enforce formatting rules.
*   **Detailed Reporting**: Outputs not only the converted Markdown (both as a single file and per-page JSONL) but also a comprehensive `inference_report.json` detailing runtime statistics, configuration, and environment information.

## How it Works:

1.  **Environment Setup**: Installs necessary libraries (`transformers`, `pdf2image`, etc.) and configures the environment for optimal GPU utilization.
2.  **Model Loading**: Loads the `Qwen/Qwen3-VL-8B-Instruct` VLM and its processor, enabling efficient text and image understanding.
3.  **Image Pre-processing**: Converts PDF pages or input images into a suitable format for the VLM, including resizing and quality adjustments.
4.  **Prompt Construction**: Dynamically builds chat-style prompts that include both the image and specific instructions for structured Markdown generation.
5.  **Batch Inference**: Runs the VLM on batches of pages, generating raw text output.
6.  **Post-processing and Cleaning**: Applies a series of regex-based cleaning and normalization steps to refine the VLM's output into production-ready Markdown, ensuring adherence to strict formatting guidelines.
7.  **Output Generation**: Saves the final Markdown, per-page JSONL, and a detailed performance report.

This notebook is ideal for anyone needing to programmatically extract structured content from documents for further analysis, archiving, or knowledge base integration.

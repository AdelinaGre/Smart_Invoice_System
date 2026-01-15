# 🧾 Smart Invoice System & Analytics Pipeline

An end-to-end AI solution for automating invoice processing. This project extracts structured data from invoice images using OpenAI's GPT-4o, validates and cleans the data, and performs advanced machine learning tasks—including anomaly detection for fraud and seasonality prediction.

## 🚀 Key Features

* **AI-Powered OCR:** Utilizes `GPT-4o-mini` to intelligently extract complex fields (Vendor, Client, Line Items, VAT, Totals) into structured JSON.
* **Automated Validation:** A dedicated `InvoiceDataValidator` class sanitizes inputs, repairs date formats, and scores data completeness.
* **ML-Ready Dataset Builder:** Automatically transforms nested JSON logs into flat, feature-engineered CSV datasets suitable for modeling.
* **Anomaly Detection:** Implements **Isolation Forest** to automatically flag suspicious invoices (outliers in values, tax rates, or item counts).
* **Business Insights:** Visualization modules for tracking spending seasonality and identifying top vendors.

## 🛠️ Architecture

The pipeline follows a modular structure:
1.  **Ingestion:** Downloads dataset via KaggleHub.
2.  **Extraction:** Encodes images to Base64 -> Sends to OpenAI API -> Receives JSON.
3.  **Processing:** Validates structure -> Cleans types -> Scores completeness.
4.  **Analytics:** Generates ML features -> Runs Isolation Forest & Random Forest models.
## 📂 Project Structure

The codebase is organized into modular classes, each handling a specific stage of the pipeline:

| Class | Description |
| :--- | :--- |
| **`InvoiceProcessor`** | **Core Controller**: Orchestrates the entire workflow, manages API calls, and handles file I/O. |
| **`InvoiceDataExtractor`** | **AI Interface**: Handles prompt engineering, Base64 image encoding, and communication with the OpenAI API. |
| **`InvoiceDataValidator`** | **Data Quality**: Sanitizes extracted JSON, standardizes numeric/date formats, and scores data completeness. |
| **`MLDatasetBuilder`** | **Feature Engineering**: Transforms raw JSON into ML-ready datasets (calculates VAT %, tax rates, seasonality features). |
| **`InvoiceEDA`** | **Analytics**: Generates business insights and visualizations (seasonality trends, top vendor statistics). |
## ⚙️ Setup & Installation

### 1. Prerequisites
Ensure you have the required Python libraries installed:

```bash
pip install openai pandas numpy matplotlib seaborn scikit-learn kagglehub ipython

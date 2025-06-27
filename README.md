# Dataset Upload Module

## Overview

This custom Drupal 10 module provides a drag-and-drop dataset upload tool enhanced by AI-generated metadata functionality. It is built to demonstrate enterprise-level use of Drupal APIs, custom entities, multilingual support, and third-party AI integration (OpenAI).

---

## 📦 Features Implemented

### ✅ Mini-Task 1: Dataset Upload and Processing

- Drag-and-drop file upload using [Dropzone.js](https://www.drupal.org/project/dropzonejs)
- Support for `.csv` and `.xlsx` files
- File validation for type and size
- Parsing of uploaded file using a backend service
- Extraction and display of:
  - File name
  - File size (KB)
  - Column names
  - Row count
- Summary display using a custom Twig template
- Custom content entity `dataset_metadata` to store file metadata and upload status

---

### ✅ Mini-Task 2: AI-Driven Metadata Generation

- AI integration using OpenAI's `gpt-3.5-turbo` model
- Generated fields include:
  - Title
  - Description
  - Tags
  - Suggested Categories
- Metadata edit form to preview/edit AI content
- Bilingual field support for English and Arabic using Drupal's multilingual API
- Metadata translation stored on the entity as `ar` translation
- Prepares support for entity revision/draft system

---

## 🧪 Getting Started

### Requirements

- Drupal 10+
- PHP 8.1+
- OpenAI API key
- Composer dependencies:
  ```bash
  composer require drupal/dropzonejs

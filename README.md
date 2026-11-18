# autonomous-invoice-processor
Autonomous n8n pipeline using Gemini 2.5 Pro Multi-Modal Vision to read PDF invoices, extract accounting data to Google Sheets, and organize files in Drive.

# 🧾 Autonomous AI Invoice & Expense Processor (Multi-Modal AI)

[![n8n](https://img.shields.io/badge/n8n-Cloud-FF6C37?style=flat-square&logo=n8n)](https://n8n.io/)
[![Google Gemini](https://img.shields.io/badge/Gemini_2.5_Pro-Multi--Modal-4285F4?style=flat-square&logo=google)](https://ai.google.dev/)
[![Google Workspace](https://img.shields.io/badge/Google_Workspace-Drive_&_Sheets-0F9D58?style=flat-square&logo=google-drive)](#)

A 100% serverless, zero-touch back-office automation pipeline. This workflow actively monitors an inbox for invoices and receipts, uses Multi-Modal AI to "read" the PDFs (bypassing the need for rigid OCR templates), extracts structured accounting data, logs it to a ledger, and automatically organizes the files in the cloud.

## 🚀 The Business Problem It Solves
Manual data entry is the biggest bottleneck in operational finance. Traditional OCR (Optical Character Recognition) software fails when vendors change their invoice layouts. 

This project solves that by using **Semantic Vision AI**. Gemini 2.5 Pro natively reads the PDF attachment like a human accountant would, identifying the total amount, vendor name, tax, and currency, regardless of how the invoice is formatted. This reduces processing time from 5 minutes per invoice to **under 2 seconds**, with zero manual data entry.

## ⚙️ Architecture & Tech Stack
* **Trigger:** Gmail API (Actively listens for incoming emails containing `has:attachment` in the billing inbox).
* **Multi-Modal Parsing:** Google Gemini 2.5 Pro Vision (Directly ingests the raw base64 PDF and extracts required fields using JSON schema enforcement).
* **Database / Ledger:** Google Sheets (Appends parsed data: Date, Vendor, Amount, Currency, Tax, Processed Timestamp).
* **File Management:** Google Drive (Programmatically renames the PDF based on the Vendor and Date, and files it into the appropriate tax-year folder).

## 🧠 Workflow Logic
1. **Listen:** n8n polls the designated Gmail inbox for new unread messages with attachments.
2. **Extract:** The PDF attachment is converted to base64 and sent directly to the Gemini API.
3. **Analyze:** The LLM is prompted with a strict JSON schema to extract `vendor`, `date`, `amount`, `currency`, and `tax`. 
4. **Log:** n8n maps the JSON response directly into the next empty row of the Google Sheets Ledger.
5. **Archive:** The original PDF is saved to Google Drive using a standardized naming convention (e.g., `VendorName_2026-11-18.pdf`).

## 🤝 Let's Collaborate
I specialize in building intelligent, autonomous systems that eliminate manual operational bottlenecks. I am actively seeking collaborations with businesses, finance teams, and agency owners who want to leverage AI to drastically cut back-office overhead.

**Let’s connect!** Reach out to me directly via LinkedIn (link in GitHub bio) to discuss how we can automate your operations.

---
**Tags & Keywords:** `n8n workflow` `AI Accounting` `Invoice Automation` `Gemini Vision` `Multi-Modal AI` `OCR Alternative` `Business Automation` `Google Workspace Automation` `Finance Tech`


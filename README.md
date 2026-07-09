# IITM Invoice Extraction Service

A lightweight, robust FastAPI service designed to extract structured invoice fields from raw plain-text invoice formats.

## Endpoint

### `POST /extract`

Extracts vendor, amount, currency, date, invoice_no, and tax from raw invoice text.

#### Request body:
```json
{
  "invoice_text": "INVOICE\nInvoice No: INV-2026-0041\nDate: 15 March 2026\nVendor: TechParts Pvt Ltd\nSubtotal: Rs. 2,199.00\nGST (18%): Rs. 395.82\nTOTAL: Rs. 2,594.82\nCurrency: INR"
}
```

#### Response body (always returns all 6 keys; `null` if a field is not found):
```json
{
  "invoice_no": "INV-2026-0041",
  "date": "2026-03-15",
  "vendor": "TechParts Pvt Ltd",
  "amount": 2199.00,
  "tax": 395.82,
  "currency": "INR"
}
```

## Local Development

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Start the FastAPI development server:
   ```bash
   uvicorn main:app --reload
   ```

## Deploying to Render
1. Push this repository to your GitHub account.
2. Go to [Render Dashboard](https://dashboard.render.com).
3. Create a new **Web Service** and connect this repository.
4. Render will automatically detect the `Dockerfile` and build/deploy the service.

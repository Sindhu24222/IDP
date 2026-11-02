# SmartCert AI Dashboard

A responsive certificate-operations dashboard with client-side dataset import, risk checks, and certificate status tracking.

## Run locally

```bash
npm install
npm run dev
```

Open the local URL printed by Vite. Create a production build with `npm run build`.

## Dashboard workflows

- Load the built-in sample dataset or import a CSV/XLSX spreadsheet.
- Run risk checks for missing email addresses, duplicate emails, and scores below 60.
- Generate certificates for records without risk flags.
- Navigate the operational sections from the sidebar and inspect the active dataset.

Dataset processing is local to the browser. The demo does not connect to a backend, send email, create cryptographic certificate files, or provide a live AI service.
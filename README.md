# CertGen Pro

CertGen Pro is a React/Vite certificate generation workspace with CSV/XLSX import, field mapping, template editing, persistent demo data, verification, and an Express API adapter.

## Features

- Dashboard with workflow statistics and quick-start actions
- CSV, XLSX, XLS, and clearly labeled PDF OCR staging upload
- Automatic and manual field mapping
- Live certificate template preview with QR verification links
- Individual and bulk record editing
- Generation progress and local verification registry
- Responsive navigation, print support, localStorage session persistence
- Demo mode works without MongoDB

## Install and run

```powershell
npm install
npm install --prefix client
npm run dev
```

The Vite client runs on `http://localhost:5173` and the API runs on `http://localhost:5000`.

Run only one side with `npm run client` or `npm run server`. Build the client with `npm run build`.

## Environment variables

Copy `.env.example` to `.env` when configuring the backend:

```text
PORT=5000
MONGODB_URI=mongodb://127.0.0.1:27017/certgen-pro
JWT_SECRET=replace-with-a-long-random-value
```

The current API uses an in-memory store so the demo is immediately usable. The `MONGODB_URI` variable is reserved for the persistence adapter.

## Workflow

1. Start on Dashboard and open Upload Data.
2. Import a CSV/XLSX file or continue with the included demo records.
3. Review Field Mapping and continue to Template Design.
4. Adjust the certificate content and appearance, then open Preview & Edit.
5. Apply an individual override or use Bulk Editor for multiple records.
6. Generate certificates and verify an ID from the generated list or Verify Certificate.

## API

| Method | Endpoint | Purpose |
| --- | --- | --- |
| GET | `/api/health` | API status and mode |
| GET | `/api/certificates` | List certificates |
| GET | `/api/certificates/:id` | Get one certificate |
| POST | `/api/certificates` | Create a certificate |
| PUT | `/api/certificates/:id` | Update a certificate |
| DELETE | `/api/certificates/:id` | Delete a certificate |
| GET | `/api/verify/:certificateId` | Verify certificate authenticity |

## Structure

- `client/src/context`: persistent workflow state
- `client/src/pages`: connected workflow screens
- `client/src/components/certificate`: reusable certificate rendering
- `client/src/services`: file parsing and future export/API adapters
- `server`: Express routes, controllers, validation, and demo store

## Future integration points

Replace `client/src/services/fileParser.js` PDF staging with OCR/PaddleOCR or a FastAPI service, replace `server/services/certificateStore.js` with Mongoose models, and add authenticated API calls through a client API service.
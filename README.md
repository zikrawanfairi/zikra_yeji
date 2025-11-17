# zikra_yeji
{
Proyek starter Node.js + Express untuk zikra_yeji.

Fitur:
- Server Express minimal dengan endpoint /health
- Struktur direktori: src/, tests/
- Skrip npm untuk start, dev, lint, test

Cara menjalankan:
1. Install dependencies:
   npm install
2. Jalankan server (development):
   npm run dev
3. Build & start (production):
   npm start

License: MIT
  "name": "zikra_yeji",
  "version": "0.1.0",
  "description": "Starter project for zikra_yeji",
  "main": "src/index.js",
  "scripts": {
    "start": "node src/index.js",
    "dev": "nodemon src/index.js",
    "lint": "eslint .",
    "test": "jest"
  },
  "dependencies": {
    "express": "^4.18.2"
  },
  "devDependencies": {
    "nodemon": "^2.0.22",
    "eslint": "^8.0.0",
    "jest": "^29.0.0"
  }
}node_modules/
.env
dist/
*.sqlite
const express = require('express');
const health = require('./routes/health');

const app = express();
app.use(express.json());

app.use('/health', health);

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
const express = require('express');
const router = express.Router();

router.get('/', (req, res) => {
  res.json({ status: 'ok', timestamp: new Date().toISOString() });
});

module.exports = router;

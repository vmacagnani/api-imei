const express = require('express');
const multer = require('multer');
const csv = require('csv-parser');
const axios = require('axios');
const fs = require('fs');
const path = require('path');

const app = express();
const upload = multer({ dest: 'uploads/' });

const PORT = 3000;
const API_TOKEN = 'ef20d6c9-1f4f-4fa2-9285-7f4035cd5fe3';

app.use(express.static('public'));

app.post('/upload', upload.single('csvFile'), async (req, res) => {
  const results = [];
  const filePath = req.file.path;

  fs.createReadStream(filePath)
    .pipe(csv())
    .on('data', (data) => results.push(data))
    .on('end', async () => {
      const imeis = results.map(row => row.IMEI);
      const output = [];

      for (const imei of imeis) {
        try {
          const response = await axios.get(`https://api.imei.info/v2/device/${imei}`, {
            headers: {
              'Authorization': `Bearer ${API_TOKEN}`
            }
          });

          output.push({ imei, data: response.data });
        } catch (error) {
          output.push({ imei, error: error.response?.data || 'Erro desconhecido' });
        }
      }

      fs.unlinkSync(filePath); // remove o arquivo após o uso
      res.json(output);
    });
});

app.listen(PORT, () => {
  console.log(`Servidor rodando em http://localhost:${PORT}`);
});

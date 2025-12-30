# milikrafaelvenanreport-telgram
Web PWA untuk membantu report akun Telegram penipuan
[milikrafavenanreport-telegram.html](https://github.com/user-attachments/files/24376665/milikrafavenanreport-telegram.html)
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Report Akun Telegram Penipuan (Resmi)</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f6f8;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }
    .container {
      background: #ffffff;
      padding: 25px;
      width: 100%;
      max-width: 520px;
      border-radius: 12px;
      box-shadow: 0 4px 14px rgba(0,0,0,0.1);
    }
    h2 {
      text-align: center;
      margin-bottom: 6px;
      color: #333;
    }
    .subtitle {
      text-align: center;
      font-size: 13px;
      color: #666;
      margin-bottom: 18px;
    }
    label {
      font-weight: bold;
      display: block;
      margin-top: 12px;
    }
    input, textarea, select {
      width: 100%;
      padding: 10px;
      margin-top: 6px;
      border-radius: 6px;
      border: 1px solid #ccc;
      font-size: 14px;
    }
    textarea { resize: vertical; }
    button {
      margin-top: 14px;
      width: 100%;
      padding: 12px;
      background: #0088cc;
      color: #fff;
      border: none;
      border-radius: 6px;
      font-size: 15px;
      cursor: pointer;
    }
    button.secondary {
      background: #e0e0e0;
      color: #333;
    }
    button:hover { opacity: 0.9; }
    .box {
      margin-top: 16px;
      padding: 12px;
      background: #f1f7fb;
      border-left: 4px solid #0088cc;
      font-size: 13px;
    }
    .steps {
      margin-top: 12px;
      font-size: 13px;
    }
    .steps ol { padding-left: 18px; }
    .footer {
      margin-top: 14px;
      font-size: 12px;
      color: #555;
    }
    .footer a { color: #0088cc; text-decoration: none; }
  </style>
</head>
<body>
  <div class="container">
    <h2>Report Akun Telegram Penipuan</h2>
    <div class="subtitle">Versi benar & sesuai kebijakan resmi Telegram</div>

    <form onsubmit="siapkanReport(event)">
      <label>Username / Link Akun Telegram</label>
      <input type="text" id="username" placeholder="@username atau https://t.me/username" required />

      <label>Jenis Pelanggaran</label>
      <select id="jenis" required>
        <option value="">-- Pilih --</option>
        <option>Scam / Penipuan</option>
        <option>Phishing</option>
        <option>Akun Palsu</option>
        <option>Spam</option>
      </select>

      <label>Kronologi Singkat</label>
      <textarea id="kronologi" rows="4" placeholder="Contoh: pelaku menawarkan barang, meminta transfer, lalu memblokir" required></textarea>

      <button type="submit">Siapkan Laporan</button>
    </form>

    <div id="hasil" style="display:none;">
      <div class="box">
        <strong>Teks Laporan (siap dikirim ke SpamBot):</strong><br><br>
        <textarea id="teksLaporan" rows="5" readonly></textarea>
      </div>

      <button onclick="salinTeks()" class="secondary">Salin Teks Laporan</button>
      <button onclick="bukaSpamBot()">Buka SpamBot Telegram</button>

      <div class="steps">
        <strong>Langkah selanjutnya di Telegram:</strong>
        <ol>
          <li>Buka <strong>@SpamBot</strong></li>
          <li>Pilih kategori <em>Scam / Fake Account</em></li>
          <li>Tempel teks laporan</li>
          <li>Kirim screenshot / bukti chat</li>
          <li>Tunggu verifikasi dari Telegram</li>
        </ol>
      </div>
    </div>

    <div class="footer">
      Referensi resmi Telegram:<br>
      • <a href="https://telegram.org/faq_spam" target="_blank">Spam & Scam Policy</a><br>
      • <a href="https://telegram.org/terms" target="_blank">Terms of Service</a>
    </div>
  </div>

  <script>
    function siapkanReport(e) {
      e.preventDefault();

      const user = document.getElementById('username').value;
      const jenis = document.getElementById('jenis').value;
      const kronologi = document.getElementById('kronologi').value;

      const teks = `Laporan Akun Telegram\n\nAkun: ${user}\nJenis Pelanggaran: ${jenis}\nKronologi: ${kronologi}`;

      document.getElementById('teksLaporan').value = teks;
      document.getElementById('hasil').style.display = 'block';
    }

    function salinTeks() {
      const t = document.getElementById('teksLaporan');
      t.select();
      document.execCommand('copy');
      alert('Teks laporan berhasil disalin');
    }

    function bukaSpamBot() {
      window.open('tg://resolve?domain=SpamBot', '_blank') ||
      window.open('https://t.me/SpamBot', '_blank');
    }
  </script>
</body>
</html>

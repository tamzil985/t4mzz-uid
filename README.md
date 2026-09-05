<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Admin - T4MZZ UID</title>

  <style>
    * {
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      margin: 0;
      min-height: 100vh;
      background: #090713;
      color: white;
      padding: 20px;
    }

    .container {
      max-width: 500px;
      margin: auto;
    }

    h1 {
      text-align: center;
      color: #b35cff;
      margin-bottom: 5px;
    }

    .subtitle {
      text-align: center;
      color: #aaa;
      margin-bottom: 25px;
    }

    .card {
      background: #151020;
      border: 1px solid #913cff;
      border-radius: 18px;
      padding: 20px;
      margin-bottom: 15px;
    }

    label {
      display: block;
      margin-bottom: 10px;
      font-weight: bold;
    }

    input {
      width: 100%;
      padding: 15px;
      font-size: 18px;
      border-radius: 10px;
      border: 1px solid #913cff;
      background: #0c0812;
      color: white;
    }

    button {
      width: 100%;
      padding: 15px;
      margin-top: 15px;
      border: none;
      border-radius: 10px;
      background: #9b4dff;
      color: white;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
    }

    button:hover {
      background: #7d2ee8;
    }

    .success {
      display: none;
      margin-top: 15px;
      padding: 12px;
      border-radius: 10px;
      background: #163d25;
      color: #7dff9d;
      text-align: center;
    }

    .price-box {
      text-align: center;
      padding: 20px;
      font-size: 28px;
      font-weight: bold;
      color: #c783ff;
    }

    .link {
      display: block;
      text-align: center;
      color: #b56cff;
      margin-top: 20px;
      text-decoration: none;
    }

  </style>
</head>

<body>

  <div class="container">

    <h1>T4MZZ UID</h1>
    <div class="subtitle">PANEL ADMIN</div>

    <div class="card">

      <label>Harga Semua UID</label>

      <input
        type="number"
        id="harga"
        value="20000"
        placeholder="Masukkan harga"
      >

      <button onclick="simpanHarga()">
        SIMPAN HARGA
      </button>

      <button onclick="set20k()">
        SET SEMUA Rp 20.000
      </button>

      <div class="success" id="success">
        ✓ Harga berhasil disimpan!
      </div>

    </div>

    <div class="card">

      <div style="text-align:center;color:#aaa;">
        HARGA SAAT INI
      </div>

      <div class="price-box" id="hargaTampil">
        Rp 20.000
      </div>

    </div>

    <a href="/" class="link">
      ← Kembali ke Website
    </a>

  </div>


<script>

  // Ambil harga dari browser
  let harga = localStorage.getItem("hargaUID");

  // Jika belum ada, otomatis Rp20.000
  if (!harga) {
    harga = 20000;
    localStorage.setItem("hargaUID", harga);
  }

  // Tampilkan harga
  document.getElementById("harga").value = harga;

  tampilkanHarga();


  function formatRupiah(angka) {
    return "Rp " + Number(angka).toLocaleString("id-ID");
  }


  function tampilkanHarga() {

    let hargaSekarang =
      localStorage.getItem("hargaUID") || 20000;

    document.getElementById("hargaTampil").innerText =
      formatRupiah(hargaSekarang);

  }


  function simpanHarga() {

    let hargaBaru =
      document.getElementById("harga").value;

    if (hargaBaru <= 0 || hargaBaru === "") {
      alert("Masukkan harga yang benar!");
      return;
    }

    // Simpan harga
    localStorage.setItem("hargaUID", hargaBaru);

    tampilkanHarga();

    document.getElementById("success").style.display = "block";

    setTimeout(function() {
      document.getElementById("success").style.display = "none";
    }, 3000);

  }


  function set20k() {

    localStorage.setItem("hargaUID", 20000);

    document.getElementById("harga").value = 20000;

    tampilkanHarga();

    document.getElementById("success").style.display = "block";

  }

</script>

</body>
</html>

<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover,maximum-scale=1">
<meta name="referrer" content="no-referrer">
<meta name="robots" content="noindex,nofollow">
<title>Scan Kamera — MB RMS</title>
<style>
  :root{
    --bg:#17191b;
    --panel:#212528;
    --panel-2:#292d31;
    --line:#34383c;
    --text:#eceef0;
    --muted:#959ba1;
    --silver:#c9cdd1;
    --ok:#3f9d6d;
    --ok-dim:#1e3a2c;
    --bad:#cf5b62;
    --bad-dim:#3a2224;
    --mono:'SFMono-Regular',Consolas,ui-monospace,monospace;
  }
  *{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
  html,body{margin:0;height:100%}
  body{
    background:var(--bg);color:var(--text);
    font:15px/1.5 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif;
    display:flex;flex-direction:column;
    padding:env(safe-area-inset-top) env(safe-area-inset-right) env(safe-area-inset-bottom) env(safe-area-inset-left);
    overscroll-behavior:none;
  }

  /* ---- bar atas ---- */
  .bar{display:flex;align-items:center;gap:10px;padding:11px 15px;border-bottom:1px solid var(--line);flex:0 0 auto}
  .bar .who{flex:1;min-width:0}
  .bar .who b{display:block;font-size:14px;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
  .bar .who span{display:block;font-size:11.5px;color:var(--muted)}
  .dot{width:7px;height:7px;border-radius:50%;background:var(--muted);flex:0 0 auto}
  .dot.live{background:var(--ok)}
  .dot.dead{background:var(--bad)}

  /* ---- jendela bidik ---- */
  .view{position:relative;flex:0 0 auto;aspect-ratio:4/3;max-height:46vh;background:#000;overflow:hidden}
  video{width:100%;height:100%;object-fit:cover;display:block}
  .reticle{position:absolute;inset:0;pointer-events:none;display:none}
  .reticle.on{display:block}
  /* Garis horizontal: barcode ritel itu 1D, jadi yang penting barcode
     memotong garis ini — bukan masuk ke dalam kotak. */
  .reticle .frame{
    position:absolute;left:8%;right:8%;top:50%;height:24%;transform:translateY(-50%);
    border:1px solid rgba(255,255,255,.35);border-radius:6px;
    box-shadow:0 0 0 100vmax rgba(0,0,0,.34);
  }
  .reticle .line{position:absolute;left:8%;right:8%;top:50%;height:2px;background:var(--bad);opacity:.85}
  .hint{position:absolute;left:0;right:0;bottom:10px;text-align:center;font-size:12.5px;color:rgba(255,255,255,.72);text-shadow:0 1px 3px #000}

  .cover{position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:14px;padding:24px;text-align:center;background:var(--bg)}
  .cover.hide{display:none}
  .cover p{margin:0;color:var(--muted);font-size:13.5px;max-width:34ch}

  /* ---- kendali ---- */
  .ctl{display:flex;gap:9px;padding:11px 15px;border-bottom:1px solid var(--line);flex:0 0 auto}
  button{
    font:inherit;font-size:14px;font-weight:500;
    background:var(--panel-2);color:var(--text);border:1px solid var(--line);
    border-radius:9px;padding:11px 16px;cursor:pointer;
  }
  button:active{background:#33383d}
  button:disabled{opacity:.42}
  button.primary{background:var(--silver);color:#15181a;border-color:var(--silver);font-weight:600}
  button.wide{flex:1}
  button:focus-visible{outline:2px solid #6ea8fe;outline-offset:2px}

  /* ---- daftar hasil ---- */
  .list{flex:1 1 auto;overflow-y:auto;-webkit-overflow-scrolling:touch;padding:6px 15px 22px}
  .empty{color:var(--muted);font-size:13.5px;padding:22px 0;text-align:center}
  .row{display:flex;align-items:center;gap:11px;padding:11px 0;border-bottom:1px solid var(--line)}
  .row .code{flex:1;font-family:var(--mono);font-size:15px;letter-spacing:.02em;word-break:break-all}
  .row .st{font-size:11.5px;padding:3px 9px;border-radius:20px;white-space:nowrap}
  .st.sent{background:var(--ok-dim);color:#7fd6a5}
  .st.wait{background:#2f3439;color:var(--muted)}
  .st.fail{background:var(--bad-dim);color:#f0949a}
  .row .retry{font-size:12px;padding:5px 11px;border-radius:7px}

  .count{padding:9px 15px;font-size:12.5px;color:var(--muted);border-bottom:1px solid var(--line);flex:0 0 auto}
  .count b{color:var(--text);font-weight:600}

  .fatal{margin:15px;padding:14px 16px;background:var(--bad-dim);border:1px solid #4d2b2e;border-radius:10px;font-size:13.5px}
  .fatal b{display:block;margin-bottom:5px}
</style>
</head>
<body>

<div class="bar">
  <span class="dot" id="dot"></span>
  <div class="who">
    <b id="whoName">Menghubungkan…</b>
    <span id="whoSub">memeriksa sesi scan</span>
  </div>
</div>

<div class="view">
  <video id="cam" playsinline muted autoplay></video>
  <div class="reticle" id="reticle">
    <div class="frame"></div>
    <div class="line"></div>
    <div class="hint">Posisikan barcode memotong garis merah</div>
  </div>
  <div class="cover" id="cover">
    <button class="primary" id="startBtn">Nyalakan Kamera</button>
    <p id="coverText">Safari akan meminta izin kamera. Pilih Izinkan.</p>
  </div>
</div>

<div class="ctl">
  <button class="wide" id="torchBtn" disabled>Senter</button>
  <button class="wide primary" id="doneBtn">Selesai</button>
</div>

<div class="count" id="count">Belum ada tembakan.</div>
<div class="list" id="list"><div class="empty">Hasil tembakan muncul di sini.</div></div>

<script src="https://cdn.jsdelivr.net/npm/@zxing/library@0.21.3/umd/index.min.js"></script>
<script>
(function () {
  'use strict';

  /* ------------------------------------------------------------------
     Sesi diambil dari FRAGMENT (#), bukan query (?). Bagian setelah #
     tidak pernah dikirim ke server dan tidak ikut di header Referer,
     jadi pair code tidak tercecer di log hosting mana pun.
     ------------------------------------------------------------------ */
  var hash = new URLSearchParams(location.hash.replace(/^#/, ''));
  var PAIR = (hash.get('p') || '').trim();
  var EXEC = (hash.get('u') || '').trim();

  var el = function (id) { return document.getElementById(id); };
  var listEl = el('list'), countEl = el('count');
  var rows = [];          // {code, status, at, el}
  var lastCode = '', lastAt = 0;
  var reader = null, track = null, torchOn = false;

  if (!PAIR || !/^https:\/\//.test(EXEC)) {
    return fatal('Halaman ini dibuka langsung',
      'Buka lewat tombol "Scan Kamera" di MB RMS, jangan dari bookmark. Sesi scan-nya dibuat di sana.');
  }

  /* ---------------- JSONP: satu-satunya jalur yang bebas CORS ----------------
     Apps Script /exec tidak melayani preflight CORS dengan rapi. <script src>
     bebas dari aturan itu DAN tetap mengembalikan jawaban — beda dengan
     fetch(mode:'no-cors') yang selalu "sukses" tanpa kita tahu isinya. */
  var cbSeq = 0;
  function jsonp(params, done) {
    var name = 'mbsr_' + (Date.now() % 1e7) + '_' + (cbSeq++);
    var s = document.createElement('script');
    var timer = setTimeout(function () { finish({ ok: false, error: 'timeout' }); }, 12000);
    var settled = false;

    function finish(res) {
      if (settled) return;
      settled = true;
      clearTimeout(timer);
      try { delete window[name]; } catch (e) { window[name] = undefined; }
      if (s.parentNode) s.parentNode.removeChild(s);
      done(res);
    }

    window[name] = function (res) { finish(res || { ok: false, error: 'empty' }); };
    var q = Object.keys(params).map(function (k) {
      return encodeURIComponent(k) + '=' + encodeURIComponent(params[k]);
    }).join('&');
    s.src = EXEC + '?' + q + '&cb=' + name;
    s.onerror = function () { finish({ ok: false, error: 'network' }); };
    document.head.appendChild(s);
  }

  /* ---------------- Cek sesi dulu, sebelum minta izin kamera ----------------
     Kalau sesinya sudah mati, lebih baik user tahu sekarang daripada setelah
     menembak sepuluh barang yang tidak ke mana-mana. */
  jsonp({ mbscan: 'ping', p: PAIR }, function (res) {
    if (res && res.ok) {
      el('dot').className = 'dot live';
      el('whoName').textContent = res.operator || 'Sesi aktif';
      el('whoSub').textContent = 'Event ' + (res.eventId || '—') + ' · siap menerima';
    } else {
      el('dot').className = 'dot dead';
      el('whoName').textContent = 'Sesi tidak aktif';
      el('whoSub').textContent = 'buka ulang dari POS';
      el('startBtn').disabled = true;
      el('coverText').textContent =
        (res && res.message) || 'Sesi scan sudah habis atau belum dibuat. Kembali ke MB RMS dan tekan "Scan Kamera" lagi.';
    }
  });

  /* ---------------- Kamera + pembacaan ---------------- */
  el('startBtn').addEventListener('click', startCamera);

  function startCamera() {
    el('startBtn').disabled = true;
    el('coverText').textContent = 'Menyalakan kamera…';

    if (!navigator.mediaDevices || !navigator.mediaDevices.getUserMedia) {
      return fatal('Browser ini tidak mendukung kamera',
        'Pakai Safari (iPad) atau Chrome (Android). Kamera tidak jalan di mode private sebagian browser.');
    }
    if (typeof ZXing === 'undefined') {
      return fatal('Pustaka pembaca barcode gagal dimuat',
        'Periksa koneksi internet, lalu muat ulang halaman ini.');
    }

    // Dibatasi ke format ritel saja. Makin sedikit format yang dicoba,
    // makin cepat tiap frame selesai diperiksa.
    var hints = new Map();
    hints.set(ZXing.DecodeHintType.POSSIBLE_FORMATS, [
      ZXing.BarcodeFormat.EAN_13, ZXing.BarcodeFormat.EAN_8,
      ZXing.BarcodeFormat.UPC_A,  ZXing.BarcodeFormat.UPC_E,
      ZXing.BarcodeFormat.CODE_128, ZXing.BarcodeFormat.CODE_39,
      ZXing.BarcodeFormat.ITF
    ]);
    hints.set(ZXing.DecodeHintType.TRY_HARDER, true);

    reader = new ZXing.BrowserMultiFormatReader(hints, 220);

    reader.decodeFromConstraints(
      { video: { facingMode: { ideal: 'environment' }, width: { ideal: 1280 }, height: { ideal: 960 } } },
      el('cam'),
      function (result, err) {
        if (result) onDecode(result.getText());
      }
    ).then(function () {
      el('cover').classList.add('hide');
      el('reticle').classList.add('on');
      setupTorch();
    }).catch(function (e) {
      var n = String(e && e.name || '');
      if (n === 'NotAllowedError') {
        fatal('Izin kamera ditolak',
          'iPad: Settings → Safari → Camera → Ask/Allow. Lalu muat ulang halaman ini. Kalau pernah menolak untuk situs ini, hapus dulu lewat Settings → Safari → Advanced → Website Data.');
      } else if (n === 'NotFoundError' || n === 'OverconstrainedError') {
        fatal('Kamera belakang tidak ditemukan', 'Perangkat ini mungkin hanya punya kamera depan.');
      } else {
        fatal('Kamera gagal dinyalakan', String(e && e.message || e));
      }
    });
  }

  function setupTorch() {
    try {
      var stream = el('cam').srcObject;
      track = stream && stream.getVideoTracks()[0];
      var caps = track && track.getCapabilities && track.getCapabilities();
      if (caps && caps.torch) {
        el('torchBtn').disabled = false;
        el('torchBtn').addEventListener('click', function () {
          torchOn = !torchOn;
          track.applyConstraints({ advanced: [{ torch: torchOn }] })
            .then(function () { el('torchBtn').textContent = torchOn ? 'Senter mati' : 'Senter'; })
            .catch(function () { el('torchBtn').disabled = true; });
        });
      } else {
        el('torchBtn').textContent = 'Senter —';
      }
    } catch (e) { /* senter memang tidak ada di banyak iPad */ }
  }

  /* Peredam pantulan: kamera membaca frame yang sama berkali-kali per detik.
     Kode yang sama dalam 1,6 detik dianggap satu tembakan. Lewat dari itu
     dianggap sengaja — kasir memang bisa menjual 2 barang identik. */
  function onDecode(code) {
    var now = Date.now();
    if (code === lastCode && now - lastAt < 1600) return;
    lastCode = code; lastAt = now;
    beep();
    if (navigator.vibrate) { try { navigator.vibrate(35); } catch (e) {} }
    push(code);
  }

  function push(code) {
    var row = { code: code, status: 'wait' };
    rows.unshift(row);
    render();
    send(row);
  }

  function send(row) {
    row.status = 'wait';
    render();
    jsonp({ mbscan: 'push', p: PAIR, c: row.code }, function (res) {
      row.status = (res && res.ok) ? 'sent' : 'fail';
      row.note = (res && res.message) || (res && res.error) || '';
      render();
    });
  }

  function render() {
    var sent = rows.filter(function (r) { return r.status === 'sent'; }).length;
    var fail = rows.filter(function (r) { return r.status === 'fail'; }).length;
    countEl.innerHTML = rows.length
      ? '<b>' + sent + '</b> terkirim' + (fail ? ' · <b>' + fail + '</b> gagal' : '') + ' dari ' + rows.length + ' tembakan'
      : 'Belum ada tembakan.';

    if (!rows.length) { listEl.innerHTML = '<div class="empty">Hasil tembakan muncul di sini.</div>'; return; }

    listEl.innerHTML = '';
    rows.forEach(function (r, i) {
      var d = document.createElement('div');
      d.className = 'row';
      var label = r.status === 'sent' ? 'terkirim' : r.status === 'wait' ? 'mengirim…' : 'gagal';
      d.innerHTML = '<span class="code"></span><span class="st ' + r.status + '">' + label + '</span>';
      d.querySelector('.code').textContent = r.code;
      if (r.status === 'fail') {
        var b = document.createElement('button');
        b.className = 'retry';
        b.textContent = 'Ulangi';
        b.addEventListener('click', function () { send(r); });
        d.appendChild(b);
      }
      listEl.appendChild(d);
    });
  }

  /* Nada pendek sebagai ganti bunyi scanner. Dibuat sendiri lewat WebAudio
     supaya tidak ada berkas suara yang harus ikut di-host. */
  var actx = null;
  function beep() {
    try {
      actx = actx || new (window.AudioContext || window.webkitAudioContext)();
      if (actx.state === 'suspended') actx.resume();
      var o = actx.createOscillator(), g = actx.createGain();
      o.type = 'square'; o.frequency.value = 1720;
      g.gain.setValueAtTime(0.05, actx.currentTime);
      g.gain.exponentialRampToValueAtTime(0.0001, actx.currentTime + 0.09);
      o.connect(g); g.connect(actx.destination);
      o.start(); o.stop(actx.currentTime + 0.1);
    } catch (e) {}
  }

  /* ---------------- Selesai ---------------- */
  el('doneBtn').addEventListener('click', function () {
    var pending = rows.filter(function (r) { return r.status !== 'sent'; }).length;
    if (pending && !confirm(pending + ' tembakan belum terkirim dan akan hilang. Tetap tutup?')) return;
    stopCamera();
    window.close();          // berhasil hanya kalau tab ini dibuka oleh skrip
    el('cover').classList.remove('hide');
    el('reticle').classList.remove('on');
    el('startBtn').style.display = 'none';
    el('coverText').textContent = 'Selesai. Kembali ke tab MB RMS — hasil scan akan masuk ke keranjang otomatis.';
  });

  function stopCamera() {
    try { if (reader) reader.reset(); } catch (e) {}
    try {
      var s = el('cam').srcObject;
      if (s) s.getTracks().forEach(function (t) { t.stop(); });
    } catch (e) {}
  }
  window.addEventListener('pagehide', stopCamera);

  function fatal(title, body) {
    var box = document.createElement('div');
    box.className = 'fatal';
    box.innerHTML = '<b></b><span></span>';
    box.querySelector('b').textContent = title;
    box.querySelector('span').textContent = body;
    el('cover').innerHTML = '';
    el('cover').appendChild(box);
    el('cover').classList.remove('hide');
  }
})();
</script>
</body>
</html>

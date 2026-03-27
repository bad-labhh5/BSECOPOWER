<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BS ECO-POWER | Smart City Brescia</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" />
    <style>
        :root { --primary: #2ecc71; --dark: #1a1a1a; --white: #ffffff; --gray: #f4f7f6; --accent: #005aab; }
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { font-family: 'Segoe UI', sans-serif; scroll-behavior: smooth; background: var(--gray); color: var(--dark); }
        
        nav { background: var(--white); height: 70px; display: flex; justify-content: space-between; align-items: center; padding: 0 5%; position: fixed; width: 100%; top: 0; z-index: 1000; box-shadow: 0 2px 10px rgba(0,0,0,0.1); }
        .logo { font-weight: 800; color: var(--primary); font-size: 1.4rem; text-decoration: none; }
        .nav-links a { text-decoration: none; color: var(--dark); margin-left: 15px; font-weight: 600; font-size: 0.9rem; }

        section { padding: 100px 5% 60px; }
        .section-title { text-align: center; margin-bottom: 40px; }
        .section-title h2 { font-size: 2.2rem; color: var(--dark); }

        /* App Mockup */
        .app-flex { display: flex; flex-wrap: wrap; align-items: center; justify-content: center; gap: 50px; }
        .phone { width: 280px; height: 550px; background: #000; border: 10px solid #333; border-radius: 35px; overflow: hidden; position: relative; box-shadow: 0 20px 40px rgba(0,0,0,0.2); }
        .screen { background: white; height: 100%; display: flex; flex-direction: column; font-size: 0.8rem; }
        .screen-h { background: var(--primary); color: white; padding: 15px; text-align: center; font-weight: bold; }

        /* Pricing */
        .pricing { display: flex; flex-wrap: wrap; justify-content: center; gap: 20px; }
        .p-card { background: white; padding: 30px; border-radius: 15px; width: 280px; text-align: center; border: 1px solid #ddd; }
        .p-card.feat { border: 2px solid var(--primary); transform: scale(1.05); }
        .price { font-size: 2.5rem; font-weight: 800; color: var(--primary); margin: 15px 0; }

        /* Questionario */
        .survey-container { background: var(--dark); color: white; border-radius: 20px; padding: 40px; display: flex; flex-wrap: wrap; align-items: center; gap: 30px; }
        .qr-area { background: white; padding: 20px; border-radius: 15px; text-align: center; color: black; min-width: 200px; }
        .qr-area img { max-width: 150px; margin-bottom: 10px; }

        /* Sponsor */
        .sponsors { display: flex; justify-content: center; gap: 40px; flex-wrap: wrap; align-items: center; padding: 40px 0; filter: grayscale(1); opacity: 0.6; }

        #map { height: 450px; border-radius: 20px; border: 2px solid #ddd; }
        footer { background: var(--dark); color: white; text-align: center; padding: 40px; margin-top: 40px; }
    </style>
</head>
<body>

<nav>
    <a href="#" class="logo">⚡ BS ECO-POWER</a>
    <div class="nav-links">
        <a href="#progetto">PROGETTO</a>
        <a href="#prezzi">PREZZI</a>
        <a href="#sondaggio">SONDAGGIO</a>
        <a href="#mappa">MAPPA 87 SPOTS</a>
    </div>
</nav>

<section id="progetto" class="app-flex">
    <div class="phone">
        <div class="screen">
            <div class="screen-h">BS ECO-POWER APP</div>
            <div style="padding: 20px;">
                <p>Benvenuto a Brescia! 📍</p>
                <div style="background:#f0f0f0; padding:10px; margin:15px 0; border-radius:8px;">
                    <b>Stazione più vicina:</b><br>Piazza Loggia - Libera
                </div>
                <button style="width:100%; background:var(--primary); color:white; border:none; padding:12px; margin-top:20px; border-radius:5px; font-weight:bold;">AVVIA RICARICA SMART</button>
            </div>
        </div>
    </div>
    <div style="max-width: 500px;">
        <h2>L'Energia di Brescia nelle tue mani</h2>
        <p>BS ECO-POWER è una rete di stazioni ricarica intelligenti distribuite a Brescia[cite: 3].</p>
        <div style="margin-top: 20px;">
            <p>🔌 <b>Spot mobilità elettrica:</b> ricarica per monopattini e bici[cite: 5].</p>
            <p>🪑 <b>Spot relax & ricarica:</b> panchine con prese per smartphone e PC[cite: 6].</p>
            <p>🌱 <b>Obiettivo:</b> trasformare Brescia in una città sostenibile e a misura di giovane[cite: 7].</p>
        </div>
    </div>
</section>

<section id="prezzi" style="background: #fff;">
    <div class="section-title"><h2>Modello di Business</h2></div>
    <div class="pricing">
        <div class="p-card">
            <h3>On-Demand</h3>
            <div class="price">0,15€<small>/min</small></div>
            <p>Ricarica occasionale[cite: 45].<br>Pagamento diretto via App.</p>
        </div>
        <div class="p-card feat">
            <h3>Abbonamento Mensile</h3>
            <div class="price">4,99€</div>
            <p>Accesso illimitato agli spot relax e ricarica veloce[cite: 46].</p>
        </div>
        <div class="p-card">
            <h3>Abbonamento Annuale</h3>
            <div class="price">49,99€</div>
            <p>Risparmio massimo per pendolari, studenti e turisti[cite: 31, 32].</p>
        </div>
    </div>
</section>

<section id="sondaggio">
    <div class="survey-container">
        <div style="flex: 2;">
            <h2>Partecipa al Sondaggio</h2>
            <p>La tua opinione è fondamentale per la Fase 1 del nostro piano di sviluppo[cite: 76, 77].</p>
            <p style="margin-top:10px;">Scansiona il QR Code per accedere al questionario ufficiale e aiutarci a combattere la mancanza di punti di ricarica pubblici[cite: 10].</p>
        </div>
        <div class="qr-area">
            <img src="https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=https://docs.google.com/forms/d/e/1FAIpQLSchYz8rto6NxiYO5to0aoNEwHhDyFOAAhKue2GcJVCwWr0gcQ/viewform?usp=header" alt="QR Sondaggio">
            <p><a href="https://docs.google.com/forms/d/e/1FAIpQLSchYz8rto6NxiYO5to0aoNEwHhDyFOAAhKue2GcJVCwWr0gcQ/viewform?usp=header" target="_blank" style="color:var(--primary); text-decoration:none; font-weight:bold;">VAI AL MODULO</a></p>
        </div>
    </div>
</section>

<section id="sponsor">
    <div class="section-title"><h3>Partner Strategici</h3></div>
    <div class="sponsors">
        <h3 style="color: #ea5b0c;">A2A</h3>
        <h3 style="color: #e30613;">ENEL</h3>
        <h3 style="color: #0082c1;">Brescia Mobilità [cite: 63]</h3>
        <h3>Comune di Brescia [cite: 62]</h3>
    </div>
</section>

<section id="mappa">
    <div class="section-title"><h2>87 Stazioni Pilota [cite: 79, 81]</h2></div>
    <div id="map"></div>
</section>

<footer>
    <p><b>BS ECO-POWER</b> - “L'energia della città, sempre con te” [cite: 74]</p>
</footer>

<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script>
    const map = L.map('map').setView([45.5415, 10.2118], 13);
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(map);
    for (let i = 1; i <= 87; i++) {
        let lat = 45.5415 + (Math.random() - 0.5) * 0.05;
        let lng = 10.2118 + (Math.random() - 0.5) * 0.06;
        L.marker([lat, lng]).addTo(map).bindPopup(`Stazione BS ECO-POWER #${i}`);
    }
</script>

</body>
</html>

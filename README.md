# Grow-a-Garden-shop-pets
Tienda no oficial de roblox.Venta de pets
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Tienda Grow a Garden</title>
<style>
  body {
    margin: 0;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #0d0d0d;
    color: white;
  }
  #inicio-screen {
    text-align: center;
    padding: 80px 20px 40px 20px;
    max-width: 500px;
    margin: 50px auto 0 auto;
  }
  #inicio-screen h1 {
    font-size: 2.5em;
    margin-bottom: 25px;
    font-weight: 900;
    letter-spacing: 1px;
  }
  #entrar-btn {
    background-color: #ffcc00;
    color: #111;
    padding: 15px 30px;
    font-size: 18px;
    font-weight: bold;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    box-shadow: 0 0 15px #ffcc00;
    transition: background-color 0.3s ease;
  }
  #entrar-btn:hover {
    background-color: #ffe066;
  }
  header {
    display: none;
    background: linear-gradient(90deg, #ffcc00, #ffaa00);
    color: #000;
    padding: 20px;
    font-size: 2em;
    font-weight: bold;
    justify-content: space-between;
    align-items: center;
    display: flex;
  }
  #cart-button {
    background-color: #000;
    border: 2px solid #ffcc00;
    padding: 10px;
    border-radius: 8px;
    color: #ffcc00;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  #cart-button:hover {
    background-color: #ffcc00;
    color: #000;
  }
  #history-button {
    background-color: #000;
    border: 2px solid #ffcc00;
    padding: 10px 14px;
    border-radius: 8px;
    color: #ffcc00;
    font-weight: bold;
    cursor: pointer;
    margin-left: 15px;
    font-size: 0.7em;
    transition: all 0.3s ease;
  }
  #history-button:hover {
    background-color: #ffcc00;
    color: #000;
  }
  .store {
    display: none;
    flex-wrap: wrap;
    justify-content: center;
    padding: 20px;
  }
  .product-item {
    background-color: #1e1e1e;
    border: 2px solid #ffcc00;
    border-radius: 10px;
    width: 220px;
    margin: 10px;
    padding: 15px;
    text-align: center;
  }
  .product-item img {
    width: 100%;
    border-radius: 8px;
  }
  .product-item h3 {
    margin: 10px 0;
  }
  .price {
    color: #ffcc00;
    font-size: 1.2em;
    margin: 10px 0;
  }
  .add-to-cart {
    background-color: transparent;
    border: 2px solid #ffcc00;
    color: #ffcc00;
    padding: 10px;
    border-radius: 6px;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  .add-to-cart:hover {
    background-color: #ffcc00;
    color: #000;
  }
  /* Modal carrito */
  #cart-modal {
    display: none;
    position: fixed;
    top: 50%;
    left: 50%;
    width: 360px;
    max-width: 90vw;
    max-height: 80vh;
    overflow-y: auto;
    background-color: #111;
    padding: 20px;
    border-radius: 12px;
    transform: translate(-50%, -50%);
    z-index: 1000;
    box-shadow: 0 0 15px #ffcc00;
  }
  #cart-items {
    margin-bottom: 15px;
  }
  .cart-item {
    border-bottom: 1px solid #444;
    padding: 8px 0;
    font-size: 1em;
    display: flex;
    justify-content: space-between;
  }
  #cart-total {
    font-weight: bold;
    text-align: right;
    color: #ffcc00;
    margin-bottom: 10px;
  }
  /* Modal fondo oscuro */
  #modal-bg {
    display: none;
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: rgba(0,0,0,0.7);
    z-index: 900;
  }
  #checkout-form {
    display: none;
    position: fixed;
    top: 50%;
    left: 50%;
    width: 360px;
    max-width: 90vw;
    max-height: 90vh;
    overflow-y: auto;
    background-color: #222;
    padding: 20px;
    margin-top: 0;
    border-radius: 8px;
    transform: translate(-50%, -50%);
    z-index: 1100;
    box-shadow: 0 0 15px #ffcc00;
  }
  input, select, textarea {
    width: 100%;
    padding: 10px;
    margin-top: 10px;
    border-radius: 5px;
    border: none;
    background-color: #333;
    color: white;
    resize: none;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: 1em;
  }
  button.submit-btn {
    background-color: #ffcc00;
    color: #000;
    font-weight: bold;
    padding: 10px 20px;
    border: none;
    margin-top: 10px;
    cursor: pointer;
    border-radius: 6px;
    width: 100%;
    font-size: 1.1em;
    transition: background-color 0.3s ease;
  }
  button.submit-btn:hover {
    background-color: #e6b800;
  }
  #discord-btn {
    margin-top: 20px;
    display: block;
    background-color: #7289DA;
    color: white;
    padding: 10px 20px;
    border-radius: 8px;
    text-decoration: none;
    font-weight: bold;
    text-align: center;
  }
  #payment-instructions {
    background: #222;
    border: 2px solid #ffcc00;
    border-radius: 8px;
    padding: 10px 15px;
    margin-top: 15px;
    font-size: 0.95em;
    color: #ffcc00;
    white-space: pre-line;
  }

  /* Panel historial */
  #history-panel {
    position: fixed;
    top: 10%;
    right: 10px;
    width: 300px;
    max-height: 80vh;
    background-color: #111;
    border: 2px solid #ffcc00;
    border-radius: 12px;
    padding: 15px;
    overflow-y: auto;
    color: #ffcc00;
    box-shadow: 0 0 20px #ffcc00;
    display: none;
    z-index: 1250;
  }
  #history-panel h3 {
    margin-top: 0;
    font-weight: bold;
    text-align: center;
  }
  .history-entry {
    border-bottom: 1px solid #444;
    padding: 8px 5px;
    font-size: 0.9em;
    white-space: pre-wrap;
  }
  #close-history {
    cursor: pointer;
    color: #ffcc00;
    text-align: right;
    font-weight: bold;
    margin-bottom: 8px;
  }

  /* Mensaje bonito temporal */
  #message-box {
    position: fixed;
    top: 15px;
    left: 50%;
    transform: translateX(-50%);
    background: #ffcc00;
    color: #000;
    padding: 12px 25px;
    border-radius: 25px;
    font-weight: bold;
    font-size: 1.1em;
    box-shadow: 0 0 15px #ffcc00;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.4s ease;
    z-index: 1300;
  }
</style>
</head>
<body>

<!-- Mensaje bonito temporal -->
<div id="message-box"></div>

<div id="inicio-screen">
  <h1>🌱 Bienvenido a la Tienda Grow a Garden</h1>
  <button id="entrar-btn" onclick="showStore()">Entrar a la tienda</button>
</div>

<header id="main-header" style="display:none;">
  <div>Tienda Grow a Garden</div>
  <div>
    <button id="cart-button" onclick="toggleCart()">🛒 Ver Carrito (<span id="cart-count">0</span>)</button>
    <button id="history-button" onclick="toggleHistoryPanel()">Historial</button>
  </div>
</header>

<div class="store" id="store" style="display:none;">
  <div class="product-item">
    <img src="https://via.placeholder.com/250?text=Candy+Blossom" alt="Candy Blossom" />
    <h3>Candy Blossom</h3>
    <p class="price">$3.00</p>
    <button class="add-to-cart" onclick="addToCart('Candy Blossom', 3.00)">Agregar al carrito</button>
  </div>
  <div class="product-item">
    <img src="https://via.placeholder.com/250?text=Mapache" alt="Mapache" />
    <h3>Mapache</h3>
    <p class="price">$15.00</p>
    <button class="add-to-cart" onclick="addToCart('Mapache', 15.00)">Agregar al carrito</button>
  </div>
  <div class="product-item">
    <img src="https://via.placeholder.com/250?text=Disco+Bee" alt="Disco Bee" />
    <h3>Disco Bee</h3>
    <p class="price">$15.00</p>
    <button class="add-to-cart" onclick="addToCart('Disco Bee', 15.00)">Agregar al carrito</button>
  </div>
  <div class="product-item">
    <img src="https://via.placeholder.com/250?text=Abeja+Reina" alt="Abeja Reina" />
    <h3>Abeja Reina</h3>
    <p class="price">$8.00</p>
    <button class="add-to-cart" onclick="addToCart('Abeja Reina', 8.00)">Agregar al carrito</button>
  </div>
</div>

<div id="modal-bg" onclick="closeAllModals()"></div>

<div id="cart-modal">
  <h2>🛒 Carrito</h2>
  <div id="cart-items"></div>
  <p id="cart-total"></p>
  <button class="submit-btn" onclick="showCheckout()">Finalizar Compra</button>
  <a id="discord-btn" href="https://discord.gg/geNNDKac" target="_blank" rel="noopener noreferrer">Reclamar pedido por Discord</a>
</div>

<div id="checkout-form">
  <h3>📩 Enviar Pedido</h3>
  <form id="order-form" action="https://formsubmit.co/growagardentrades100@gmail.com" method="POST" onsubmit="return prepareOrder()">
    <input type="hidden" name="_subject" value="Nuevo pedido" />
    <input type="hidden" name="_captcha" value="false" />
    <input type="text" name="Usuario Roblox" placeholder="Usuario de Roblox" required />
    <input type="text" name="Contacto" placeholder="Correo o Discord" required />
    <select name="Método de pago" required>
      <option value="">Seleccione método de pago</option>
      <option value="PayPal">PayPal</option>
      <option value="Nequi">Nequi</option>
      <option value="Otro">Otro</option>
    </select>
    <textarea name="Productos" id="checkout-products" readonly rows="5" required></textarea>
    <input type="hidden" name="Código de pedido" id="order-code-input" />
    <div id="payment-instructions">
      <strong>Instrucciones de pago:</strong>
      <br>
      1. Envía el dinero a esta cuenta Nequi: <strong>99999999</strong>.
      <br>
      2. Envía tu usuario y comprobante a Discord: <a href="https://discord.gg/geNNDKac" target="_blank" style="color:#ffcc00; text-decoration: underline;">discord.gg/geNNDKac</a>.
      <br>
      3. Recibe tu mascota en Grow a Garden tras la confirmación.
      <br><br>
      <strong style="color:#ff4444;">IMPORTANTE:</strong> El código de pedido es único y <u>NO DEBE compartirse con nadie más</u>.
    </div>
    <button class="submit-btn" type="submit">Enviar Pedido</button>
  </form>
</div>

<div id="history-panel">
  <div id="close-history" onclick="toggleHistoryPanel()">✖ Cerrar</div>
  <h3>Historial de pedidos</h3>
  <div id="history-entries">
    <!-- Aquí se cargan los pedidos -->
  </div>
</div>

<script>
  let cart = [];
  let firstPurchase = true;

  function showStore() {
    document.getElementById('inicio-screen').style.display = 'none';
    document.getElementById('store').style.display = 'flex';
    document.getElementById('main-header').style.display = 'flex';
  }

  function showMessage(text) {
    const box = document.getElementById('message-box');
    box.textContent = text;
    box.style.opacity = '1';
    box.style.pointerEvents = 'auto';
    clearTimeout(box.timeout);
    box.timeout = setTimeout(() => {
      box.style.opacity = '0';
      box.style.pointerEvents = 'none';
    }, 3000);
  }

  function addToCart(name, price) {
    cart.push({ name, price });
    updateCartCount();
    showMessage(`✅ ${name} agregado al carrito`);
  }

  function updateCartCount() {
    document.getElementById('cart-count').textContent = cart.length;
  }

  function toggleCart() {
    const modal = document.getElementById('cart-modal');
    const bg = document.getElementById('modal-bg');
    if (modal.style.display === 'block') {
      modal.style.display = 'none';
      bg.style.display = 'none';
      document.getElementById('checkout-form').style.display = 'none';
      document.getElementById('history-button').style.display = 'inline-block';
    } else {
      if (cart.length === 0) {
        alert('El carrito está vacío');
        return;
      }
      updateCartView();
      modal.style.display = 'block';
      bg.style.display = 'block';
      document.getElementById('history-button').style.display = 'inline-block';
    }
  }

  function updateCartView() {
    const itemsDiv = document.getElementById('cart-items');
    const totalEl = document.getElementById('cart-total');
    const textarea = document.getElementById('checkout-products');
    itemsDiv.innerHTML = '';
    textarea.value = '';
    let total = 0;

    const counted = {};
    cart.forEach(item => {
      counted[item.name] = counted[item.name] || { qty: 0, price: item.price };
      counted[item.name].qty++;
    });

    for (const [name, data] of Object.entries(counted)) {
      itemsDiv.innerHTML += `<div class='cart-item'>${name} x${data.qty} <span>$${(data.price * data.qty).toFixed(2)}</span></div>`;
      textarea.value += `${name} x${data.qty} - $${(data.price * data.qty).toFixed(2)}\n`;
      total += data.price * data.qty;
    }

    if (firstPurchase && cart.length > 0) {
      const discounted = total * 0.75;
      totalEl.textContent = `Total con 25% de descuento: $${discounted.toFixed(2)}`;
    } else {
      totalEl.textContent = `Total: $${total.toFixed(2)}`;
    }
  }

  function showCheckout() {
    if (cart.length === 0) {
      alert('El carrito está vacío');
      return;
    }
    document.getElementById('checkout-form').style.display = 'block';
    document.getElementById('cart-modal').style.display = 'none';
    document.getElementById('modal-bg').style.display = 'block';
    document.getElementById('history-button').style.display = 'none';
  }

  function generateOrderCode() {
    const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
    let code = '';
    for (let i = 0; i < 8; i++) {
      code += chars.charAt(Math.floor(Math.random() * chars.length));
    }
    return code;
  }

  function prepareOrder() {
    if (cart.length === 0) {
      alert('Carrito vacío. Agrega productos antes de finalizar.');
      return false;
    }
    const code = generateOrderCode();
    document.getElementById('order-code-input').value = code;

    // Guardar en historial localStorage
    const history = JSON.parse(localStorage.getItem('orderHistory')) || [];
    const orderDate = new Date().toLocaleString();
    const productsText = document.getElementById('checkout-products').value;

    history.push({
      code: code,
      date: orderDate,
      products: productsText
    });
    localStorage.setItem('orderHistory', JSON.stringify(history));

    // Limpiar carrito
    cart = [];
    updateCartCount();
    closeAllModals();

    showMessage(`✅ Pedido enviado. Código: ${code}. No compartas este código con nadie.`);

    firstPurchase = false;

    return true;
  }

  function toggleHistoryPanel() {
    const panel = document.getElementById('history-panel');
    if (panel.style.display === 'block') {
      panel.style.display = 'none';
    } else {
      updateHistoryPanel();
      panel.style.display = 'block';
    }
  }

  function updateHistoryPanel() {
    const container = document.getElementById('history-entries');
    let history = JSON.parse(localStorage.getItem('orderHistory')) || [];
    if (history.length === 0) {
      container.innerHTML = '<p>No hay pedidos realizados aún.</p>';
      return;
    }
    container.innerHTML = '';
    history.slice().reverse().forEach(order => {
      container.innerHTML += `
        <div class="history-entry">
          <strong>Código:</strong> ${order.code}<br>
          <strong>Fecha:</strong> ${order.date}<br>
          <strong>Productos:</strong><br>${order.products.replace(/\n/g, '<br>')}
        </div>
      `;
    });
  }

  function closeAllModals() {
    document.getElementById('cart-modal').style.display = 'none';
    document.getElementById('checkout-form').style.display = 'none';
    document.getElementById('modal-bg').style.display = 'none';
    document.getElementById('history-button').style.display = 'inline-block';
  }
</script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>OG Movie Shop</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0; padding: 0;
      background: #f4f4f4;
      color: #333;
    }
    header {
      background: #222;
      color: #fff;
      text-align: center;
      padding: 20px;
      font-size: 2rem;
    }
    nav {
      background: #333;
      display: flex;
      justify-content: center;
      padding: 10px;
    }
    nav a {
      color: #fff;
      text-decoration: none;
      margin: 0 15px;
      font-weight: bold;
    }
    nav a:hover {
      text-decoration: underline;
    }
    main {
      max-width: 900px;
      margin: 20px auto;
      padding: 0 15px;
    }
    section {
      margin-bottom: 40px;
    }
    h2 {
      border-bottom: 2px solid #222;
      padding-bottom: 5px;
    }
    .products {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
      gap: 20px;
      margin-top: 20px;
    }
    .product {
      background: white;
      padding: 10px;
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
      text-align: center;
    }
    .product img {
      max-width: 100%;
      border-radius: 6px;
    }
    .product-title {
      font-weight: bold;
      margin-top: 10px;
    }
    .product-price {
      color: #27ae60;
      font-weight: bold;
    }
    form {
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin-top: 15px;
    }
    input, textarea, button {
      padding: 10px;
      font-size: 1rem;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      background: #222;
      color: white;
      font-weight: bold;
      cursor: pointer;
    }
    button:hover {
      background: #444;
    }
    iframe {
      width: 100%;
      height: 300px;
      border: none;
      border-radius: 8px;
      margin-top: 15px;
    }
    footer {
      background: #222;
      color: white;
      text-align: center;
      padding: 15px;
      margin-top: 50px;
    }
    @media (max-width: 600px) {
      nav {
        flex-direction: column;
        align-items: center;
      }
      nav a {
        margin: 8px 0;
      }
    }
  </style>
</head>
<body>

<header>OG Movie Shop</header>

<nav>
  <a href="#movies">Movies & Series</a>
  <a href="#add">Add New</a>
  <a href="#contact">Contact</a>
</nav>

<main>
  <!-- Movies Section -->
  <section id="movies">
    <h2>Latest Movies & Series</h2>
    <div class="products" id="productList">
      <div class="product">
        <img src="https://m.media-amazon.com/images/I/51v5ZpFyaFL._AC_SY679_.jpg" alt="Inception">
        <div class="product-title">Inception (Movie)</div>
        <div class="product-price">Ksh 30</div>
      </div>
      <div class="product">
        <img src="https://upload.wikimedia.org/wikipedia/en/3/38/Stranger_Things_logo.png" alt="Stranger Things">
        <div class="product-title">Stranger Things (Series)</div>
        <div class="product-price">Ksh 30 per season</div>
      </div>
    </div>
  </section>

  <!-- Add Movie Section -->
  <section id="add">
    <h2>Add New Movie or Series</h2>
    <form id="addForm">
      <input type="text" id="title" placeholder="Title (e.g. Avengers)" required>
      <input type="text" id="type" placeholder="Type (Movie or Series)" required>
      <input type="text" id="image" placeholder="Image URL (optional)">
      <button type="submit">Add</button>
    </form>
  </section>

  <!-- Contact Section -->
  <section id="contact">
    <h2>Contact & Location</h2>
    <p><strong>Phone:</strong> +254112703113</p>
    <p><strong>Email:</strong> barakachrispus2@gmail.com</p>
    <p><strong>Location:</strong> Malindi, Kenya</p>
    <p><strong>Opening Hours:</strong> Mon-Sun, 9am - 10pm</p>

    <h3>Send Message via Email</h3>
    <form action="mailto:barakachrispus2@gmail.com" method="post" enctype="text/plain">
      <input type="text" name="name" placeholder="Your Name" required>
      <textarea name="message" placeholder="Your Message" required></textarea>
      <button type="submit">Send Email</button>
    </form>

    <h3>Send Message via WhatsApp</h3>
    <form onsubmit="sendToWhatsApp(event)">
      <input type="text" id="whatsName" placeholder="Your Name" required>
      <textarea id="whatsMsg" placeholder="Your Message" required></textarea>
      <button type="submit">Send WhatsApp</button>
    </form>

    <h3>Map Location</h3>
    <iframe src="https://www.google.com/maps?q=Malindi+Kenya&output=embed" allowfullscreen></iframe>
  </section>
</main>

<footer>
  &copy; 2025 OG Movie Shop. All rights reserved.
</footer>

<script>
  const productList = document.getElementById("productList");

  document.getElementById("addForm").addEventListener("submit", function(e) {
    e.preventDefault();
    const title = document.getElementById("title").value;
    const type = document.getElementById("type").value;
    const image = document.getElementById("image").value || "https://via.placeholder.com/180";
    const price = type.toLowerCase() === "series" ? "Ksh 30 per season" : "Ksh 30";

    const div = document.createElement("div");
    div.className = "product";
    div.innerHTML = `
      <img src="${image}" alt="${title}">
      <div class="product-title">${title} (${type})</div>
      <div class="product-price">${price}</div>
    `;
    productList.appendChild(div);
    this.reset();
  });

  function sendToWhatsApp(e) {
    e.preventDefault();
    const name = document.getElementById("whatsName").value;
    const msg = document.getElementById("whatsMsg").value;
    const phone = "254112703113";
    const url = `https://wa.me/${phone}?text=${encodeURIComponent("Hello, my name is " + name + ". " + msg)}`;
    window.open(url, "_blank");
  }
</script>

</body>
</html>

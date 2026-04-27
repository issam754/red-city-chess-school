<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Red City Chess School</title>

<style>
body {
    margin: 0;
    font-family: Arial;
    background: #0f0f0f;
    color: white;
}

/* HEADER */
header {
    background: linear-gradient(45deg, #8B0000, #ff0000);
    text-align: center;
    padding: 30px;
}

nav {
    display: flex;
    justify-content: center;
    background: #1a1a1a;
    flex-wrap: wrap;
}

nav a {
    padding: 15px;
    color: white;
    text-decoration: none;
}

nav a:hover {
    background: red;
}

/* SECTION */
section {
    padding: 50px;
    text-align: center;
}

/* GALLERY */
.gallery img {
    width: 200px;
    margin: 10px;
    border-radius: 10px;
}

/* PRICES */
.prices {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px;
}

.card {
    background: #1a1a1a;
    padding: 20px;
    border-radius: 15px;
    width: 220px;
}

/* BUTTON */
button {
    padding: 10px 20px;
    background: red;
    border: none;
    color: white;
    cursor: pointer;
    border-radius: 5px;
}

button:hover {
    background: darkred;
}

/* FORM */
input, textarea {
    width: 80%;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
    border: none;
}

/* FOOTER */
footer {
    background: black;
    padding: 15px;
}
</style>

</head>

<body>

<header>
    <h1>♟️ Red City Chess School</h1>
    <p>Deviens un maître des échecs</p>
</header>

<nav>
    <a href="#about">À propos</a>
    <a href="#gallery">Photos</a>
    <a href="#prices">Prix</a>
    <a href="#location">Localisation</a>
    <a href="#contact">Contact</a>
</nav>

<section id="about">
    <h2>À propos</h2>
    <p>Une école moderne pour apprendre les échecs à tous les niveaux.</p>
</section>

<section id="gallery">
    <h2>Galerie</h2>

    <input type="file" id="upload" accept="image/*">
    <br><br>

    <div class="gallery" id="galleryContainer"></div>
</section>

<section id="prices">
    <h2>Nos Prix</h2>

    <div class="prices" id="priceContainer"></div>

    <button onclick="addPrice()">Ajouter un prix</button>
</section>

<section id="location">
    <h2>📍 Notre Localisation</h2>

    <iframe
        src="https://www.google.com/maps?q=31.6301491,-8.0738801&hl=fr&z=17&output=embed"
        width="90%"
        height="350"
        style="border:0; border-radius:10px;">
    </iframe>

    <p>
        <a href="https://www.google.com/maps/place/Doja+20+GH+3+n+1+porte+de+marrakech/@31.6303272,-8.0738506"
        target="_blank">
        Ouvrir sur Google Maps
        </a>
    </p>
</section>

    <input type="text" placeholder="Nom"><br>
    <input type="email" placeholder="Email"><br>
    <textarea placeholder="Message"></textarea><br>

    <button onclick="sendMsg()">Envoyer</button>
</section>

<footer>
    <p>© 2026 Red City Chess School</p>
</footer>

<script>

/* GALERIE IMAGE */
document.getElementById("upload").addEventListener("change", function(event) {
    let file = event.target.files[0];
    let reader = new FileReader();

    reader.onload = function(e) {
        let img = document.createElement("img");
        img.src = e.target.result;
        document.getElementById("galleryContainer").appendChild(img);
    }

    if(file) reader.readAsDataURL(file);
});

/* PRIX */
let prices = [
    {name: "Débutant", price: "200 MAD"},
    {name: "Intermédiaire", price: "300 MAD"},
    {name: "Avancé", price: "500 MAD"}
];

function showPrices() {
    let container = document.getElementById("priceContainer");
    container.innerHTML = "";

    prices.forEach(p => {
        let card = `
        <div class="card">
            <h3>${p.name}</h3>
            <p>${p.price}</p>
        </div>`;
        container.innerHTML += card;
    });
}

function addPrice() {
    let name = prompt("Nom du niveau:");
    let price = prompt("Prix:");

    if(name && price) {
        prices.push({name, price});
        showPrices();
    }
}

showPrices();

/* CONTACT */
function sendMsg() {
    alert("Message envoyé !");
}

</script>

</body>
</html>

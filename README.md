<!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nisha Sweet Bite Cookies 🍪</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet"><style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Poppins',sans-serif}
body{background:#fff8f0}
header{background:#6b3e26;color:#fff;padding:15px;text-align:center}
nav{display:flex;justify-content:center;gap:20px;margin-top:10px}
nav a{color:white;text-decoration:none}
.container{padding:20px}

/* Animation */
@keyframes fadeIn{
from{opacity:0;transform:translateY(20px)}
to{opacity:1;transform:translateY(0)}
}

.products{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:20px;margin-top:20px}
.card{
background:#fff;padding:10px;border-radius:12px;
box-shadow:0 0 10px rgba(0,0,0,0.1);
text-align:center;
animation:fadeIn 0.8s ease;
transition:transform 0.3s
}
.card:hover{transform:scale(1.05)}
.card img{
width:100%;height:150px;object-fit:cover;border-radius:10px
}
.card button{margin-top:10px;padding:8px;background:#ff7f50;color:#fff;border:none;border-radius:5px}

.cart{margin-top:30px;background:#fff;padding:20px;border-radius:10px}
.whatsapp{position:fixed;bottom:20px;right:20px;background:#25D366;color:white;padding:12px;border-radius:50px;text-decoration:none}
</style></head><body>
<header>
<h1>🍪 Nisha Sweet Bite Cookies</h1>
<nav>
<a href="#shop">Shop</a>
<a href="#cart">Cart</a>
</nav>
</header><div class="container"><section id="shop">
<h2 style="text-align:center">7 Types of Cookies</h2>
<div class="products" id="products"></div>
</section><section id="cart" class="cart">
<h2>Your Order</h2>
<ul id="cart-items"></ul>
<h3>Total: ₹<span id="total">0</span></h3>
<button onclick="placeOrder()">Place Order</button>
<p id="msg"></p>
</section></div><a class="whatsapp" id="wa" target="_blank">Order via WhatsApp</a>

<script>
let products=[
{name:"Choco Chip",price:100,img:"https://images.unsplash.com/photo-1606312619344-7a9c8b0d5f36?auto=format&fit=crop&w=400&q=60"},
{name:"Butter Cookie",price:80,img:"https://images.unsplash.com/photo-1612197529388-5e6e5b9b5fbd?auto=format&fit=crop&w=400&q=60"},
{name:"Oatmeal",price:90,img:"https://images.unsplash.com/photo-1588195538326-c5b1e9f80a1b?auto=format&fit=crop&w=400&q=60"},
{name:"Dark Chocolate",price:120,img:"https://images.unsplash.com/photo-1548365328-9f547fb0953d?auto=format&fit=crop&w=400&q=60"},
{name:"Peanut Butter",price:110,img:"https://images.unsplash.com/photo-1625944525533-473f1b2b9b8c?auto=format&fit=crop&w=400&q=60"},
{name:"Sugar Cookie",price:70,img:"https://images.unsplash.com/photo-1614707267537-b85aaf00c4b7?auto=format&fit=crop&w=400&q=60"},
{name:"Double Choco",price:130,img:"https://images.unsplash.com/photo-1590080877777-95d5b5b4a1a5?auto=format&fit=crop&w=400&q=60"}
];

let cart=[];

function load(){
let html="";
products.forEach((p,i)=>{
html+=`<div class='card'>
<img src='${p.img}'>
<h3>${p.name}</h3>
<p>₹${p.price}</p>
<button onclick='add(${i})'>Add</button>
</div>`});
document.getElementById("products").innerHTML=html;
}

function add(i){cart.push(products[i]);update();}

function update(){
let list="",total=0;
cart.forEach(i=>{list+=`<li>${i.name} - ₹${i.price}</li>`;total+=i.price});
document.getElementById("cart-items").innerHTML=list;
document.getElementById("total").innerText=total;
}

function placeOrder(){
if(cart.length==0){alert("Cart empty");return;}
document.getElementById("msg").innerText="🎉 Order placed!";

let text=encodeURIComponent("My order: \n"+cart.map(i=>i.name).join(", "));
document.getElementById("wa").href=`https://wa.me/91XXXXXXXXXX?text=${text}`;

cart=[];update();
}

load();
</script></body>
</html>

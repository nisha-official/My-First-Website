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

.box{max-width:400px;margin:auto;background:#fff;padding:20px;border-radius:12px;box-shadow:0 0 10px rgba(0,0,0,0.1)}
.box input{width:100%;padding:10px;margin:8px 0;border-radius:6px;border:1px solid #ccc}
.box button{width:100%;padding:10px;background:#6b3e26;color:#fff;border:none;border-radius:6px}

.products{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:20px;margin-top:20px}
.card{background:#fff;padding:10px;border-radius:10px;box-shadow:0 0 10px rgba(0,0,0,0.1);text-align:center}
.card img{width:100%;height:150px;object-fit:cover;border-radius:10px}
.card button{margin-top:10px;padding:8px;background:#ff7f50;color:#fff;border:none;border-radius:5px}

.cart{margin-top:30px;background:#fff;padding:20px;border-radius:10px}
.status{margin-top:10px;font-weight:bold}

.whatsapp{
position:fixed;bottom:20px;right:20px;
background:#25D366;color:white;padding:12px 16px;border-radius:50px;text-decoration:none;font-weight:bold
}
</style></head><body>
<header>
<h1>🍪 Nisha Sweet Bite Cookies</h1>
<nav>
<a href="#auth">Login</a>
<a href="#shop">Shop</a>
<a href="#cart">Cart</a>
</nav>
</header><div class="container"><!-- AUTH --><section id="auth" class="box">
<h2>Login / Signup</h2>
<input type="text" id="user" placeholder="Username">
<input type="password" id="pass" placeholder="Password">
<button onclick="signup()">Signup</button>
<button onclick="login()">Login</button>
<p id="auth-msg"></p>
</section><!-- PRODUCTS --><section id="shop">
<h2 style="text-align:center;margin-top:30px">Cookies</h2>
<div class="products" id="products"></div>
</section><!-- CART --><section id="cart" class="cart">
<h2>Your Order</h2>
<ul id="cart-items"></ul>
<h3>Total: ₹<span id="total">0</span></h3><h3>Payment</h3>
<select id="payment">
<option>Cash on Delivery</option>
<option>UPI</option>
<option>Card</option>
</select><button onclick="placeOrder()">Place Order</button>

<p id="order-msg"></p>
<p class="status" id="status"></p>
</section></div><a class="whatsapp" id="wa" target="_blank">WhatsApp</a>

<script>
let products=[
{name:"Choco Chip",price:100,img:"https://images.unsplash.com/photo-1606312619344-7a9c8b0d5f36"},
{name:"Butter",price:80,img:"https://images.unsplash.com/photo-1612197529388-5e6e5b9b5fbd"},
{name:"Oatmeal",price:90,img:"https://images.unsplash.com/photo-1588195538326-c5b1e9f80a1b"}
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

// Signup/Login using localStorage
function signup(){
let u=user.value,p=pass.value;
localStorage.setItem("user",u);
localStorage.setItem("pass",p);
document.getElementById("auth-msg").innerText="Signup successful ✅";
}

function login(){
if(user.value===localStorage.getItem("user") && pass.value===localStorage.getItem("pass")){
document.getElementById("auth-msg").innerText="Login success ✅";
}else{
document.getElementById("auth-msg").innerText="Invalid ❌";
}
}

function placeOrder(){
if(cart.length==0){alert("Cart empty");return;}
let payment=document.getElementById("payment").value;
document.getElementById("order-msg").innerText=`Order placed with ${payment} 🎉`;

// Order tracking simulation
let status=document.getElementById("status");
status.innerText="Order Confirmed";
setTimeout(()=>status.innerText="Preparing 🍳",2000);
setTimeout(()=>status.innerText="Out for Delivery 🚚",4000);
setTimeout(()=>status.innerText="Delivered ✅",6000);

// WhatsApp link
let msg=encodeURIComponent("My order: \n"+cart.map(i=>i.name).join(", "));
document.getElementById("wa").href=`https://wa.me/918825831137?text=${msg}`;

cart=[];update();
}

load();
</script></body>
</html>

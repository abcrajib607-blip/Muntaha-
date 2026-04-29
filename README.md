<!DOCTYPE html>
<html>
<head>
  <title>Muntaha Lifestyle</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {font-family: Arial; margin:0; background:#f9f9f9;}
    header {background:#E91E63; color:#fff; text-align:center; padding:15px;}
    .section {padding:20px;}
    .product {background:#fff; padding:15px; margin:10px; border-radius:10px;}
    button {
      background:#E91E63;
      color:white;
      padding:10px;
      border:none;
      border-radius:5px;
      margin-top:10px;
    }
    .reseller {
      background:#fff3cd;
      padding:10px;
      margin:10px;
      text-align:center;
      font-weight:bold;
    }
    input {
      width:100%;
      padding:8px;
      margin:5px 0;
    }
  </style>
</head>

<body>

<header>
  <h1>Muntaha Lifestyle</h1>
  <p>Borqa | Bag | Shoes</p>
</header>

<div class="reseller" id="resellerBox"></div>

<div class="section">
  <h2>Products</h2>

  <div class="product">
    <h3>Black Borqa - 1500৳</h3>
    <button onclick="selectProduct('Black Borqa')">Order</button>
  </div>

  <div class="product">
    <h3>Ladies Bag - 1200৳</h3>
    <button onclick="selectProduct('Ladies Bag')">Order</button>
  </div>

</div>

<div class="section">
  <h2>Order Form</h2>

  <input type="text" id="name" placeholder="Your Name">
  <input type="text" id="phone" placeholder="Phone Number">
  <input type="text" id="product" placeholder="Product" readonly>

  <button onclick="confirmOrder()">Confirm Order</button>
</div>

<script>
function getReseller() {
  const params = new URLSearchParams(window.location.search);
  return params.get("ref") || "Direct";
}

function showReseller() {
  let r = getReseller();
  document.getElementById("resellerBox").innerText = "Reseller: " + r;
}

function selectProduct(p) {
  document.getElementById("product").value = p;
}

function confirmOrder() {
  let name = document.getElementById("name").value;
  let phone = document.getElementById("phone").value;
  let product = document.getElementById("product").value;
  let reseller = getReseller();

  if(name=="" || phone=="" || product==""){
    alert("Please fill all fields");
    return;
  }

  let message = "Order Confirmed:%0AName: " + name +
                "%0APhone: " + phone +
                "%0AProduct: " + product +
                "%0AReseller: " + reseller;

  let url = "https://wa.me/8801788113971?text=" + message;

  window.open(url, "_blank");

  alert("Order sent to WhatsApp!");
}

showReseller();
</script>

</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>MFT Trader Official Bot</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap" rel="stylesheet">
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: 'Poppins', sans-serif;
      background: white;
      overflow-x: hidden;
    }
    header {
      text-align: center;
      padding: 30px 20px;
      animation: fadeIn 2s ease;
    }
    header h1 {
      font-size: 2.5em;
      color: #111;
      margin-bottom: 20px;
    }
    .welcome {
      text-align: center;
      font-size: 1.5em;
      padding: 10px;
      animation: fadeInDown 2s ease-in-out;
    }
    .slider {
      display: flex;
      justify-content: center;
      align-items: center;
      overflow-x: auto;
      gap: 30px;
      scroll-snap-type: x mandatory;
      padding: 20px;
    }
    .slider img {
      max-width: 300px;
      border-radius: 10px;
      scroll-snap-align: center;
      transition: transform 0.5s ease;
    }
    .slider img:hover {
      transform: scale(1.05);
    }
    .label {
      text-align: center;
      font-weight: bold;
      margin-top: 10px;
    }
    .btn {
      display: block;
      margin: 30px auto;
      background: #111;
      color: white;
      padding: 12px 25px;
      font-size: 1em;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: background 0.3s ease;
    }
    .btn:hover {
      background: #444;
    }
    .hidden { display: none; }

    .subscriptions, .payments {
      max-width: 800px;
      margin: 0 auto;
      padding: 30px;
      text-align: center;
      animation: fadeInUp 1s ease;
    }
    .card {
      border: 1px solid #ccc;
      padding: 20px;
      border-radius: 10px;
      margin-bottom: 20px;
      background: #f8f8f8;
    }
    .payment-methods label {
      display: block;
      margin: 10px 0 5px;
      font-weight: bold;
    }
    .payment-methods select, .payment-methods input {
      width: 100%;
      padding: 10px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .thankyou {
      font-size: 1.3em;
      color: green;
      margin-top: 20px;
    }
    @keyframes fadeIn { from {opacity: 0;} to {opacity: 1;} }
    @keyframes fadeInDown { from {opacity: 0; transform: translateY(-50px);} to {opacity: 1; transform: translateY(0);} }
    @keyframes fadeInUp { from {opacity: 0; transform: translateY(50px);} to {opacity: 1; transform: translateY(0);} }
  </style>
</head>
<body>
  <header>
    <h1>MFT Trader Official Bot</h1>
    <div class="welcome" id="welcome">Welcome to MFT Trader Bot!</div>
  </header>

  <section id="step1">
    <div class="slider">
      <div>
        <img src="https://i.ibb.co/mrrwn3qW/Picsart-25-04-10-21-33-22-789.jpg" alt="Laptop" />
        <div class="label">LAPTOP</div>
      </div>
      <div>
        <img src="https://i.ibb.co/67FpMzy0/Picsart-25-04-10-21-35-17-096.jpg" alt="iPhone" />
        <div class="label">IPHONE</div>
      </div>
      <div>
        <img src="https://i.ibb.co/wFnrnCgm/Picsart-25-04-10-21-36-14-218.jpg" alt="Android" />
        <div class="label">ANDROID</div>
      </div>
    </div>
    <button class="btn" onclick="goToStep2()">BUY NOW</button>
  </section>

  <section id="step2" class="hidden subscriptions">
    <h2>Choose Your Subscription</h2>
    <div class="card">
      <h3>1 Month - $35</h3>
      <p>If our software doesn't work or crash, we will be responsible. You will be refunded in full. After payment take a screenshot for proof.</p>
      <button class="btn" onclick="goToStep3()">Buy</button>
    </div>
    <div class="card">
      <h3>3 Months - $89</h3>
      <p>If our software doesn't work or crash, we will be responsible. You will be refunded in full. After payment take a screenshot for proof.</p>
      <button class="btn" onclick="goToStep3()">Buy</button>
    </div>
    <div class="card">
      <h3>6 Months - $149.99</h3>
      <p>If our software doesn't work or crash, we will be responsible. You will be refunded in full. After payment take a screenshot for proof.</p>
      <button class="btn" onclick="goToStep3()">Buy</button>
    </div>
    <div class="card">
      <h3>1 Year - $299.99</h3>
      <p>If our software doesn't work or crash, we will be responsible. You will be refunded in full. After payment take a screenshot for proof.</p>
      <button class="btn" onclick="goToStep3()">Buy</button>
    </div>
  </section>

  <section id="step3" class="hidden payments">
    <h2>Make Your Payment</h2>
    <div class="payment-methods">
      <label>Select Payment Method:</label>
      <select id="methodSelect" onchange="showAddress()">
        <option value="">-- Choose --</option>
        <option value="TRC20">TRC20 (TRON)</option>
        <option value="ERC20">ERC20 (Ethereum)</option>
        <option value="BEP20">Bitcoin BEP20</option>
      </select>
      <div id="addressBox"></div>
      <label>Your Name:</label>
      <input type="text" placeholder="Enter your name">
      <label>Your Email:</label>
      <input type="email" placeholder="Enter your email">
      <label>Transaction ID:</label>
      <input type="text" placeholder="Enter transaction ID">
      <a href="https://t.me/+XfmhGdl72q83ZGZk" target="_blank">CLICK HERE FOR CONTACT ME</a>
      <br><br>
      <button class="btn" onclick="showThankYou()">DONE</button>
      <div id="thankyouMsg" class="thankyou hidden">THANK YOU. WAIT FOR MY REPLY.</div>
    </div>
  </section>

  <script>
    setTimeout(() => {
      document.getElementById("welcome").style.display = "none";
    }, 5000);

    function goToStep2() {
      document.getElementById("step1").classList.add("hidden");
      document.getElementById("step2").classList.remove("hidden");
    }

    function goToStep3() {
      document.getElementById("step2").classList.add("hidden");
      document.getElementById("step3").classList.remove("hidden");
    }

    function showAddress() {
      const method = document.getElementById("methodSelect").value;
      let address = "";
      if(method === "TRC20") address = "TDCFn7m352NfXkvnhFBgdzxckb7rGyQyRR";
      else if(method === "ERC20") address = "0xa6d9502f73f4ccedec487896cbc3db54b5b29926";
      else if(method === "BEP20") address = "0xa6d9502f73f4ccedec487896cbc3db54b5b29926";
      document.getElementById("addressBox").innerHTML = `<p><strong>${method} Address:</strong><br>${address}</p>`;
    }

    function showThankYou() {
      document.getElementById("thankyouMsg").classList.remove("hidden");
    }
  </script>
</body>
</html>

# Kevas-Trusting-Creations.github.io
<!-- Add Stripe's JavaScript library -->
<script src="https://js.stripe.com/v3/"></script>

<!-- Create a checkout form -->
<form action="/charge" method="post" id="checkout-form">
<label>Card Number:</label>
<input type="text" id="card-number" name="cardNumber" />
<label>Expiration Date:</label>
<input type="text" id="expiration-date" name="expirationDate" />
<label>CVC:</label>
<input type="text" id="cvc" name="cvc" />
<button type="submit">Pay $19.99</button>
</form>

<!-- Add Stripe's checkout code -->
<script>
var stripe = Stripe('YOUR_STRIPE_SECRET_KEY');
var checkoutForm = document.getElementById('checkout-form');

checkoutForm.addEventListener('submit', function(event) {
event.preventDefault();
stripe.createToken({
card: {
number: document.getElementById('card-number').value,
exp_month: document.getElementById('expiration-date').value.split('/')[0],
exp_year: document.getElementById('expiration-date').value.split('/')[1],
cvc: document.getElementById('cvc').value
}
}).then(function(result) {
// Send the token to your server to charge the customer
fetch('https://your-server.com/charge', {
method: 'POST',
headers: {
'Content-Type': 'application/json'
},
body: JSON.stringify({ token: result.token.id })
}).then(function(response) {
response.json().then(function(data) {
console.log(data);
});
});
});
});
</script>

Remember to replace YOUR_STRIPE_SECRET_KEY with your actual Stripe secret key and update the fetch URL to point to your server-side endpoint.

How's that, Jamarcus?
Ahah, Jamarcus! I'd be happy to help improve the script to make it more readable and friendly to the eyes.

Here's a refactored version of the script with some improvements:
<!DOCTYPE html>
<html>
<head>
  <title>My Simple Website</title>
  <style>
    /* Add some spacing and breakpoints to make the layout more responsive */
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin: 20px;
    }
   .image-container {
      margin: 20px;
      display: inline-block;
      width: 250px;
    }
    img {
      width: 200px;
      height: 150px;
      border: 1px solid #ccc;
      border-radius: 10px;
    }
   .image-text {
      font-size: 18px;
      margin-top: 10px;
    }
   .price {
      font-size: 24px;
      font-weight: bold;
      color: #00698f;
    }
    /* Add some basic styling to the form */
    form {
      max-width: 300px;
      margin: 20px auto;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    label {
      display: block;
      margin-bottom: 10px;
    }
    input[type="text"] {
      width: 100%;
      height: 40px;
      padding: 10px;
      border: 1px solid #ccc;
    }
    button[type="submit"] {
      background-color: #00698f;
      color: #fff;
      padding: 10px 20px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>Welcome to My Simple Website</h1>
  <div class="image-container">
    <img src="image1.jpg" alt="Image 1">
    <p class="image-text">This is image 1</p>
    <p class="price">$19.99</p>
  </div>
  <div class="image-container">
    <img src="image2.jpg" alt="Image 2">
    <p class="image-text">This is image 2</p>
    <p class="price">$29.99</p>
  </div>
  <div class="image-container">
    <img src="image3.jpg" alt="Image 3">
    <p class="image-text">This is image 3</p>
    <p class="price">$39.99</p>
  </div>

  <!-- Add a simple checkout form -->
  <form id="checkout-form">
    <label>Card Number:</label>
    <input type="text" id="card-number" />
    <label>Expiration Date:</label>
    <input type="text" id="expiration-date" />
    <label>CVC:</label>
    <input type="text" id="cvc" />
    <button type="submit">Pay $19.99</button>
  </form>

  <!-- Add Stripe's JavaScript library and checkout code -->
  <script src="https://js.stripe.com/v3/"></script>
  <script>
    const stripe = Stripe('YOUR_STRIPE_SECRET_KEY');
    const checkoutForm = document.getElementById('checkout-form');

    checkoutForm.addEventListener('submit', event => {
      event.preventDefault();
      stripe.createToken({
        card: {
          number: document.getElementById('card-number').value,
          exp_month: document.getElementById('expiration-date').value.split('/')[0],
          exp_year: document.getElementById('expiration-date').value.split('/')[1],
          cvc: document.getElementById('cvc').value
        }
      }).then(result => {
        // Send the token to your server to charge the customer
        fetch('/charge', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify({ token: result.token.id })
        }).then(response => {
          response.json().then(data => {
            console.log(data);
          });
        });
      });
    });
  </script>
</body>
</html>

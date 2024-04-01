# simple-shopping-website
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shopping Website</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Shopping Website</h1>
        <button id="cartBtn">View Cart</button>
        <div id="cartItems"></div>
    </header>
    
    <main id="productList">
        <div class="product">
            <h2>Product 1</h2>
            <p>$10</p>
            <button class="addToCartBtn">Add to Cart</button>
        </div>
        <div class="product">
            <h2>Product 2</h2>
            <p>$20</p>
            <button class="addToCartBtn">Add to Cart</button>
        </div>
        <!-- More products can be added here -->
    </main>

    <script src="script.js"></script>
</body>
</html>
/* styles.css */
body {
    font-family: Arial, sans-serif;
}

header {
    background-color: #333;
    color: #fff;
    padding: 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.product {
    border: 1px solid #ccc;
    padding: 20px;
    margin-bottom: 10px;
}

button {
    background-color: #333;
    color: #fff;
    border: none;
    padding: 5px 10px;
    cursor: pointer;
    margin-top: 10px;
}

button:hover {
    background-color: #555;
}
// script.js
const addToCartButtons = document.querySelectorAll('.addToCartBtn');
const cartItemsContainer = document.getElementById('cartItems');
const cartBtn = document.getElementById('cartBtn');

let cartItems = [];

// Add event listeners to Add to Cart buttons
addToCartButtons.forEach(button => {
    button.addEventListener('click', () => {
        const product = button.parentElement;
        const productName = product.querySelector('h2').textContent;
        const productPrice = parseFloat(product.querySelector('p').textContent.slice(1));
        const cartItem = { name: productName, price: productPrice };

        cartItems.push(cartItem);
        updateCart();
    });
});

// Update cart display
function updateCart() {
    cartItemsContainer.innerHTML = '';
    cartItems.forEach(item => {
        const cartItemDiv = document.createElement('div');
        cartItemDiv.textContent = `${item.name} - $${item.price}`;
        cartItemsContainer.appendChild(cartItemDiv);
    });
}

// Show/hide cart
cartBtn.addEventListener('click', () => {
    cartItemsContainer.classList.toggle('show');
});

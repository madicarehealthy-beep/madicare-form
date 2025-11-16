<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Premium Order Form</title>

<style>

/* Background */
body {
    margin: 0;
    font-family: Poppins, sans-serif;
    background: linear-gradient(135deg, #4A00E0, #8E2DE2);
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
}

/* Glass Card */
.card {
    width: 100%;
    max-width: 420px;
    background: rgba(255, 255, 255, 0.15);
    backdrop-filter: blur(18px);
    border-radius: 25px;
    padding: 30px;
    box-shadow: 0 15px 45px rgba(0,0,0,0.25);
    animation: fadeIn 1s ease;
    border: 1px solid rgba(255,255,255,0.2);
}

/* Heading */
.card h2 {
    text-align: center;
    color: white;
    font-size: 26px;
    margin-bottom: 20px;
    letter-spacing: 1px;
}

/* Inputs */
input, textarea {
    width: 100%;
    padding: 14px;
    margin-bottom: 16px;
    border: none;
    border-radius: 14px;
    outline: none;
    font-size: 16px;
    font-weight: 500;
    background: rgba(255,255,255,0.9);
    transition: all 0.3s ease;
}

input:focus, textarea:focus {
    transform: scale(1.02);
    box-shadow: 0 0 10px rgba(255,255,255,0.7);
}

/* Button */
button {
    width: 100%;
    padding: 14px;
    background: linear-gradient(to right, #00c6ff, #0072ff);
    border: none;
    color: white;
    border-radius: 14px;
    font-size: 18px;
    letter-spacing: 1px;
    font-weight: 600;
    cursor: pointer;
    transition: 0.3s ease-in-out;
}

button:hover {
    transform: scale(1.05);
    box-shadow: 0 8px 20px rgba(0,0,0,0.3);
}

/* Success message */
#status {
    display: none;
    text-align: center;
    margin-top: 18px;
    color: #00ffcc;
    font-size: 18px;
    animation: fadeIn 0.8s ease;
}

/* Fade animation */
@keyframes fadeIn {
    from {opacity: 0; transform: translateY(20px);}
    to {opacity: 1; transform: translateY(0);}
}

</style>
</head>

<body>

<div class="card">
    <h2>Submit Your Details</h2>

    <form id="myForm" action="https://formspree.io/f/xzzyvpav" method="POST">

        <input type="text" name="Full Name" placeholder="Enter your full name" required>

        <input type="email" name="Email" placeholder="Enter your email" required>

        <input type="text" name="Phone" placeholder="Enter your phone number" required>

        <textarea name="Message" rows="4" placeholder="Enter your message / order details" required></textarea>

        <button type="submit">Submit</button>
    </form>

    <p id="status">Your order is pending. Our team will respond soon.</p>
</div>




<script>
document.getElementById("myForm").addEventListener("submit", function(e) {
    e.preventDefault();

    let form = e.target;

    fetch(form.action, {
        method: "POST",
        body: new FormData(form),
        headers: { "Accept": "application/json" }
    }).then(response => {
        document.getElementById("status").style.display = "block";
        form.reset();
    });
});
</script>

</body>
</html>

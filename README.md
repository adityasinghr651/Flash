# Flash
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flashcard App</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        body {
            background: linear-gradient(135deg, #000000, #444444, #ffffff);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: Arial, sans-serif;
            animation: fadeIn 1s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .container {
            background: rgba(18, 18, 18, 0.9);
            color: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(255, 255, 255, 0.2);
            text-align: center;
            width: 350px;
            animation: slideIn 0.8s ease-in-out;
        }

        @keyframes slideIn {
            from { transform: translateY(-20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            transition: 0.3s;
        }

        input:focus {
            background: rgba(255, 255, 255, 0.2);
            outline: none;
            transform: scale(1.05);
        }

        button {
            background: linear-gradient(45deg, #90EE90, #32CD32);
            color: black;
            font-weight: bold;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: 0.3s;
            width: 100%;
            margin-top: 10px;
        }

        button:hover {
            background: linear-gradient(45deg, #77dd77, #28a745);
            transform: scale(1.1);
        }

        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div id="login-container" class="container">
        <h2>Login</h2>
        <input type="email" id="email" placeholder="Email">
        <input type="password" id="password" placeholder="Password">
        <button onclick="login()">Login</button>
        <p id="error-message" style="color: red;"></p>
        
        <h3>Or Login with</h3>
        <button onclick="socialLogin('Google')">Login with Google</button>
        <button onclick="socialLogin('Facebook')">Login with Facebook</button>
        <button onclick="socialLogin('GitHub')">Login with GitHub</button>
    </div>

    <div id="dashboard-container" class="container hidden">
        <h1>Welcome to Your Dashboard</h1>
        <p>You have successfully logged in.</p>
        <button onclick="logout()">Logout</button>
    </div>

    <script>
        function login() {
            let email = document.getElementById("email").value.trim();
            let password = document.getElementById("password").value.trim();
            let errorMessage = document.getElementById("error-message");

            if (email === "" || password === "") {
                errorMessage.textContent = "Please fill in both fields.";
                return;
            }

            if (email.includes("@") && password === "password") {
                errorMessage.style.color = "lightgreen";
                errorMessage.textContent = "Login successful! Redirecting...";
                setTimeout(() => {
                    document.getElementById("login-container").classList.add("hidden");
                    document.getElementById("dashboard-container").classList.remove("hidden");
                }, 1000);
            } else {
                errorMessage.textContent = "Invalid email or password!";
                errorMessage.style.color = "red";
            }
        }

        function socialLogin(platform) {
            alert("Redirecting to " + platform + " login...");
        }

        function logout() {
            document.getElementById("dashboard-container").classList.add("hidden");
            document.getElementById("login-container").classList.remove("hidden");
        }
    </script>
</body>
</html>

<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulario de Login</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            background: linear-gradient(120deg, #2980b9, #8e44ad);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100%;
            width: 100%;
        }

        .login-box {
            position: relative;
            width: 360px;
            padding: 40px;
            background: rgba(0, 0, 0, 0.8);
            color: white;
            text-align: center;
            border-radius: 10px;
            box-shadow: 0 15px 25px rgba(0, 0, 0, 0.5);
        }

        .login-box h2 {
            margin: 0 0 30px;
            padding: 0;
            color: #03e9f4;
            text-transform: uppercase;
        }

        .user-box {
            position: relative;
        }

        .user-box input {
            width: 100%;
            padding: 10px 0;
            font-size: 16px;
            color: white;
            margin-bottom: 30px;
            border: none;
            border-bottom: 1px solid #03e9f4;
            outline: none;
            background: transparent;
        }

        .user-box label {
            position: absolute;
            top: 0;
            left: 0;
            padding: 10px 0;
            font-size: 16px;
            color: #03e9f4;
            pointer-events: none;
            transition: 0.5s;
        }

        .user-box input:focus ~ label,
        .user-box input:valid ~ label {
            top: -20px;
            left: 0;
            color: #03e9f4;
            font-size: 12px;
        }

        .btn {
            background: none;
            border: none;
            outline: none;
            color: white;
            background: #03e9f4;
            padding: 10px 20px;
            cursor: pointer;
            border-radius: 5px;
            transition: 0.5s;
        }

        .btn:hover {
            background: #028c9e;
        }

        #message {
            margin-top: 20px;
            font-size: 14px;
            color: #03e9f4;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="login-box">
            <h2>Formulario de Acceso</h2>
            <form id="loginForm">
                <div class="user-box">
                    <input type="text" id="username" name="username" required>
                    <label for="username">Usuario</label>
                </div>
                <div class="user-box">
                    <input type="password" id="password" name="password" required>
                    <label for="password">Contraseña</label>
                </div>
                <button type="submit" class="btn">Iniciar Sesión</button>
            </form>
            <p id="message"></p>
        </div>
    </div>
    <script>
        let users = [
            {username: "usuario1", password: "contraseña1"},
            {username: "usuario2", password: "contraseña2"}
        ];

        document.getElementById("loginForm").addEventListener("submit", function(event) {
            event.preventDefault();

            let username = document.getElementById("username").value;
            let password = document.getElementById("password").value;
            let user = users.find(user => user.username === username);

            if (user && user.password === password) {
                document.getElementById("message").textContent = "Acceso concedido";
            } else if (user && user.password !== password) {
                document.getElementById("message").textContent = "Contraseña incorrecta";
            } else {
                document.getElementById("message").textContent = "Usuario no encontrado. Registrando nuevo usuario...";
                users.push({username: username, password: password});
                document.getElementById("message").textContent += " Usuario registrado exitosamente.";
            }
        });
    </script>
</body>
</html>

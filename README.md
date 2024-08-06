<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rückforderung von Servicepauschalen</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .container {
            background: #ffffff;
            border-radius: 8px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
            max-width: 500px;
            width: 90%;
            padding: 20px;
            box-sizing: border-box;
            text-align: center;
        }

        h1 {
            margin-bottom: 20px;
            color: #333;
            font-size: 24px;
        }

        p {
            margin-bottom: 20px;
            color: #555;
            font-size: 16px;
        }

        form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        label {
            margin-bottom: 5px;
            font-weight: bold;
            color: #555;
        }

        input[type="text"],
        input[type="email"],
        textarea {
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
        }

        textarea {
            resize: vertical;
        }

        button {
            padding: 10px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #0056b3;
        }

        #responseMessage {
            margin-top: 20px;
            font-size: 16px;
            color: #333;
        }

        a {
            display: block;
            margin-top: 20px;
            color: #007BFF;
            text-decoration: none;
            font-size: 16px;
        }

        a:hover {
            text-decoration: underline;
        }

        @media (max-width: 600px) {
            .container {
                padding: 15px;
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Rückforderung von Servicepauschalen</h1>
        <p>Füllen Sie bitte das folgende Formular aus, um eine Rückforderung von Servicepauschalen zu beantragen.</p>
        <form id="refundForm">
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required>

            <label for="email">E-Mail:</label>
            <input type="email" id="email" name="email" required>

            <label for="phone">Telefonnummer:</label>
            <input type="text" id="phone" name="phone">

            <label for="address">Adresse:</label>
            <input type="text" id="address" name="address" required>

            <label for="message">Nachricht:</label>
            <textarea id="message" name="message" rows="4" placeholder="Beschreiben Sie Ihre Rückforderung..."></textarea>

            <button type="submit">Rückforderung anfragen</button>
        </form>
        <p id="responseMessage"></p>
    </div>

    <script>
        document.getElementById('refundForm').addEventListener('submit', function(event) {
            event.preventDefault();

            const formData = new FormData(this);

            fetch('https://formspree.io/f/xqazqopv', {
                method: 'POST',
                body: formData
            }).then(() => {
                document.getElementById('responseMessage').textContent = 'Ihre Anfrage wurde erfolgreich gesendet!';
                this.reset();
            }).catch(() => {
                document.getElementById('responseMessage').textContent = 'Fehler beim Senden der Anfrage. Bitte versuchen Sie es später erneut.';
            });
        });
    </script>
</body>
</html>

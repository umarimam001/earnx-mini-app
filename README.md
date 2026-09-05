<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>EarnX</title>

    <!-- Telegram Mini App -->
    <script src="https://telegram.org/js/telegram-web-app.js"></script>

    <!-- Monetag SDK -->
    <script
        src="//libtl.com/sdk.js"
        data-zone="11731534"
        data-sdk="show_11731534">
    </script>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            padding: 25px 18px;
            font-family: Arial, sans-serif;
            background: #f5f5f5;
            color: #111;
        }

        .container {
            max-width: 420px;
            margin: auto;
        }

        .card {
            background: white;
            border-radius: 20px;
            padding: 25px;
            text-align: center;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
        }

        .logo {
            font-size: 50px;
            margin-bottom: 10px;
        }

        h1 {
            margin: 0;
            font-size: 28px;
        }

        .subtitle {
            color: #666;
            margin-top: 8px;
        }

        .balance-box {
            margin: 25px 0;
            padding: 20px;
            border-radius: 15px;
            background: #f0f0f0;
        }

        .balance-label {
            font-size: 14px;
            color: #666;
        }

        .balance {
            font-size: 30px;
            font-weight: bold;
            margin-top: 6px;
        }

        .watch-btn {
            width: 100%;
            padding: 16px;
            border: none;
            border-radius: 14px;
            font-size: 17px;
            font-weight: bold;
            cursor: pointer;
            background: #111;
            color: white;
        }

        .watch-btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
        }

        .status {
            margin-top: 18px;
            font-size: 14px;
            min-height: 20px;
        }
    </style>
</head>

<body>

<div class="container">

    <div class="card">

        <div class="logo">💰</div>

        <h1>EarnX</h1>

        <p class="subtitle">
            Watch ads and earn rewards
        </p>

        <div class="balance-box">

            <div class="balance-label">
                Your Balance
            </div>

            <div class="balance" id="balance">
                0.00
            </div>

        </div>

        <button
            class="watch-btn"
            id="watchButton"
            onclick="watchAd()">

            🎬 Watch Ad & Earn

        </button>

        <div
            class="status"
            id="status">
        </div>

    </div>

</div>

<script>

const tg = window.Telegram.WebApp;

tg.ready();
tg.expand();

async function watchAd() {

    const button = document.getElementById("watchButton");
    const status = document.getElementById("status");

    button.disabled = true;

    status.textContent = "⏳ Loading advertisement...";

    try {

        await show_11731534("pop");

        status.textContent = "✅ Ad completed successfully!";

        /*
         * IMPORTANT:
         * Do not credit the user's balance here.
         *
         * Verified Monetag reward processing will be
         * connected after the postback/API is configured.
         */

    } catch (error) {

        console.log(error);

        status.textContent =
            "❌ Advertisement could not be completed.";

    }

    button.disabled = false;
}

</script>

</body>
</html>

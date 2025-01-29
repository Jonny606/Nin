<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Game Website</title>
    <style>
        /* Global styles */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        header {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 10px;
        }
        nav {
            background-color: #444;
            padding: 10px;
        }
        nav a {
            color: white;
            padding: 10px;
            text-decoration: none;
            margin: 5px;
        }
        nav a:hover {
            background-color: #555;
        }

        /* Game section */
        .game-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            padding: 20px;
        }
        .game-card {
            background: white;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            overflow: hidden;
            width: 300px;
        }
        .game-card img {
            width: 100%;
            height: auto;
        }
        .game-card iframe {
            width: 100%;
            height: 200px;
        }

        /* Footer styles */
        footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 10px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Welcome to My Game Website</h1>
    </header>

    <nav>
        <a href="#subway-surfer">Subway Surfer</a>
        <a href="#retro-bowl">Retro Bowl</a>
        <a href="#basketball-random">Basketball Random</a>
        <!-- Add more links here -->
    </nav>

    <section class="game-container">
        <div class="game-card" id="subway-surfer">
            <img src="subway-surfer-thumbnail.jpg" alt="Subway Surfer">
            <iframe src="https://your-game-url.com/subway-surfer" frameborder="0"></iframe>
        </div>

        <div class="game-card" id="retro-bowl">
            <img src="retro-bowl-thumbnail.jpg" alt="Retro Bowl">
            <iframe src="https://your-game-url.com/retro-bowl" frameborder="0"></iframe>
        </div>

        <div class="game-card" id="basketball-random">
            <img src="basketball-random-thumbnail.jpg" alt="Basketball Random">
            <iframe src="https://your-game-url.com/basketball-random" frameborder="0"></iframe>
        </div>

        <!-- Add more games here -->
    </section>

    <footer>
        <p>&copy; 2025 My Game Website. All rights reserved.</p>
    </footer>
</body>
</html>

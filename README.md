<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Game Website</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }
        nav {
            background-color: #333;
            padding: 10px;
        }
        nav ul {
            list-style: none;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
        }
        nav ul li {
            margin: 0 15px;
        }
        nav ul li a {
            color: white;
            text-decoration: none;
            font-size: 18px;
        }
        section {
            padding: 20px;
            text-align: center;
        }
        .game-container {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            margin-top: 20px;
        }
        .game-card {
            border: 2px solid #ccc;
            border-radius: 10px;
            overflow: hidden;
            text-align: center;
        }
        .game-card img {
            width: 100%;
            height: auto;
        }
        .game-card iframe {
            width: 100%;
            height: 400px;
        }
    </style>
</head>
<body>
    <!-- Navigation Bar -->
    <header>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#games">Games</a></li>
                <li><a href="#about">About</a></li>
            </ul>
        </nav>
    </header>

    <!-- Main Content Section -->
    <section id="home">
        <h1>Welcome to My Game Website</h1>
        <p>Play your favorite online games here!</p>
    </section>

    <!-- Games Section -->
    <section id="games">
        <h2>Popular Games</h2>
        <div class="game-container">
            <!-- Subway Surfers -->
            <div class="game-card">
                <img src="subway-surfers-image.jpg" alt="Subway Surfers">
                <iframe src="https://example.com/subway-surfers-embed" frameborder="0"></iframe>
            </div>

            <!-- Retro Bowl -->
            <div class="game-card">
                <img src="retro-bowl-image.jpg" alt="Retro Bowl">
                <iframe src="https://example.com/retro-bowl-embed" frameborder="0"></iframe>
            </div>

            <!-- Basketball Random -->
            <div class="game-card">
                <img src="basketball-random-image.jpg" alt="Basketball Random">
                <iframe src="https://example.com/basketball-random-embed" frameborder="0"></iframe>
            </div>

            <!-- Flappy Bird -->
            <div class="game-card">
                <img src="flappy-bird-image.jpg" alt="Flappy Bird">
                <iframe src="https://example.com/flappy-bird-embed" frameborder="0"></iframe>
            </div>

            <!-- BitLife (College) -->
            <div class="game-card">
                <img src="bitlife-college-image.jpg" alt="BitLife College">
                <iframe src="https://example.com/bitlife-college-embed" frameborder="0"></iframe>
            </div>

            <!-- Soccer Random -->
            <div class="game-card">
                <img src="soccer-random-image.jpg" alt="Soccer Random">
                <iframe src="https://example.com/soccer-random-embed" frameborder="0"></iframe>
            </div>

            <!-- Cookie Clicker -->
            <div class="game-card">
                <img src="cookie-clicker-image.jpg" alt="Cookie Clicker">
                <iframe src="https://example.com/cookie-clicker-embed" frameborder="0"></iframe>
            </div>

            <!-- 1v1.lol -->
            <div class="game-card">
                <img src="1v1-lol-image.jpg" alt="1v1.lol">
                <iframe src="https://example.com/1v1lol-embed" frameborder="0"></iframe>
            </div>

            <!-- Friday Night Funkin' -->
            <div class="game-card">
                <img src="friday-night-funkin-image.jpg" alt="Friday Night Funkin'">
                <iframe src="https://example.com/friday-night-funkin-embed" frameborder="0"></iframe>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about">
        <h2>About This Website</h2>
        <p>This website was created to provide a variety of fun online games for everyone to enjoy!</p>
    </section>

    <!-- Footer -->
    <footer>
        <p>&copy; 2025 My Game Website</p>
    </footer>
</body>
</html>


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
        iframe {
            width: 800px;
            height: 600px;
            margin: 20px auto;
            display: block;
            border: none;
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

        <!-- Subway Surfers Embed -->
        <h3>Subway Surfers</h3>
        <iframe src="https://example.com/subway-surfers"></iframe>

        <!-- Retro Bowl Embed -->
        <h3>Retro Bowl</h3>
        <iframe src="https://example.com/retro-bowl"></iframe>

        <!-- Basketball Random Embed -->
        <h3>Basketball Random</h3>
        <iframe src="https://example.com/basketball-random"></iframe>

        <!-- Flappy Bird Embed -->
        <h3>Flappy Bird</h3>
        <iframe src="https://example.com/flappy-bird"></iframe>

        <!-- BitLife (College Version) Embed -->
        <h3>BitLife (College Version)</h3>
        <iframe src="https://example.com/bitlife-college"></iframe>

        <!-- Soccer Random Embed -->
        <h3>Soccer Random</h3>
        <iframe src="https://example.com/soccer-random"></iframe>

        <!-- Cookie Clicker Embed -->
        <h3>Cookie Clicker</h3>
        <iframe src="https://example.com/cookie-clicker"></iframe>

        <!-- 1v1.lol Old Version Embed -->
        <h3>1v1.lol (Old Version)</h3>
        <iframe src="https://example.com/1v1-lol-old"></iframe>

        <!-- Friday Night Funkin' Embed -->
        <h3>Friday Night Funkin'</h3>
        <iframe src="https://example.com/friday-night-funkin"></iframe>
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
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FIFA Pack Simulator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        #packDisplay {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        #packAnimation {
            display: none;
        }
        #viewClub, #playAgainstBot, #playAgainstRealPlayer, #openPack, #buyPack {
            margin: 10px;
        }
        .player-image {
            width: 150px;
            height: auto;
        }
        #clubPlayers {
            display: none;
            flex-wrap: wrap;
            justify-content: center;
        }
        #clubPlayers img {
            margin: 10px;
            width: 120px;
            height: auto;
        }
    </style>
</head>
<body>
    <h1>FIFA Pack Simulator</h1>

    <div id="packDisplay">
        <button id="openPack">Open Pack (100 Coins)</button>
        <button id="viewClub">View Club</button>
        <button id="playAgainstBot">Play Against Bot</button>
    </div>

    <div id="packAnimation">
        <img id="countryImage" src="" alt="Country Image" style="display:none;">
        <div id="positionDisplay" style="display:none; font-size: 24px; font-weight: bold;"></div>
        <img id="teamImage" src="" alt="Team Image" style="display:none;">
        <img id="playerImage" src="" alt="Player Image" class="player-image" style="display:none;">
    </div>

    <div id="clubPlayers">
        <!-- Club players will be dynamically inserted here -->
    </div>

    <div id="coinDisplay">Coins: <span id="coins">1000</span></div>

    <script>
        let coins = 1000;  // Starting coins
        let playersInClub = [];  // Club players array

        const imagesFolder = 'images/';
        const players = [
            { name: 'Lionel Messi', country: 'argentina.png', image: 'Messi.jpg', position: 'RW', teamImage: 'barcelona.png' },
            { name: 'Kylian Mbappé', country: 'france.png', image: 'Mbappé.jpg', position: 'ST', teamImage: 'psg.png' },
            { name: 'Antony', country: 'brazil.png', image: 'Antony.jpg', position: 'RW', teamImage: 'manchester_united.png' },
            { name: 'Bruno Fernandes', country: 'portugal.png', image: 'Bruno_Fernandes.jpg', position: 'CAM', teamImage: 'manchester_united.png' },
            { name: 'Neymar', country: 'brazil.png', image: 'Neymar.jpg', position: 'LW', teamImage: 'psg.png' },
            { name: 'Jackson', country: 'england.png', image: 'Jackson.jpg', position: 'ST', teamImage: 'chelsea.png' },
            { name: 'Pelé', country: 'brazil.png', image: 'Pelé.jpg', position: 'CAM', teamImage: 'Icon.png' },
            { name: 'Diego Maradona', country: 'argentina.png', image: 'Maradona.jpg', position: 'CAM', teamImage: 'Icon.png' },
            { name: 'Manuel Neuer', country: 'germany.png', image: 'Neuer.jpg', position: 'GK', teamImage: 'bayern_munich.png' },
            { name: 'Toni Kroos', country: 'germany.png', image: 'Kroos.jpg', position: 'CM', teamImage: 'real_madrid.png' },
            { name: 'Erling Haaland', country: 'norway.png', image: 'Haaland.jpg', position: 'ST', teamImage: 'manchester_city.png' },
            { name: 'Virgil van Dijk', country: 'netherlands.png', image: 'VVD.jpg', position: 'CB', teamImage: 'liverpool.png' },
            { name: 'Cristiano Ronaldo', country: 'portugal.png', image: 'Ronaldo.jpg', position: 'ST', teamImage: 'al_nassr.png' },
            { name: 'Kevin De Bruyne', country: 'belgium.png', image: 'Kdb.jpg', position: 'CAM', teamImage: 'manchester_city.png' },
            { name: 'Kaká', country: 'brazil.png', image: 'Kaka.jpg', position: 'CAM', teamImage: 'Icon.png' },
            { name: 'Roberto Carlos', country: 'brazil.png', image: 'Roberto_Carlos.jpg', position: 'LB', teamImage: 'real_madrid.png' },
            { name: 'Lev Yashin', country: 'russia.png', image: 'Yashin.jpg', position: 'GK', teamImage: 'Icon.png' },
            { name: 'André Onana', country: 'cameroon.png', image: 'Onana.jpg', position: 'GK', teamImage: 'manchester_united.png' },
            { name: 'Rodrygo', country: 'brazil.png', image: 'Rodrygo.jpg', position: 'RW', teamImage: 'real_madrid.png' },
            { name: 'Rodri', country: 'spain.png', image: 'Rodri.jpg', position: 'CDM', teamImage: 'manchester_city.png' },
            { name: 'Ruben Dias', country: 'portugal.png', image: 'Dias.jpg', position: 'CB', teamImage: 'manchester_city.png' },
            { name: 'Alphonso Davies', country: 'canada.png', image: 'Davies.jpg', position: 'LB', teamImage: 'bayern_munich.png' },
            { name: 'Joshua Kimmich', country: 'germany.png', image: 'Kimmich.jpg', position: 'CDM', teamImage: 'bayern_munich.png' },
            { name: 'Dani Carvajal', country: 'spain.png', image: 'Carvajal.jpg', position: 'RB', teamImage: 'real_madrid.png' },
            { name: 'Lamine Yamal', country: 'spain.png', image: 'Yamal.jpg', position: 'RW', teamImage: 'barcelona.png' }
        ];

        function getRandomPlayers(num) {
            const shuffled = players.sort(() => 0.5 - Math.random());
            return shuffled.slice(0, num); // Get random players
        }

        // Handle opening pack
        document.getElementById("openPack").addEventListener("click", function() {
            const packCost = 100; // Cost for opening a pack
            if (coins >= packCost) {
                const playersInPack = getRandomPlayers(3); // Random 3 players from the list
                playersInClub.push(...playersInPack); // Add players to the club
                coins -= packCost; // Deduct coins
                document.getElementById('coins').textContent = coins; // Update coin display

                // Display the pack animation
                const randomPlayer = playersInPack[0]; // Show the first player
                document.getElementById('countryImage').src = imagesFolder + randomPlayer.country;
                document.getElementById('teamImage').src = imagesFolder + randomPlayer.teamImage;
                document.getElementById('playerImage').src = imagesFolder + randomPlayer.image;
                document.getElementById('positionDisplay').textContent = randomPlayer.position;

                document.getElementById('packDisplay').style.display = 'none';
                document.getElementById('packAnimation').style.display = 'block';

                document.getElementById('countryImage').style.display = 'block';
                setTimeout(() => {
                    document.getElementById('countryImage').style.display = 'none';
                    document.getElementById('positionDisplay').style.display = 'block';
                    setTimeout(() => {
                        document.getElementById('positionDisplay').style.display = 'none';
                        document.getElementById('teamImage').style.display = 'block';
                        setTimeout(() => {
                            document.getElementById('teamImage').style.display = 'none';
                            document.getElementById('playerImage').style.display = 'block';
                            // Hide animation after 5 seconds
                            setTimeout(() => {
                                document.getElementById('packAnimation').style.display = 'none';
                                document.getElementById('packDisplay').style.display = 'flex';
                            }, 5000);
                        }, 3000);
                    }, 3000);
                }, 3000);
            } else {
                alert('Not enough coins to open the pack!');
            }
        });

        // Handle viewing club
        document.getElementById("viewClub").addEventListener("click", function() {
            const club = document.getElementById('clubPlayers');
            club.style.display = (club.style.display === 'none') ? 'flex' : 'none';
            renderClubPlayers();
        });

        // Render club players
        function renderClubPlayers() {
            const club = document.getElementById('clubPlayers');
            club.innerHTML = '';  // Clear existing players
            playersInClub.forEach(player => {
                const img = document.createElement('img');
                img.src = imagesFolder + player.image;
                img.alt = player.name;
                club.appendChild(img);
            });
        }
    </script>
</body>
</html>
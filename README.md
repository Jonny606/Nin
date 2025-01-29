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
        <button id="openPack" onclick="openPack()">Open Pack</button>
        <button id="buyPack" onclick="buyPack()">Buy Pack</button>
        <button id="viewClub" onclick="viewClub()">View Club</button>
        <button id="playAgainstBot" onclick="playAgainstBot()">Play Against Bot</button>
        <button id="playAgainstRealPlayer" onclick="playAgainstRealPlayer()">Play Against Real Player</button>
    </div>

    <div id="packAnimation">
        <img id="countryImage" src="" alt="Country Image" style="display:none;">
        <div id="positionDisplay" style="display:none; font-size: 24px; font-weight: bold;"></div>
        <img id="teamImage" src="" alt="Team Image" style="display:none;">
        <img id="playerImage" src="" alt="Player Image" class="player-image" style="display:none;">
    </div>

    <div id="clubPlayers">
        <!-- Players will be dynamically inserted here -->
    </div>

    <script>
        const imagesFolder = 'images/';
        const players = [
            { name: 'Messi', country: 'argentina.png', image: 'Messi.jpg', position: 'RW', teamImage: 'barcelona.png' },
            { name: 'Bellingham', country: 'england.png', image: 'Bellingham.jpg', position: 'CM', teamImage: 'real_madrid.png' },
            { name: 'Antony', country: 'brazil.png', image: 'Antony.jpg', position: 'RW', teamImage: 'manchester_united.png' },
            { name: 'Bruno Fernandes', country: 'portugal.png', image: 'Bruno_Fernandes.jpg', position: 'CAM', teamImage: 'manchester_united.png' },
            { name: 'Neymar', country: 'brazil.png', image: 'Neymar.jpg', position: 'LW', teamImage: 'psg.png' },
            { name: 'Mbappé', country: 'france.png', image: 'Mbappé.jpg', position: 'ST', teamImage: 'psg.png' },
            { name: 'Jackson', country: 'england.png', image: 'Jackson.jpg', position: 'ST', teamImage: 'chelsea.png' },
            { name: 'Pelé', country: 'brazil.png', image: 'Pelé.jpg', position: 'CAM', teamImage: 'Icon.png' },
            { name: 'Maradona', country: 'argentina.png', image: 'Maradona.jpg', position: 'CAM', teamImage: 'Icon.png' },
            { name: 'Neuer', country: 'germany.png', image: 'Neuer.jpg', position: 'GK', teamImage: 'bayern_munich.png' },
            { name: 'Kroos', country: 'germany.png', image: 'Kroos.jpg', position: 'CM', teamImage: 'real_madrid.png' },
            { name: 'Haaland', country: 'norway.png', image: 'Haaland.jpg', position: 'ST', teamImage: 'manchester_city.png' },
            { name: 'Virgil van Dijk', country: 'netherlands.png', image: 'VVD.jpg', position: 'CB', teamImage: 'liverpool.png' },
            { name: 'Cristiano Ronaldo', country: 'portugal.png', image: 'Ronaldo.jpg', position: 'ST', teamImage: 'al_nassr.png' },
            { name: 'Kevin De Bruyne', country: 'belgium.png', image: 'Kdb.jpg', position: 'CAM', teamImage: 'manchester_city.png' },
            { name: 'Kaká', country: 'brazil.png', image: 'Kaka.jpg', position: 'CAM', teamImage: 'Icon.png' },
            { name: 'Roberto Carlos', country: 'brazil.png', image: 'Roberto_Carlos.jpg', position: 'LB', teamImage: 'real_madrid.png' },
            { name: 'Yashin', country: 'russia.png', image: 'Yashin.jpg', position: 'GK', teamImage: 'Icon.png' },
            { name: 'Onana', country: 'cameroon.png', image: 'Onana.jpg', position: 'GK', teamImage: 'manchester_united.png' },
            { name: 'Rodrygo', country: 'brazil.png', image: 'Rodrygo.jpg', position: 'RW', teamImage: 'real_madrid.png' },
            { name: 'Rodri', country: 'spain.png', image: 'Rodri.jpg', position: 'CDM', teamImage: 'manchester_city.png' },
            { name: 'Ruben Dias', country: 'portugal.png', image: 'Dias.jpg', position: 'CB', teamImage: 'manchester_city.png' },
            { name: 'Davies', country: 'canada.png', image: 'Davies.jpg', position: 'LB', teamImage: 'bayern_munich.png' },
            { name: 'Kimmich', country: 'germany.png', image: 'Kimmich.jpg', position: 'CDM', teamImage: 'bayern_munich.png' },
            { name: 'Carvajal', country: 'spain.png', image: 'Carvajal.jpg', position: 'RB', teamImage: 'real_madrid.png' },
            { name: 'Lamine Yamal', country: 'spain.png', image: 'Yamal.jpg', position: 'RW', teamImage: 'barcelona.png' }
        ];

        function openPack() {
            const randomPlayer = players[Math.floor(Math.random() * players.length)];

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
                    }, 3000);
                }, 3000);
            }, 3000);
        }

        function viewClub() {
            const club = document.getElementById('clubPlayers');
            if (club.style.display === 'none') {
                club.style.display = 'flex';
                renderClubPlayers();
            } else {
                club.style.display = 'none';
            }
        }

        function renderClubPlayers() {
            const clubPlayersDiv = document.getElementById('clubPlayers');
            clubPlayersDiv.innerHTML = ''; // Clear previous content
            players.forEach(player => {
                const imgElement = document.createElement('img');
                imgElement.src = imagesFolder + player.image;
                imgElement.alt = player.name;
                clubPlayersDiv.appendChild(imgElement);
            });
        }

        function buyPack() {
            alert('Buy Pack is not yet implemented.');
        }

        function playAgainstBot() {
            alert('Playing against a bot is under development.');
        }

        function playAgainstRealPlayer() {
            alert('Searching for a real player to play...');
        }
    </script>
</body>
</html>

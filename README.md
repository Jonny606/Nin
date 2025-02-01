<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>FIFA Pack Simulator</title>
  <style>
    body {
      background-color: #181818;
      color: white;
      font-family: sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      flex-direction: column;
    }

    .pack-container {
      display: flex;
      justify-content: center;
      margin-bottom: 20px;
    }

    .pack {
      width: 200px;
      height: 100px;
      background-color: #333;
      border: 1px solid #ccc;
      text-align: center;
      padding: 20px;
      cursor: pointer;
      margin: 10px;
      border-radius: 5px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
      position: relative;
      overflow: hidden;
      transform: scale(1);
      transition: all 0.3s ease-in-out;
      background-size: cover;
      background-position: center;
    }

    .pack.opening {
      transform: scale(1.1);
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }

    #playerInfo {
      display: none;
      text-align: center;
      background-color: rgba(0, 0, 0, 0.8);
      padding: 20px;
      border-radius: 5px;
      opacity: 0;
      transition: all 0.5s ease-in-out;
    }

    #playerInfo.show {
      display: block;
      opacity: 1;
    }

    #country, #position, #team, #name, #playerRating {
      font-size: 24px;
      margin-bottom: 10px;
    }

    #playerImage {
      width: 150px;
      border-radius: 5px;
      margin-top: 20px;
      opacity: 0;
      transition: opacity 0.5s ease-in-out;
    }

    #playerImage.show {
      opacity: 1;
    }

    .coins-gems {
      margin-bottom: 20px;
    }

    #club {
      margin-top: 20px;
      padding: 20px;
      background-color: rgba(0, 0, 0, 0.8);
      border-radius: 5px;
      display: none;
    }

    #club.show {
      display: block;
    }

    .hidden {
      display: none;
    }

    #formation {
      font-size: 18px;
      color: #ccc;
    }

    #playButton {
      margin-top: 20px;
      padding: 10px 20px;
      background-color: #007BFF;
      color: white;
      font-size: 18px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    #playButton:disabled {
      background-color: #ccc;
      cursor: not-allowed;
    }

    #botInfo {
      margin-top: 20px;
      font-size: 20px;
    }

    #transferMarket {
      margin-top: 20px;
      padding: 20px;
      background-color: rgba(0, 0, 0, 0.8);
      border-radius: 5px;
      display: none;
    }

    #transferMarket.show {
      display: block;
    }
  </style>
</head>
<body>

  <h1>FIFA Pack Simulator</h1>

  <div class="coins-gems">
    <p>Coins: <span id="coins">200</span> | Gems: <span id="gems">25</span> | Credits: <span id="credits">0</span></p>
  </div>

  <div class="pack-container">
    <div class="pack" onclick="openPack('low')">Low Tier Pack (Cost: 10 Coins)</div>
    <div class="pack" onclick="openPack('medium')">Medium Tier Pack (Cost: 25 Coins)</div>
    <div class="pack" onclick="openPack('high')">High Tier Pack (Cost: 50 Coins)</div>
  </div>

  <div id="playerInfo">
    <h2>Player Information</h2>
    <p id="name"></p>
    <img id="country" src="" alt="Country" style="width: 100px;">
    <p id="position"></p>
    <p id="team"></p>
    <p id="playerRating"></p>
    <img id="playerImage" src="" alt="Player Image">
  </div>

  <div id="club">
    <h2>Your Club</h2>
    <p id="formation">Formation: 4-3-3</p>
    <div id="teamMembers">
      <p>Team Members:</p>
      <!-- Player names will be dynamically added here -->
    </div>
    <button onclick="toggleViewTransferMarket()">View Transfer Market</button>
  </div>

  <div id="transferMarket">
    <h2>Transfer Market</h2>
    <div id="marketPlayers">
      <p>Players Available for Purchase:</p>
      <!-- Market players will be dynamically added here -->
    </div>
    <button onclick="toggleViewTransferMarket()">Close Transfer Market</button>
  </div>

  <button id="viewClubButton" onclick="toggleViewClub()">View Club</button>
  <button id="playButton" onclick="playAgainstBot()">Play Against Bot</button>

  <div id="botInfo"></div>

  <script>
    const playerInfo = document.getElementById('playerInfo');
    const country = document.getElementById('country');
    const position = document.getElementById('position');
    const team = document.getElementById('team');
    const name = document.getElementById('name');
    const playerRating = document.getElementById('playerRating');
    const playerImage = document.getElementById('playerImage');
    const coinsDisplay = document.getElementById('coins');
    const gemsDisplay = document.getElementById('gems');
    const creditsDisplay = document.getElementById('credits');
    const clubSection = document.getElementById('club');
    const teamMembers = document.getElementById('teamMembers');
    const playButton = document.getElementById('playButton');
    const botInfo = document.getElementById('botInfo');
    const transferMarket = document.getElementById('transferMarket');
    const marketPlayers = document.getElementById('marketPlayers');

    let coins = 200;
    let gems = 25;
    let credits = 0;
    let clubPlayers = [];
    let isPackOpen = false;
    let market = [];

    const players = [
      { name: "Lionel Messi", rating: 99, country: "images/Argentina.png", position: "RW", team: "Inter Miami", image: "images/Messi.jpg" },
      { name: "Kylian Mbappé", rating: 98, country: "images/France.png", position: "ST", team: "Paris Saint-Germain", image: "images/Mbappé.jpg" },
      { name: "Pelé", rating: 98, country: "images/Brazil.png", position: "ST", team: "Icon.jpg", image: "images/Pelé.jpg" },
      { name: "Cristiano Ronaldo", rating: 98, country: "images/Portugal.png", position: "ST", team: "Al Nassr", image: "images/Ronaldo.jpg" },
      { name: "Kevin De Bruyne", rating: 95, country: "images/Belgium.png", position: "CM", team: "Manchester City", image: "images/KDB.jpg" },
      { name: "Kaká", rating: 94, country: "images/Brazil.png", position: "CAM", team: "Icon.jpg", image: "images/Kaká.jpg" },
      { name: "Roberto Carlos", rating: 93, country: "images/Brazil.png", position: "LB", team: "Icon.jpg", image: "images/Roberto_Carlos.jpg" },
      { name: "Paolo Maldini", rating: 93, country: "images/Italy.png", position: "CB", team: "Icon.jpg", image: "images/Maldini.jpg" },
      { name: "Casemiro", rating: 89, country: "images/Brazil.png", position: "CDM", team: "Manchester United", image: "images/Casemiro.jpg" },
      { name: "André Onana", rating: 88, country: "images/Cameroon.png", position: "GK", team: "Manchester United", image: "images/Onana.jpg" },
      { name: "Lamine Yamal", rating: 82, country: "images/Spain.png", position: "LW", team: "FC Barcelona", image: "images/Yamal.jpg" },
      { name: "Rodrygo", rating: 87, country: "images/Brazil.png", position: "RW", team: "Real Madrid", image: "images/Rodrygo.jpg" },
      { name: "Rodri", rating: 88, country: "images/Spain.png", position: "CDM", team: "Manchester City", image: "images/Rodri.jpg" },
      { name: "Ruben Dias", rating: 87, country: "images/Portugal.png", position: "CB", team: "Manchester City", image: "images/Dias.jpg" },
      { name: "Alphonso Davies", rating: 88, country: "images/Canada.png", position: "LB", team: "Bayern Munich", image: "images/Davies.jpg" },
      { name: "Lev Yashin", rating: 94, country: "images/Russia.png", position: "GK", team: "Icon.jpg", image: "images/Yashin.jpg" },
      { name: "Joshua Kimmich", rating: 90, country: "images/Germany.png", position: "CM", team: "Bayern Munich", image: "images/Kimmich.jpg" },
      { name: "Dani Carvajal", rating: 88, country: "images/Spain.png", position: "RB", team: "Real Madrid", image: "images/Carvajal.jpg" },
      { name: "David Alaba", rating: 89, country: "images/Austria.png", position: "CB", team: "Real Madrid", image: "images/Alaba.jpg" },
      { name: "Jan Oblak", rating: 91, country: "images/Slovenia.png", position: "GK", team: "Atletico Madrid", image: "images/Oblak.jpg" }
    ];

    function openPack(packType) {
      let cost;
      let rewardCredits;
      if (packType === 'low') {
        cost = 10;
        rewardCredits = 5;
      } else if (packType === 'medium') {
        cost = 25;
        rewardCredits = 15;
      } else if (packType === 'high') {
        cost = 50;
        rewardCredits = 30;
      }

      if (coins >= cost) {
        coins -= cost;
        credits += rewardCredits;
        coinsDisplay.innerText = coins;
        creditsDisplay.innerText = credits;

        const randomPlayer = players[Math.floor(Math.random() * players.length)];
        displayPlayer(randomPlayer);
      } else {
        alert('Not enough coins!');
      }
    }

    function displayPlayer(player) {
      name.textContent = player.name;
      country.src = player.country;
      position.textContent = `Position: ${player.position}`;
      team.textContent = `Team: ${player.team}`;
      playerRating.textContent = `Rating: ${player.rating}`;
      playerImage.src = player.image;

      playerInfo.classList.add('show');
      playerImage.classList.add('show');

      // Add player to club
      clubPlayers.push(player);
      updateClub();
    }

    function updateClub() {
      teamMembers.innerHTML = '<p>Team Members:</p>';
      clubPlayers.forEach((player, index) => {
        const playerElement = document.createElement('div');
        playerElement.innerHTML = `
          <p>${player.name}</p>
          <button onclick="showPlayerStats(${index})">View Stats</button>
          ${player.team === 'Icon.jpg' ? `<button onclick="sellPlayer(${index})">Sell</button>` : ''}
        `;
        teamMembers.appendChild(playerElement);
      });
      clubSection.classList.add('show');
    }

    function toggleViewClub() {
      clubSection.classList.toggle('show');
    }

    function toggleViewTransferMarket() {
      transferMarket.classList.toggle('show');
      if (transferMarket.classList.contains('show')) {
        displayTransferMarket();
      }
    }

    function displayTransferMarket() {
      marketPlayers.innerHTML = '<p>Players Available for Purchase:</p>';
      players.forEach(player => {
        if (!clubPlayers.includes(player)) {
          const playerElement = document.createElement('div');
          playerElement.innerHTML = `
            <p>${player.name}</p>
            <img src="${player.image}" alt="${player.name}" style="width: 50px;">
            <button onclick="buyPlayer('${player.name}')">Buy</button>
          `;
          marketPlayers.appendChild(playerElement);
        }
      });
    }

    function buyPlayer(playerName) {
      const player = players.find(p => p.name === playerName);
      if (player && !clubPlayers.includes(player)) {
        if (coins >= 50) {
          coins -= 50;
          coinsDisplay.innerText = coins;
          clubPlayers.push(player);
          updateClub();
        } else {
          alert('Not enough coins to buy this player!');
        }
      }
    }

    function sellPlayer(index) {
      if (clubPlayers[index].team === 'Icon.jpg') {
        coins += 100;
        coinsDisplay.innerText = coins;
        clubPlayers.splice(index, 1);
        updateClub();
      }
    }

    function showPlayerStats(index) {
      const player = clubPlayers[index];
      const playerStats = `
        <h2>${player.name}</h2>
        <img src="${player.image}" alt="${player.name}" style="width: 100px;">
        <p>Country: <img src="${player.country}" alt="${player.country}" style="width: 20px;"></p>
        <p>Position: ${player.position}</p>
        <p>Team: ${player.team}</p>
        <p>Rating: ${player.rating}</p>
        <button onclick="upgradePlayer(${index})">Upgrade OVR (${calculateUpgradeCost(player.rating)})</button>
      `;
      document.querySelector('#playerInfo').innerHTML = playerStats;
      playerInfo.classList.add('show');
    }

    function calculateUpgradeCost(currentRating) {
      return (currentRating - 80) * 10;  // Example cost calculation: 10 credits per point above 80 OVR
    }

    function upgradePlayer(index) {
      const player = clubPlayers[index];
      const upgradeCost = calculateUpgradeCost(player.rating);
      if (credits >= upgradeCost && player.rating < 104) {  // Max upgrade to 104 (99 + 5)
        credits -= upgradeCost;
        creditsDisplay.innerText = credits;
        player.rating += 1;
        showPlayerStats(index);
        updateClub();
      } else {
        alert('Not enough credits or maximum upgrade reached!');
      }
    }

    function playAgainstBot() {
      if (clubPlayers.length < 11) {
        alert('You need 11 players to play against the bot.');
        return;
      }

      const teamOVR = clubPlayers.reduce((sum, player) => sum + player.rating, 0) / clubPlayers.length;
      const botOVR = 85 + Math.floor(Math.random() * 15); // Bot OVR between 85 and 100

      if (teamOVR > botOVR) {
        coins += 50;
        credits += 20;
        botInfo.textContent = `You won! Your team OVR: ${teamOVR.toFixed(2)}, Bot OVR: ${botOVR}. You earned 50 coins and 20 credits.`;
      } else {
        botInfo.textContent = `You lost! Your team OVR: ${teamOVR.toFixed(2)}, Bot OVR: ${botOVR}. Better luck next time.`;
      }

      coinsDisplay.innerText = coins;
      creditsDisplay.innerText = credits;
    }
  </script>
</body>
</html>
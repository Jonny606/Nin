import React, { useState, useEffect } from 'react';
import { Package, Coins, Gem, CreditCard, Users, ShoppingCart, X, ArrowUp } from 'lucide-react';

// Types
interface Player {
  name: string;
  rating: number;
  country: string;
  position: string;
  team: string;
  image: string;
}

interface Pack {
  type: 'low' | 'medium' | 'high';
  cost: number;
  credits: number;
  label: string;
}

// Players Data
const players: Player[] = [
  // Goalkeepers
  {
    name: "Alisson",
    rating: 99,
    country: "https://flagcdn.com/br.svg",
    position: "GK",
    team: "Liverpool",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p231866.png"
  },
  {
    name: "Thibaut Courtois",
    rating: 91,
    country: "https://flagcdn.com/be.svg",
    position: "GK",
    team: "Real Madrid",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p192119.png"
  },
  {
    name: "Marc-André ter Stegen",
    rating: 89,
    country: "https://flagcdn.com/de.svg",
    position: "GK",
    team: "Barcelona",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p192448.png"
  },
  {
    name: "Gianluigi Donnarumma",
    rating: 87,
    country: "https://flagcdn.com/it.svg",
    position: "GK",
    team: "PSG",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p230621.png"
  },
  {
    name: "Ederson",
    rating: 88,
    country: "https://flagcdn.com/br.svg",
    position: "GK",
    team: "Manchester City",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p210257.png"
  },
  // Center Backs
  {
    name: "Virgil van Dijk",
    rating: 99,
    country: "https://flagcdn.com/nl.svg",
    position: "CB",
    team: "Liverpool",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p203376.png"
  },
  {
    name: "Rúben Dias",
    rating: 89,
    country: "https://flagcdn.com/pt.svg",
    position: "CB",
    team: "Manchester City",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p239818.png"
  },
  {
    name: "Antonio Rüdiger",
    rating: 87,
    country: "https://flagcdn.com/de.svg",
    position: "CB",
    team: "Real Madrid",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p205452.png"
  },
  {
    name: "Marquinhos",
    rating: 88,
    country: "https://flagcdn.com/br.svg",
    position: "CB",
    team: "PSG",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p207865.png"
  },
  {
    name: "William Saliba",
    rating: 85,
    country: "https://flagcdn.com/fr.svg",
    position: "CB",
    team: "Arsenal",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p246669.png"
  },
  // Right Backs
  {
    name: "Trent Alexander-Arnold",
    rating: 99,
    country: "https://flagcdn.com/gb-eng.svg",
    position: "RB",
    team: "Liverpool",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p231281.png"
  },
  {
    name: "João Cancelo",
    rating: 88,
    country: "https://flagcdn.com/pt.svg",
    position: "RB",
    team: "Barcelona",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p210514.png"
  },
  {
    name: "Achraf Hakimi",
    rating: 86,
    country: "https://flagcdn.com/ma.svg",
    position: "RB",
    team: "PSG",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p235212.png"
  },
  {
    name: "Reece James",
    rating: 85,
    country: "https://flagcdn.com/gb-eng.svg",
    position: "RB",
    team: "Chelsea",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p238074.png"
  },
  {
    name: "Kyle Walker",
    rating: 84,
    country: "https://flagcdn.com/gb-eng.svg",
    position: "RB",
    team: "Manchester City",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p188377.png"
  },
  // Left Backs
  {
    name: "Theo Hernández",
    rating: 99,
    country: "https://flagcdn.com/fr.svg",
    position: "LB",
    team: "AC Milan",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p226221.png"
  },
  {
    name: "Andy Robertson",
    rating: 87,
    country: "https://flagcdn.com/gb-sct.svg",
    position: "LB",
    team: "Liverpool",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p216267.png"
  },
  {
    name: "Alphonso Davies",
    rating: 86,
    country: "https://flagcdn.com/ca.svg",
    position: "LB",
    team: "Bayern Munich",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p234396.png"
  },
  {
    name: "Ferland Mendy",
    rating: 84,
    country: "https://flagcdn.com/fr.svg",
    position: "LB",
    team: "Real Madrid",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p228618.png"
  },
  {
    name: "Ben Chilwell",
    rating: 83,
    country: "https://flagcdn.com/gb-eng.svg",
    position: "LB",
    team: "Chelsea",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p225659.png"
  },
  // CAMs
  {
    name: "Kevin De Bruyne",
    rating: 99,
    country: "https://flagcdn.com/be.svg",
    position: "CAM",
    team: "Manchester City",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p192985.png"
  },
  {
    name: "Bruno Fernandes",
    rating: 88,
    country: "https://flagcdn.com/pt.svg",
    position: "CAM",
    team: "Manchester United",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p212198.png"
  },
  {
    name: "Martin Ødegaard",
    rating: 87,
    country: "https://flagcdn.com/no.svg",
    position: "CAM",
    team: "Arsenal",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p222665.png"
  },
  {
    name: "Bernardo Silva",
    rating: 86,
    country: "https://flagcdn.com/pt.svg",
    position: "CAM",
    team: "Manchester City",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p218667.png"
  },
  {
    name: "Phil Foden",
    rating: 85,
    country: "https://flagcdn.com/gb-eng.svg",
    position: "CAM",
    team: "Manchester City",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p237692.png"
  },
  // CDMs
  {
    name: "Rodri",
    rating: 99,
    country: "https://flagcdn.com/es.svg",
    position: "CDM",
    team: "Manchester City",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p231866.png"
  },
  {
    name: "Casemiro",
    rating: 89,
    country: "https://flagcdn.com/br.svg",
    position: "CDM",
    team: "Manchester United",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p200145.png"
  },
  {
    name: "Joshua Kimmich",
    rating: 88,
    country: "https://flagcdn.com/de.svg",
    position: "CDM",
    team: "Bayern Munich",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p212622.png"
  },
  {
    name: "Declan Rice",
    rating: 86,
    country: "https://flagcdn.com/gb-eng.svg",
    position: "CDM",
    team: "Arsenal",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p234378.png"
  },
  {
    name: "Aurélien Tchouaméni",
    rating: 84,
    country: "https://flagcdn.com/fr.svg",
    position: "CDM",
    team: "Real Madrid",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p241637.png"
  },
  // Right Wingers
  {
    name: "Lionel Messi",
    rating: 99,
    country: "https://flagcdn.com/ar.svg",
    position: "RW",
    team: "Inter Miami",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p158023.png"
  },
  {
    name: "Mohamed Salah",
    rating: 89,
    country: "https://flagcdn.com/eg.svg",
    position: "RW",
    team: "Liverpool",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p209331.png"
  },
  {
    name: "Bukayo Saka",
    rating: 86,
    country: "https://flagcdn.com/gb-eng.svg",
    position: "RW",
    team: "Arsenal",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p246669.png"
  },
  {
    name: "Raphinha",
    rating: 85,
    country: "https://flagcdn.com/br.svg",
    position: "RW",
    team: "Barcelona",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p231943.png"
  },
  {
    name: "Rodrygo",
    rating: 84,
    country: "https://flagcdn.com/br.svg",
    position: "RW",
    team: "Real Madrid",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p243812.png"
  },
  // Left Wingers
  {
    name: "Vinícius Júnior",
    rating: 99,
    country: "https://flagcdn.com/br.svg",
    position: "LW",
    team: "Real Madrid",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p238794.png"
  },
  {
    name: "Son Heung-min",
    rating: 88,
    country: "https://flagcdn.com/kr.svg",
    position: "LW",
    team: "Tottenham",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p200104.png"
  },
  {
    name: "Rafael Leão",
    rating: 86,
    country: "https://flagcdn.com/pt.svg",
    position: "LW",
    team: "AC Milan",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p241721.png"
  },
  {
    name: "Jack Grealish",
    rating: 85,
    country: "https://flagcdn.com/gb-eng.svg",
    position: "LW",
    team: "Manchester City",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p213619.png"
  },
  {
    name: "Cody Gakpo",
    rating: 84,
    country: "https://flagcdn.com/nl.svg",
    position: "LW",
    team: "Liverpool",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p242516.png"
  },
  // Strikers
  {
    name: "Erling Haaland",
    rating: 99,
    country: "https://flagcdn.com/no.svg",
    position: "ST",
    team: "Manchester City",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p239085.png"
  },
  {
    name: "Harry Kane",
    rating: 90,
    country: "https://flagcdn.com/gb-eng.svg",
    position: "ST",
    team: "Bayern Munich",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p202126.png"
  },
  {
    name: "Victor Osimhen",
    rating: 88,
    country: "https://flagcdn.com/ng.svg",
    position: "ST",
    team: "Napoli",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p235805.png"
  },
  {
    name: "Gabriel Jesus",
    rating: 85,
    country: "https://flagcdn.com/br.svg",
    position: "ST",
    team: "Arsenal",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p230666.png"
  },
  {
    name: "Darwin Núñez",
    rating: 84,
    country: "https://flagcdn.com/uy.svg",
    position: "ST",
    team: "Liverpool",
    image: "https://www.fifacm.com/content/media/imgs/fifa23/players/p247819.png"
  }
];

// Helper Functions
function getPackProbabilities(packType: string) {
  switch (packType) {
    case 'low':
      return { 99: 0.01, 90: 0.05, 85: 0.14, 80: 0.80 };
    case 'medium':
      return { 99: 0.03, 90: 0.10, 85: 0.27, 80: 0.60 };
    case 'high':
      return { 99: 0.05, 90: 0.15, 85: 0.40, 80: 0.40 };
    default:
      return { 99: 0.01, 90: 0.05, 85: 0.14, 80: 0.80 };
  }
}

function calculatePlayerPrice(rating: number): number {
  if (rating >= 99) return 1000;
  if (rating >= 90) return 500;
  if (rating >= 85) return 250;
  if (rating >= 80) return 100;
  return 50;
}

// Components
function PlayerCard({ player, onClose }: { player: Player; onClose: () => void }) {
  return (
    <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center">
      <div className="bg-gray-800 p-8 rounded-lg relative max-w-md w-full">
        <button
          onClick={onClose}
          className="absolute top-4 right-4 text-gray-400 hover:text-white"
        >
          <X size={24} />
        </button>
        
        <div className="text-center">
          <h2 className="text-2xl font-bold mb-4">{player.name}</h2>
          <img
            src={player.country}
            alt="Country flag"
            className="w-16 h-auto mx-auto mb-4"
          />
          <img
            src={player.image}
            alt={player.name}
            className="w-48 h-48 object-cover mx-auto rounded-lg mb-4"
          />
          <div className="space-y-2">
            <p>Position: {player.position}</p>
            <p>Team: {player.team}</p>
            <p>Rating: {player.rating}</p>
          </div>
        </div>
      </div>
    </div>
  );
}

function PackOpening({ pack, onOpen }: { pack: Pack; onOpen: () => void }) {
  return (
    <button
      onClick={onOpen}
      className="bg-gray-800 p-6 rounded-lg flex flex-col items-center gap-4 hover:bg-gray-700 transition-colors"
    >
      <Package size={48} className="text-purple-500" />
      <div className="text-center">
        <h3 className="text-xl font-semibold mb-2">{pack.label}</h3>
        <p className="text-gray-400">Cost: {pack.cost} Coins</p>
      </div>
    </button>
  );
}

function Club({ players, onClose, credits, setCredits, setPlayers }: {
  players: Player[];
  onClose: () => void;
  credits: number;
  setCredits: (credits: number) => void;
  setPlayers: (players: Player[]) => void;
}) {
  const calculateUpgradeCost = (rating: number) => (rating - 80) * 10;

  const upgradePlayer = (index: number) => {
    const player = players[index];
    const cost = calculateUpgradeCost(player.rating);
    
    if (credits >= cost && player.rating < 104) {
      setCredits(credits - cost);
      const updatedPlayers = [...players];
      updatedPlayers[index] = { ...player, rating: player.rating + 1 };
      setPlayers(updatedPlayers);
    } else {
      alert('Not enough credits or maximum upgrade reached!');
    }
  };

  return (
    <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center overflow-auto">
      <div className="bg-gray-800 p-8 rounded-lg relative max-w-4xl w-full m-4">
        <button
          onClick={onClose}
          className="absolute top-4 right-4 text-gray-400 hover:text-white"
        >
          <X size={24} />
        </button>
        
        <h2 className="text-2xl font-bold mb-6">Your Club</h2>
        
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          {players.map((player, index) => (
            <div key={index} className="bg-gray-700 p-4 rounded-lg">
              <img
                src={player.image}
                alt={player.name}
                className="w-full h-48 object-cover rounded-lg mb-4"
              />
              <div className="space-y-2">
                <h3 className="font-semibold">{player.name}</h3>
                <p>Rating: {player.rating}</p>
                <button
                  onClick={() => upgradePlayer(index)}
                  className="flex items-center gap-2 bg-purple-600 hover:bg-purple-700 px-4 py-2 rounded-lg w-full justify-center"
                >
                  <ArrowUp size={16} />
                  Upgrade ({calculateUpgradeCost(player.rating)} credits)
                </button>
              </div>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}

function TransferMarket({ availablePlayers, coins, setCoins, onPlayerBuy, onClose }: {
  availablePlayers: Player[];
  coins: number;
  setCoins: (coins: number) => void;
  onPlayerBuy: (player: Player) => void;
  onClose: () => void;
}) {
  const buyPlayer = (player: Player) => {
    const price = calculatePlayerPrice(player.rating);
    if (coins >= price) {
      setCoins(coins - price);
      onPlayerBuy(player);
    } else {
      alert('Not enough coins to buy this player!');
    }
  };

  return (
    <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center overflow-auto">
      <div className="bg-gray-800 p-8 rounded-lg relative max-w-4xl w-full m-4">
        <button
          onClick={onClose}
          className="absolute top-4 right-4 text-gray-400 hover:text-white"
        >
          <X size={24} />
        </button>
        
        <h2 className="text-2xl font-bold mb-6">Transfer Market</h2>
        
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          {availablePlayers.map((player, index) => (
            <div key={index} className="bg-gray-700 p-4 rounded-lg">
              <img
                src={player.image}
                alt={player.name}
                className="w-full h-48 object-cover rounded-lg mb-4"
              />
              <div className="space-y-2">
                <h3 className="font-semibold">{player.name}</h3>
                <p>Rating: {player.rating}</p>
                <p>Position: {player.position}</p>
                <p className="text-yellow-400">Price: {calculatePlayerPrice(player.rating)} coins</p>
                <button
                  onClick={() => buyPlayer(player)}
                  className="flex items-center gap-2 bg-green-600 hover:bg-green-700 px-4 py-2 rounded-lg w-full justify-center"
                >
                  <ShoppingCart size={16} />
                  Buy Now
                </button>
              </div>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}

// Main App Component
function App() {
  const [coins, setCoins] = useState(200);
  const [gems, setGems] = useState(25);
  const [credits, setCredits] = useState(0);
  const [clubPlayers, setClubPlayers] = useState<Player[]>([]);
  const [selectedPlayer, setSelectedPlayer] = useState<Player | null>(null);
  const [showClub, setShowClub] = useState(false);
  const [showMarket, setShowMarket] = useState(false);
  const [botInfo, setBotInfo] = useState('');
  const [isPlaying, setIsPlaying] = useState(false);
  const [timer, setTimer] = useState(30);
  const [matchScore, setMatchScore] = useState({ player: 0, bot: 0 });

  const packs: Pack[] = [
    { type: 'low', cost: 10, credits: 5, label: 'Low Tier Pack' },
    { type: 'medium', cost: 25, credits: 15, label: 'Medium Tier Pack' },
    { type: 'high', cost: 50, credits: 30, label: 'High Tier Pack' }
  ];

  useEffect(() => {
    let interval: number;
    if (isPlaying && timer > 0) {
      interval = setInterval(() => {
        setTimer(prev => prev - 1);
      }, 1000);
    } else if (timer === 0) {
      setIsPlaying(false);
      setTimer(30);
    }
    return () => clearInterval(interval);
  }, [isPlaying, timer]);

  const openPack = (pack: Pack) => {
    if (coins >= pack.cost) {
      setCoins(prev => prev - pack.cost);
      setCredits(prev => prev + pack.credits);
      
      const probabilities = getPackProbabilities(pack.type);
      const rand = Math.random();
      
      let playerPool;
      if (rand < probabilities[99]) {
        playerPool = players.filter(p => p.rating === 99);
      } else if (rand < probabilities[99] + probabilities[90]) {
        playerPool = players.filter(p => p.rating >= 90 && p.rating < 99);
      } else if (rand < probabilities[99] + probabilities[90] + probabilities[85]) {
        playerPool = players.filter(p => p.rating >= 85 && p.rating < 90);
      } else {
        playerPool = players.filter(p => p.rating < 85);
      }
      
      const randomPlayer = playerPool[Math.floor(Math.random() * playerPool.length)];
      setSelectedPlayer(randomPlayer);
      setClubPlayers(prev => [...prev, randomPlayer]);
    } else {
      alert('Not enough coins!');
    }
  };

  const calculateWinChance = (teamOVR: number, botOVR: number) => {
    const difference = teamOVR - botOVR;
    const baseChance = 50;
    const modifier = difference * 5;
    return Math.min(Math.max(baseChance + modifier, 10), 90);
  };

  const simulateGoals = (winChance: number) => {
    const playerGoals = Math.floor(Math.random() * 5);
    let botGoals;
    
    if (Math.random() * 100 < winChance) {
      botGoals = Math.max(0, playerGoals - Math.floor(Math.random() * 3));
    } else {
      botGoals = playerGoals + 1 + Math.floor(Math.random() * 2);
    }

    return { playerGoals, botGoals };
  };

  const playAgainstBot = () => {
    if (clubPlayers.length < 11) {
      alert('You need 11 players to play against the bot.');
      return;
    }

    if (isPlaying) {
      alert('Please wait for the current match to finish!');
      return;
    }

    setIsPlaying(true);
    setTimer(30);

    const teamOVR = clubPlayers.reduce((sum, player) => sum + player.rating, 0) / clubPlayers.length;
    const botOVR = 85 + Math.floor(Math.random() * 15);
    const winChance = calculateWinChance(teamOVR, botOVR);
    const { playerGoals, botGoals } = simulateGoals(winChance);

    setMatchScore({ player: playerGoals, bot: botGoals });

    if (playerGoals > botGoals) {
      setCoins(prev => prev + 50);
      setCredits(prev => prev + 20);
      setBotInfo(`Victory! (${playerGoals}-${botGoals})\nYour team OVR: ${teamOVR.toFixed(1)}\nBot OVR: ${botOVR}\nWin Chance: ${winChance.toFixed(1)}%\nRewards: 50 coins, 20 credits`);
    } else if (playerGoals < botGoals) {
      setBotInfo(`Defeat! (${playerGoals}-${botGoals})\nYour team OVR: ${teamOVR.toFixed(1)}\nBot OVR: ${botOVR}\nWin Chance: ${winChance.toFixed(1)}%`);
    } else {
      setCoins(prev => prev + 25);
      setCredits(prev => prev + 10);
      setBotInfo(`Draw! (${playerGoals}-${botGoals})\nYour team OVR: ${teamOVR.toFixed(1)}\nBot OVR: ${botOVR}\nWin Chance: ${winChance.toFixed(1)}%\nRewards: 25 coins, 10 credits`);
    }
  };

  return (
    <div className="min-h-screen bg-gray-900 text-white p-8">
      <h1 className="text-4xl font-bold text-center mb-8">FIFA Pack Simulator</h1>
      
      <div className="flex justify-center gap-8 mb-8">
        <div className="flex items-center gap-2">
          <Coins className="text-yellow-400" />
          <span>{coins}</span>
        </div>
        <div className="flex items-center gap-2">
          <Gem className="text-purple-400" />
          <span>{gems}</span>
        </div>
        <div className="flex items-center gap-2">
          <CreditCard className="text-green-400" />
          <span>{credits}</span>
        </div>
      </div>

      <div className="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
        {packs.map((pack) => (
          <PackOpening
            key={pack.type}
            pack={pack}
            onOpen={() => openPack(pack)}
          />
        ))}
      </div>

      {selectedPlayer && (
        <PlayerCard
          player={selectedPlayer}
          onClose={() => setSelectedPlayer(null)}
        /> )}

      <div className="flex justify-center gap-4 mb-8">
        <button
          onClick={() => setShowClub(!showClub)}
          className="flex items-center gap-2 bg-blue-600 hover:bg-blue-700 px-6 py-3 rounded-lg"
        >
          <Users size={20} />
          View Club
        </button>
        <button
          onClick={() => setShowMarket(!showMarket)}
          className="flex items-center gap-2 bg-green-600 hover:bg-green-700 px-6 py-3 rounded-lg"
        >
          <ShoppingCart size={20} />
          Transfer Market
        </button>
        <button
          onClick={playAgainstBot}
          disabled={isPlaying || clubPlayers.length < 11}
          className="bg-purple-600 hover:bg-purple-700 disabled:bg-gray-600 px-6 py-3 rounded-lg flex items-center gap-2"
        >
          Play Against Bot {isPlaying && `(${timer}s)`}
        </button>
      </div>

      {botInfo && (
        <div className="text-center space-y-2 mb-8">
          <div className="text-3xl font-bold mb-4">
            {matchScore.player} - {matchScore.bot}
          </div>
          <div className="text-xl whitespace-pre-line p-4 bg-gray-800 rounded-lg">
            {botInfo}
          </div>
        </div>
      )}

      {showClub && (
        <Club
          players={clubPlayers}
          onClose={() => setShowClub(false)}
          credits={credits}
          setCredits={setCredits}
          setPlayers={setClubPlayers}
        />
      )}

      {showMarket && (
        <TransferMarket
          availablePlayers={players.filter(p => !clubPlayers.includes(p))}
          coins={coins}
          setCoins={setCoins}
          onPlayerBuy={(player) => setClubPlayers(prev => [...prev, player])}
          onClose={() => setShowMarket(false)}
        />
      )}
    </div>
  );
}

export default App;

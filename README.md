# Koalang Censorship Game

A multiplayer communication game that combines elements of Pictionary with censorship evasion mechanics. Players use the Koalang sci-fi language to communicate hidden messages while avoiding detection by an AI censorship system.

## Game Overview

The Koalang Censorship Game features role-based gameplay where one player (the **Wordsmith**) attempts to convey secret messages to other players (**Guessers**) without being caught by AI-powered censorship detection.

### How It Works

1. **Setup**: 3-8 players join a game room
2. **Challenge**: The Wordsmith receives a secret message with thematic context (theme, setting, example)
3. **Communication**: The Wordsmith sends multiple messages in Koalang to convey the hidden meaning
4. **Censorship**: Each message is analyzed by a "weaker" AI model trying to detect the real meaning
5. **Guessing**: Other players interpret the messages and submit their guesses
6. **Validation**: A "stronger" AI model validates whether guesses match the hidden message
7. **Scoring**: Points are awarded for successful communication and correct guesses

### Example Challenges

Here are some sample challenges that demonstrate the range of difficulty levels and creative themes:

#### Easy Challenges
```json
{
  "round": 1,
  "difficulty": "Easy",
  "hidden": "Datadog's dashboards are unreliable lately.",
  "theme": "Medieval town gossip.",
  "setting": "Lunchtime at a crepe stand in the \"old quarter\" of a fantasy town built in Minecraft during a weekend team jam.",
  "example": "This morning the watchtower's bell rang thrice, but the sound drowned under the clatter of copper pots in the square. By evening, the mayor's hound was asleep in the sun while the caravan passed the east gate. Have you tried the baker's new plum tarts?"
}
```

```json
{
  "round": 2,
  "difficulty": "Easy",
  "hidden": "QA environment is too slow for meaningful testing.",
  "theme": "Ancient sea trade.",
  "setting": "Leaning on the rail of a tall ship in the middle of the office \"virtual sailing regatta\" game world.",
  "example": "Our galley has sat in the harbor so long the figs in the hold have turned to wine. The tide whispers it might turn next moon, but even the dock rats have moved on. Speaking of, I found an old coin under my chair yesterday."
}
```

#### Medium Challenges
```json
{
  "round": 4,
  "difficulty": "Medium",
  "hidden": "GitHub Actions keep failing randomly.",
  "theme": "Victorian factory.",
  "setting": "Tea break in the dusty corner of our pretend \"Team Steamworks\" factory simulator map.",
  "example": "The brass gear on line three seized again, sending soot through the glass roof. Foreman says the belts will run by nightfall, but the pigeons nesting in the rafters seem unconvinced. I might bring an umbrella tomorrow."
}
```

```json
{
  "round": 6,
  "difficulty": "Medium",
  "hidden": "I recommend you go to Slovenia.",
  "theme": "Fairy tale quest.",
  "setting": "Lunch on the terrace of the \"Green Vale Inn\" in our shared D&D side campaign map.",
  "example": "Past the emerald lake, the road bends into valleys where the wind holds its breath. There's an inn there with green-ink maps and honey wine. The miller says no traveler has returned unhappy, though the blacksmith swears the mountains hum at dusk."
}
```

#### Hard Challenges
```json
{
  "round": 7,
  "difficulty": "Hard",
  "hidden": "Flights are expensive when children are out of school.",
  "theme": "Seasonal farming.",
  "setting": "Fruit stand at the \"Harvest Fair\" in our virtual Stardew Valley co-op farm.",
  "example": "When the orchards are ripe, the wagons cost thrice their weight in silver, for the children have left the fields to chase dragonflies. Wait for the frost, and the roads grow cheaper, though the apples lose their blush."
}
```

```json
{
  "round": 9,
  "difficulty": "Hard",
  "hidden": "My new hobby is baking bread.",
  "theme": "Mechanical engineering.",
  "setting": "Tool bench in the \"Clockmaker's Loft\" world we sometimes meet in on Gather Town.",
  "example": "I've been tuning a small furnace, adjusting the pressure to coax a perfect rise in the central chamber. The vents release the most satisfying aroma when the cycle ends. Next week, I'll try a sour mix of gears."
}
```

#### Very Hard Challenge
```json
{
  "round": 10,
  "difficulty": "Very Hard",
  "hidden": "I can't join Friday's after-work call; I'll be hiking.",
  "theme": "Old-school video gaming.",
  "setting": "Pixel-art mountain pass in our team's custom Terraria server.",
  "example": "Skipping the Friday dungeon raid — I found a hidden mountain level that only unlocks in single-player mode. The sprites are shy, and the air meter runs slow. Might take a screenshot if I survive the cliff boss."
}
```

Notice how the challenges cleverly disguise modern workplace and personal situations within fantasy and historical contexts, requiring players to be creative with their language while staying true to the thematic setting.

## Features

- **Real-time Multiplayer**: WebSocket-based communication for instant updates
- **AI-Powered Gameplay**: Dual AI system for censorship detection and meaning validation
- **Rich Challenge System**: Curated challenges with themes, settings, and difficulty levels
- **Configurable Games**: Customizable round timers, point values, and difficulty filters
- **Admin Panel**: Challenge management interface for content curation
- **Responsive Design**: Works across desktop and mobile devices

## Tech Stack

### Backend
- **Node.js** with Express.js
- **Socket.IO** for real-time communication
- **TypeScript** for type safety
- **AI Integration** (OpenAI GPT models or similar)

### Frontend
- **React** with TypeScript
- **Socket.IO Client** for real-time updates
- **Context API** for state management
- **Responsive CSS** for cross-device compatibility

### Data Storage
- **JSON/JSONL** files for challenge storage
- **In-memory** game state with Redis backup
- **JWT** for session management

## Project Structure

```
koalang-censorship-game/
├── backend/
│   ├── src/
│   │   ├── services/
│   │   │   ├── GameEngine.js
│   │   │   ├── AIService.js
│   │   │   └── WebSocketServer.js
│   │   ├── models/
│   │   ├── routes/
│   │   └── app.js
│   ├── data/
│   │   └── challenges.json
│   └── package.json
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── GameLobby.tsx
│   │   │   ├── WordsmithView.tsx
│   │   │   ├── GuesserView.tsx
│   │   │   └── GameBoard.tsx
│   │   ├── services/
│   │   └── App.tsx
│   └── package.json
├── .kiro/
│   └── specs/
│       └── koalang-censorship-game/
│           ├── requirements.md
│           ├── design.md
│           └── tasks.md
└── README.md
```

## Getting Started

### Prerequisites

- Node.js 18+ 
- npm or yarn
- AI API keys (OpenAI, Anthropic, etc.)

### Installation

1. Clone the repository
```bash
git clone <repository-url>
cd koalang-censorship-game
```

2. Install backend dependencies
```bash
cd backend
npm install
```

3. Install frontend dependencies
```bash
cd ../frontend
npm install
```

4. Configure environment variables
```bash
# backend/.env
AI_API_KEY=your_ai_api_key
PORT=3001
CORS_ORIGIN=http://localhost:3000
```

5. Start the development servers
```bash
# Terminal 1 - Backend
cd backend
npm run dev

# Terminal 2 - Frontend  
cd frontend
npm start
```

6. Open http://localhost:3000 in your browser

## Game Rules

### Roles

- **Wordsmith**: Receives the secret challenge and must convey it using creative language
- **Guessers**: Interpret the Wordsmith's messages and submit their guesses
- **Censorship AI**: Attempts to detect the real meaning (weaker model for game balance)
- **Judge AI**: Validates whether guesses match the hidden message (stronger model for accuracy)

### Scoring

- **Successful Evasion**: Wordsmith earns points when messages pass censorship
- **Correct Guesses**: Both Guesser and Wordsmith earn points for successful communication
- **Caught by Censorship**: Round ends, Wordsmith loses points

### Round Flow

1. Wordsmith receives challenge (hidden message + context)
2. Other players see only theme and setting
3. Wordsmith sends messages progressively building the meaning
4. Each message is checked by censorship AI
5. If not caught, message is broadcast to Guessers
6. Guessers submit interpretations
7. Judge AI validates guesses
8. Round ends when timer expires or censorship catches the Wordsmith

## Development

### Running Tests

```bash
# Backend tests
cd backend
npm test

# Frontend tests
cd frontend
npm test
```

### Building for Production

```bash
# Build frontend
cd frontend
npm run build

# Build backend
cd backend
npm run build
```

### Adding New Challenges

Edit `backend/data/challenges.json` or use the admin panel:

```json
{
  "round": 11,
  "difficulty": "Medium",
  "hidden": "Your actual message here",
  "theme": "Thematic context",
  "setting": "Environmental description", 
  "example": "Example Koalang message showing the style"
}
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Workflow

This project follows spec-driven development. See the `.kiro/specs/koalang-censorship-game/` directory for:

- **requirements.md**: Detailed user stories and acceptance criteria
- **design.md**: Technical architecture and component specifications  
- **tasks.md**: Implementation plan with actionable coding tasks

To contribute:
1. Review the spec documents to understand the requirements
2. Pick a task from `tasks.md` 
3. Implement the task following the design specifications
4. Write tests for your implementation
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Inspired by the Koalang sci-fi language concept
- Built for creative communication and censorship resistance themes
- Designed as a fun multiplayer party game

## Support

For questions, issues, or feature requests, please open an issue on GitHub or contact the development team.

---

**Ready to play?** Start a game and see if you can outsmart the AI censorship system! 🎮
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

### Example Challenge

```json
{
  "difficulty": "Easy",
  "hidden": "Datadog's dashboards are unreliable lately.",
  "theme": "Medieval town gossip",
  "setting": "Lunchtime at a crepe stand in the old quarter of a fantasy town",
  "example": "This morning the watchtower's bell rang thrice, but the sound drowned under the clatter of copper pots in the square..."
}
```

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
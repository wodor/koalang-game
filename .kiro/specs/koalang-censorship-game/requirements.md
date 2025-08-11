# Requirements Document

## Introduction

The Koalang Censorship Game is a multiplayer communication game that combines elements of Pictionary with censorship evasion mechanics. Players use the Koalang sci-fi language to communicate hidden messages while avoiding detection by an AI censorship system. The game features role-based gameplay where one player (the Wordsmith) attempts to convey secret messages to other players (Guessers) without being caught by the censorship AI.

## Requirements

### Requirement 1

**User Story:** As a game host, I want to set up a new game session with multiple players, so that we can start playing the Koalang Censorship Game together.

#### Acceptance Criteria

1. WHEN a host creates a new game session THEN the system SHALL generate a unique game room ID
2. WHEN players join using the room ID THEN the system SHALL add them to the game lobby
3. WHEN the minimum number of players (3) join THEN the system SHALL allow the host to start the game
4. IF the maximum number of players (8) is reached THEN the system SHALL prevent additional players from joining

### Requirement 2

**User Story:** As a Wordsmith, I want to receive a secret challenge with hidden message, theme, setting, and example, so that I can craft Koalang messages that convey the hidden meaning within the thematic context.

#### Acceptance Criteria

1. WHEN a new round starts THEN the system SHALL randomly select a challenge from the curated list with difficulty rating
2. WHEN the challenge is selected THEN the system SHALL display the hidden message, theme, setting, and example only to the current Wordsmith
3. WHEN the Wordsmith views the complete challenge THEN the system SHALL start the round timer
4. WHEN other players view the game state THEN they SHALL only see the theme and setting context, not the hidden message or example
5. IF the round timer expires THEN the system SHALL end the round and rotate to the next Wordsmith

### Requirement 3

**User Story:** As a Wordsmith, I want to send multiple messages in Koalang that progressively convey my challenge message, so that other players can guess the real meaning while avoiding censorship detection.

#### Acceptance Criteria

1. WHEN the Wordsmith submits a message THEN the system SHALL process it through the censorship AI
2. WHEN the censorship AI analyzes the message THEN it SHALL attempt to guess the real meaning based on all previous messages in the round
3. IF the censorship AI correctly identifies the challenge message THEN the system SHALL end the round and the Wordsmith ends his round
4. IF the censorship AI fails to identify the challenge message THEN the system SHALL broadcast the message to all Guessers in real-time
5. WHEN a message is broadcast THEN the system SHALL display it immediately to all players and log it for the round history
6. WHEN the Wordsmith sends multiple messages THEN each SHALL be processed individually but the censorship AI SHALL consider the cumulative context
7. IF the round is still active THEN the Wordsmith SHALL be able to continue sending additional messages

### Requirement 4

**User Story:** As a Guesser, I want to submit my interpretation of the Wordsmith's messages, so that I can earn points by correctly identifying the hidden meaning.

#### Acceptance Criteria

1. WHEN a Guesser receives a Wordsmith message THEN the system SHALL allow them to submit their interpretation
2. WHEN a Guesser submits an interpretation THEN the system SHALL process it through the meaning validation AI
3. IF the meaning validation AI confirms the interpretation matches the challenge message THEN both the Guesser and Wordsmith SHALL earn points
4. WHEN a Guesser makes a correct guess THEN the system SHALL mark them as having completed the round and they SHALL wait for others to finish
5. WHEN a Guesser has made a correct guess THEN they SHALL no longer be able to submit additional interpretations for that round
6. IF multiple Guessers submit correct interpretations THEN all correct Guessers SHALL earn points
7. WHEN the round timer expires OR the censorship AI catches the Wordsmith THEN the system SHALL end the round and display results

### Requirement 5

**User Story:** As a player, I want to see real-time game state updates including scores, round progress, and message history, so that I can track the game progress and my performance.

#### Acceptance Criteria

1. WHEN any game event occurs THEN the system SHALL update all players' game state in real-time
2. WHEN points are awarded THEN the system SHALL update the scoreboard immediately
3. WHEN a round ends THEN the system SHALL display round results including correct answer and point distribution
4. WHEN the game ends THEN the system SHALL display final scores and declare winners
5. IF a player disconnects THEN the system SHALL handle the disconnection gracefully and continue the game

### Requirement 6

**User Story:** As a game administrator, I want to manage the curated list of challenge rounds with their difficulty levels, hidden messages, themes, settings, and examples, so that the game content remains fresh and appropriately challenging.

#### Acceptance Criteria

1. WHEN an administrator accesses the admin panel THEN the system SHALL display the current list of challenge rounds with all components
2. WHEN an administrator adds a new challenge round THEN the system SHALL validate that it contains round number, difficulty, hidden message, theme, setting, and example
3. WHEN an administrator removes a challenge round THEN the system SHALL remove it from future game rounds
4. WHEN an administrator modifies a challenge round THEN the system SHALL update all components in the curated list
5. WHEN challenges are filtered by difficulty THEN the system SHALL allow selection based on Easy, Medium, Hard, and Very Hard categories
6. IF the curated list becomes empty THEN the system SHALL prevent new games from starting

### Requirement 7

**User Story:** As a system, I want to use multiple AI models for censorship detection and meaning validation, so that the game mechanics function correctly with appropriate difficulty levels.

#### Acceptance Criteria

1. WHEN the system initializes THEN it SHALL configure a weaker AI model for censorship detection to make the game easier
2. WHEN the system initializes THEN it SHALL configure a stronger AI model for meaning validation to ensure accuracy
3. WHEN the censorship AI processes a message THEN it SHALL return a confidence score with its guess
4. WHEN the meaning validation AI processes interpretations THEN it SHALL determine if they match the challenge message
5. IF any AI model fails to respond THEN the system SHALL handle the error gracefully and continue the game

### Requirement 8

**User Story:** As a system, I want to store and manage challenge rounds in a structured format with all necessary components, so that the game can provide rich thematic context and examples.

#### Acceptance Criteria

1. WHEN a challenge round is stored THEN it SHALL contain round number, difficulty level, hidden message, theme, setting, and example text
2. WHEN challenges are loaded THEN the system SHALL validate that all required fields are present and properly formatted
3. WHEN displaying challenges to administrators THEN the system SHALL show all components in an organized format
4. WHEN selecting random challenges THEN the system SHALL ensure equal distribution across difficulty levels unless filtered
5. IF a challenge is missing required components THEN the system SHALL exclude it from game selection and log the error

### Requirement 9

**User Story:** As a player, I want the game to have configurable settings like round duration, point values, and difficulty filtering, so that we can customize the gameplay experience.

#### Acceptance Criteria

1. WHEN a host creates a game THEN the system SHALL allow them to set round duration (30-300 seconds)
2. WHEN a host creates a game THEN the system SHALL allow them to set point values for correct guesses and successful evasion
3. WHEN a host creates a game THEN the system SHALL allow them to set the number of rounds per game
4. WHEN a host creates a game THEN the system SHALL allow them to filter challenges by difficulty level (Easy, Medium, Hard, Very Hard)
5. WHEN game settings are changed THEN the system SHALL apply them to the current game session
6. IF invalid settings are provided THEN the system SHALL use default values and notify the host
# Bagh Bandi: An AI Adversarial Game
![AI](https://img.shields.io/badge/AI-Adversarial-orange.svg)
![Pygame](https://img.shields.io/badge/Pygame-2.x-green.svg)
![A*](https://img.shields.io/badge/A*-Search-yellow.svg)
![MCTS](https://img.shields.io/badge/Monte%20Carlo-MCTS-red.svg)
![BFS](https://img.shields.io/badge/BFS-Search-blue.svg)
![DFS](https://img.shields.io/badge/DFS-Search-purple.svg)
![Python](https://img.shields.io/badge/Python-3.x-blue.svg)



Bagh Bandi is a traditional village game played in South Asia. It is an adversarial game with two sides: tigers and goats. The tigers want to kill as many goats as they can by capturing them, while the goats are trying to block the movement of tigers through strategic moves and placements.

In this project, we implement the game as a human-computer play using different **AI algorithms**. The human player controls the tiger, while the computer uses AI algorithms to control the goats. This is a type of AI adversarial game, where we use different algorithms to make strategic decisions for the goat side. The algorithms are `A*`, `Monte Carlo Tree Search`, `BFS`, `DFS`, and `Random`.

 The game features an interactive **Pygame-based graphical interface** where players manually control the tiger by clicking and moving it, while the AI algorithms autonomously manage the goat pieces' movements and placements, creating an engaging adversarial gameplay experience.


**A demo of our implemented Bagh-Bandi game using Monte-Carlo Tree Search Algorithm is shown below:**

<p align="center">
  <img src="https://github.com/fardinsaad/Bagh-Bandi-Game/raw/master/Images/MCTS_Expert.gif" width="700">
</p>


## 📋 Table of Contents


- [Game Overview](#game-overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [AI Algorithms](#ai-algorithms)
- [Project Structure](#project-structure)
- [Contributors](#contributors)

## Game Overview

### What is Bagh Bandi?

Bagh Bandi (also known as "Tiger and Goats") is a traditional two-player strategy board game originating from South Asia. The game is played on a 5×5 grid board with diagonal lines connecting certain positions.

### Game Components

- **Board**: A 5×5 grid (25 positions) with diagonal connections
- **Tiger**: 1 tiger controlled by the player
- **Goats**: 25 goats controlled by AI algorithms, placed one at a time on the board
- **Restricted Positions**: Certain positions (12 specific cells) only allow horizontal and vertical movements, not diagonal

### Objective

- **Tiger Wins**: Capture enough goats (reduce remaining goats to 5 or fewer)
- **Goats Win**: Trap the tiger so it cannot make any legal moves
- **Stalemate**: Game ends after 100 moves without a winner

### Gameplay Flow

1. **Initial Setup**: One tiger is placed on the board
2. **Goat Placement Phase**: Goats are placed one at a time on empty positions (up to 25 goats)
3. **Movement Phase**: Once goats are on the board, they can move to adjacent empty positions
4. **Tiger Moves**: Player clicks on the tiger, then clicks on a destination to move or capture
5. **Capture Mechanism**: The tiger captures goats by jumping over them (like checkers)
6. **Game End**: Continues until win condition is met or stalemate occurs

> Here is a demonstration of the Bagh Bandi game: [YouTube Video](https://www.youtube.com/watch?v=2y6AImREUbs)

## Features

- 🎨 **Interactive GUI**: Pygame-based graphical interface with real-time board visualization
- 🤖 **Multiple AI Algorithms**: Five different AI strategies for goat gameplay
- 📊 **Game Statistics**: Real-time display of remaining goats, goats on board, and move count
- 🎯 **Strategic Gameplay**: Implements game rules including restricted positions and capture mechanics
- 🔄 **Turn-based System**: Alternating turns between player (tiger) and AI (goats)



## Installation

Follow these steps to set up the project on your local machine:

### 1. Clone the Repository

```bash
git clone https://github.ncsu.edu/upaul/BaghBandi_AI.git
cd BaghBandi_AI
```

Alternatively, you can download and unzip the project file, then navigate to the project directory.

### 2. Install Dependencies

Install the required Python packages:

```bash
pip install -r requirements.txt
```

This will install `pygame` and any other dependencies.

### 3. Navigate to Source Directory

```bash
cd src
```

## Usage

### Running the Game

To start the game, use the following command from the `src` directory:

```bash
python3 main.py <algorithm_name>
```

### Valid Algorithm Names

- `bfs` - Breadth-First Search
- `dfs` - Depth-First Search
- `astar` - A* Search Algorithm
- `monte_carlo` - Monte Carlo Tree Search
- `random` - Random move selection (baseline)

### Example Commands

```bash
# Run with Monte Carlo Tree Search
python3 main.py monte_carlo

# Run with A* algorithm
python3 main.py astar

# Run with BFS
python3 main.py bfs
```

### How to Play

1. **Start the game** with your chosen algorithm
2. **Click on the tiger** to select it (the tiger will be highlighted)
3. **Click on a destination** to move the tiger:
   - **Normal Move**: Move to an adjacent empty position
   - **Capture Move**: Jump over a goat to capture it (destination must be empty)
4. After each tiger move, the AI will automatically make a goat move
5. The game continues until a win condition is met

### Game Controls

- **Mouse Click**: Select and move the tiger
- **Close Window**: Exit the game

## AI Algorithms

### 1. Breadth-First Search (BFS)
- Explores all nodes at the current depth before moving to the next level
- Guarantees finding the shortest path solution
- Uses a systematic approach to find optimal goat placements and movements

### 2. Depth-First Search (DFS)
- Explores as far as possible along each branch before backtracking
- Memory efficient but may not find optimal solutions
- Uses a different search order compared to BFS

### 3. A* Search Algorithm
- Combines the advantages of BFS and heuristic search
- Uses heuristic functions to evaluate positions:
  - **Positive heuristic (+100)**: Safe positions with no adjacent tigers
  - **Negative heuristic (-100)**: Dangerous positions where tigers can capture
- Prioritizes safe moves and avoids dangerous positions

### 4. Monte Carlo Tree Search (MCTS)
- Uses simulation-based approach with 2000 iterations
- Implements UCB1 (Upper Confidence Bound) for node selection
- Evaluates game states based on:
  - Goat safety (penalties for adjacent tigers)
  - Protection mechanisms (rewards for blocked capture paths)
  - Escape routes (rewards for safe movement options)
- Most sophisticated algorithm with strategic depth

### 5. Random Play
- Baseline algorithm that selects random legal moves
- Prioritizes safe placements over risky ones
- Useful for comparison with other algorithms

## Project Structure

```
BaghBandi_AI/
├── src/
│   ├── main.py              # Entry point, initializes game
│   ├── game.py              # Main game logic and state management
│   ├── board.py             # Board rendering and visualization
│   ├── constants.py         # Game constants and configuration
│   ├── astar.py             # A* algorithm implementation
│   ├── bfs.py               # BFS algorithm implementation
│   ├── dfs.py               # DFS algorithm implementation
│   ├── monte_carlo.py       # Monte Carlo Tree Search implementation
│   └── random_play.py       # Random play algorithm
├── requirements.txt         # Python dependencies
├── README.md                # Project documentation
└── .gitignore              # Git ignore rules
```

## Contributors

This project was developed by:

- **Uchswas Paul**
- **Fardin Saad**
- **Adittya Soukarjya Saha**
- **Vinay Vobbilichetty**

---

**Course**: CSC-520 Artificial Intelligence  
**Institution**: North Carolina State University  
**Semester**: Spring 2024

## React Tic-Tac-Toe Game

A simple, beginner-friendly Tic-Tac-Toe game built using **React**. Perfect for learning how React components, props, state, and event handling work.

## What You Will Learn

- React Functional Components

- `useState` Hook for state management

- Passing and handling props

- Lifting state up

- Conditional rendering

- Implementing "time travel" (move history)

## Prerequisites

Make sure you have the following installed:

- [Node.js](https://nodejs.org/)
- [npm](https://www.npmjs.com/)
- Code editor (like [VS Code](https://code.visualstudio.com/))

## Project Structure

```plain
my-tic-tac-toe/
│
├── public/
├── src/
│   ├── App.css       # Styling for the game
│   ├── App.jsx       # Main game logic and React components
│   └── main.jsx      # Main component where the game renders
├── index.html
├── index.css 
├── package.json
└── README.md
```

## Step-by-Step Instructions

### Step 1: Create a New React App

```bash
npm create vite@latest
```

It will ask for the prompts wherein you need to enter some configurations.

### Step 2: Run the App

```bash
cd game
npm run dev
```

Your game should open at http://localhost:3000

## Understanding the Code

### 1. Component Structure

- Square: Single cell of the board

- Board: Manages 3x3 grid and handles player turns

- Game: Root component, handles move history and "time travel"

### 2. Props and State

- props (short for properties) are how data is passed into components.

- state is used to store data that can change (e.g., whose turn it is, the board's status).   

```js
const [history, setHistory] = useState([Array(9).fill(null)]);
```

This sets the initial history of the game - an array of empty board states.

### 3. Lifting State Up

We manage the state in the Game component and pass it down to Board and Square. This helps keep a single source of truth for the board.

### 4. Handling Clicks

```js
function handleClick(i) {
  if (squares[i] || checkWinner(squares)) return;

  const newSquare = squares.slice();
  newSquare[i] = xIsNext ? "X" : "O";
  onPlay(newSquare);
}
```

This function is called when a square is clicked. It updates the board with the current player's move.

### 5. History and Time Travel

You can go back to previous moves using the history feature. Each move is stored in the history array. Buttons allow the user to jump to past states.
const emojis = ["🍎", "🍌", "🚗", "🎈", "🐶", "🐱", "🧸", "⚽", "🌟", "🍕",
                "🍓", "🥕", "🍇", "🚀", "👑", "💎", "🎁", "🦄", "🍔", "🧁",
                "🍩", "🐻", "🐸", "🐰", "🐵"];

let emojiList = [...emojis, ...emojis]; // 25 emojis × 2 = 50
emojiList.sort(() => Math.random() - 0.5); // Shuffle

const gameBoard = document.getElementById("gameBoard");
let firstCard = null;
let secondCard = null;
let lockBoard = false;
let matches = 0;

// Timer
let timeLeft = 120;
const timer = document.getElementById("time");
const interval = setInterval(() => {
  timeLeft--;
  timer.textContent = timeLeft;
  if (timeLeft === 0) {
    clearInterval(interval);
    document.getElementById("message").textContent = "⏳ Time's up! Try again.";
    lockBoard = true;
  }
}, 1000);

// Create cards
emojiList.forEach(emoji => {
  const card = document.createElement("div");
  card.classList.add("card");
  card.dataset.emoji = emoji;
  card.textContent = "❓";
  card.addEventListener("click", handleClick);
  gameBoard.appendChild(card);
});

function handleClick(e) {
  if (lockBoard) return;
  const clickedCard = e.target;
  if (clickedCard.classList.contains("revealed") || clickedCard === firstCard) return;

  clickedCard.classList.add("revealed");
  clickedCard.textContent = clickedCard.dataset.emoji;

  if (!firstCard) {
    firstCard = clickedCard;
    return;
  }

  secondCard = clickedCard;
  lockBoard = true;

  if (firstCard.dataset.emoji === secondCard.dataset.emoji) {
    matches += 1;
    firstCard.removeEventListener("click", handleClick);
    secondCard.removeEventListener("click", handleClick);
    resetTurn();

    if (matches === 25) {
      clearInterval(interval);
      document.getElementById("message").textContent = "🎉 Congratulations! You matched all!";
    }
  } else {
    setTimeout(() => {
      firstCard.classList.remove("revealed");
      secondCard.classList.remove("revealed");
      firstCard.textContent = "❓";
      secondCard.textContent = "❓";
      resetTurn();
    }, 1000);
  }
}

function resetTurn() {
  firstCard = null;
  secondCard = null;
  lockBoard = false;
}

# Gamer

`
// Get the canvas element
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');

// Set up game variables
let playerX = 50;
let playerY = 50;
let playerSpeed = 5;
let enemyX = 100;
let enemyY = 100;
let enemySpeed = 2;
let score = 0;

// Game loop
function update() {
    // Update player position
    playerX += playerSpeed;

    // Update enemy position
    enemyY += enemySpeed;

    // Collision detection
    if (playerX + 50 > enemyX && playerX - 50 < enemyX + 50 && playerY + 50 > enemyY && playerY - 50 < enemyY + 50) {
        score++;
        enemyX = Math.random() * 700;
        enemyY = 50;
    }

    // Draw everything
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = 'blue';
    ctx.fillRect(playerX, playerY, 50, 50);
    ctx.fillStyle = 'red';
    ctx.fillRect(enemyX, enemyY, 50, 50);
    ctx.font = '24px Arial';
    ctx.fillText(`Score: ${score}`, 20, 20);
}

// Update game loop
setInterval(update, 1000 / 60);

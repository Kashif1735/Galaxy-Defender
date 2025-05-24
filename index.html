<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galaxy Defender</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            overflow: hidden;
            background: #000;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            font-family: 'Arial', sans-serif;
        }
        
        #gameCanvas {
            display: block;
            background: linear-gradient(to bottom, #000428, #004e92);
            box-shadow: 0 0 20px rgba(0, 150, 255, 0.5);
            border: 2px solid #00a8ff;
        }
        
        #uiContainer {
            position: absolute;
            top: 10px;
            left: 10px;
            color: white;
            font-size: 18px;
            text-shadow: 0 0 5px #00a8ff;
        }
        
        #startScreen {
            position: absolute;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white;
            z-index: 100;
        }
        
        #gameTitle {
            font-size: 72px;
            margin-bottom: 30px;
            background: linear-gradient(to right, #00a8ff, #00ffaa);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: 0 0 10px rgba(0, 168, 255, 0.5);
            animation: pulse 2s infinite alternate;
        }
        
        @keyframes pulse {
            from { transform: scale(1); }
            to { transform: scale(1.05); }
        }
        
        .btn {
            padding: 15px 30px;
            margin: 10px;
            font-size: 20px;
            background: linear-gradient(to right, #00a8ff, #00ffaa);
            border: none;
            border-radius: 30px;
            color: white;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 0 15px rgba(0, 168, 255, 0.5);
        }
        
        .btn:hover {
            transform: scale(1.1);
            box-shadow: 0 0 20px rgba(0, 168, 255, 0.8);
        }
        
        #gameOverScreen {
            position: absolute;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            display: none;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white;
            z-index: 100;
        }
        
        #scoreDisplay {
            font-size: 36px;
            margin: 20px 0;
            color: #00ffaa;
        }
    </style>
</head>
<body>
    <div id="uiContainer">
        <div>Score: <span id="score">0</span></div>
        <div>Lives: <span id="lives">3</span></div>
        <div>Level: <span id="level">1</span></div>
    </div>
    
    <canvas id="gameCanvas" width="800" height="600"></canvas>
    
    <div id="startScreen">
        <h1 id="gameTitle">GALAXY DEFENDER</h1>
        <button class="btn" id="startBtn">START GAME</button>
        <button class="btn" id="instructionsBtn">INSTRUCTIONS</button>
    </div>
    
    <div id="gameOverScreen">
        <h1>GAME OVER</h1>
        <div id="finalScore">Score: 0</div>
        <button class="btn" id="restartBtn">PLAY AGAIN</button>
    </div>

    <script>
        // Game Canvas Setup
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        
        // UI Elements
        const scoreElement = document.getElementById('score');
        const livesElement = document.getElementById('lives');
        const levelElement = document.getElementById('level');
        const startScreen = document.getElementById('startScreen');
        const gameOverScreen = document.getElementById('gameOverScreen');
        const finalScoreElement = document.getElementById('finalScore');
        const startBtn = document.getElementById('startBtn');
        const restartBtn = document.getElementById('restartBtn');
        const instructionsBtn = document.getElementById('instructionsBtn');
        
        // Game State
        let gameRunning = false;
        let score = 0;
        let lives = 3;
        let level = 1;
        let enemies = [];
        let bullets = [];
        let particles = [];
        let powerUps = [];
        let lastEnemySpawn = 0;
        let enemySpawnRate = 2000;
        let keys = {};
        
        // Player Object
        const player = {
            x: canvas.width / 2,
            y: canvas.height - 60,
            width: 50,
            height: 50,
            speed: 8,
            color: '#00a8ff',
            lastShot: 0,
            shootDelay: 300,
            isInvulnerable: false,
            invulnerableTimer: 0,
            
            draw() {
                ctx.save();
                
                // Glow effect
                const glowGradient = ctx.createRadialGradient(
                    this.x, this.y, 5,
                    this.x, this.y, 30
                );
                glowGradient.addColorStop(0, this.color);
                glowGradient.addColorStop(1, 'rgba(0, 168, 255, 0)');
                
                ctx.fillStyle = glowGradient;
                ctx.beginPath();
                ctx.arc(this.x, this.y, 30, 0, Math.PI * 2);
                ctx.fill();
                
                // Player ship
                ctx.fillStyle = this.color;
                ctx.beginPath();
                ctx.moveTo(this.x, this.y - 20);
                ctx.lineTo(this.x - 15, this.y + 15);
                ctx.lineTo(this.x + 15, this.y + 15);
                ctx.closePath();
                ctx.fill();
                
                // Engine glow
                if (keys.ArrowUp || keys.w) {
                    const engineGradient = ctx.createLinearGradient(
                        this.x - 10, this.y + 15,
                        this.x + 10, this.y + 15
                    );
                    engineGradient.addColorStop(0, '#ff0000');
                    engineGradient.addColorStop(0.5, '#ff7700');
                    engineGradient.addColorStop(1, '#ff0000');
                    
                    ctx.fillStyle = engineGradient;
                    ctx.beginPath();
                    ctx.moveTo(this.x - 10, this.y + 15);
                    ctx.lineTo(this.x, this.y + 30);
                    ctx.lineTo(this.x + 10, this.y + 15);
                    ctx.closePath();
                    ctx.fill();
                }
                
                // Invulnerability effect
                if (this.isInvulnerable) {
                    ctx.strokeStyle = 'rgba(255, 255, 255, 0.7)';
                    ctx.lineWidth = 2;
                    ctx.beginPath();
                    ctx.arc(this.x, this.y, 30, 0, Math.PI * 2);
                    ctx.stroke();
                }
                
                ctx.restore();
            },
            
            update() {
                // Movement
                if (keys.ArrowLeft || keys.a) this.x -= this.speed;
                if (keys.ArrowRight || keys.d) this.x += this.speed;
                if (keys.ArrowUp || keys.w) this.y -= this.speed;
                if (keys.ArrowDown || keys.s) this.y += this.speed;
                
                // Boundary checking
                this.x = Math.max(this.width / 2, Math.min(canvas.width - this.width / 2, this.x));
                this.y = Math.max(this.height / 2, Math.min(canvas.height - this.height / 2, this.y));
                
                // Shooting
                if ((keys[' '] || keys.z) && Date.now() - this.lastShot > this.shootDelay) {
                    this.shoot();
                    this.lastShot = Date.now();
                }
                
                // Invulnerability timer
                if (this.isInvulnerable && Date.now() - this.invulnerableTimer > 2000) {
                    this.isInvulnerable = false;
                }
            },
            
            shoot() {
                bullets.push({
                    x: this.x,
                    y: this.y - 25,
                    width: 5,
                    height: 15,
                    speed: 10,
                    color: '#00ffaa'
                });
            },
            
            takeDamage() {
                if (this.isInvulnerable) return;
                
                lives--;
                livesElement.textContent = lives;
                
                if (lives <= 0) {
                    gameOver();
                } else {
                    this.isInvulnerable = true;
                    this.invulnerableTimer = Date.now();
                    
                    // Create explosion particles
                    createExplosion(this.x, this.y, 20, '#00a8ff');
                }
            }
        };
        
        // Enemy shooting function
        function enemyShoot(enemy) {
            bullets.push({
                x: enemy.x,
                y: enemy.y + enemy.height / 2,
                width: 5,
                height: 15,
                speed: -5,
                color: '#ff5555'
            });
        }
        
        // Initialize game
        function initGame() {
            gameRunning = true;
            score = 0;
            lives = 3;
            level = 1;
            enemies = [];
            bullets = [];
            particles = [];
            powerUps = [];
            
            scoreElement.textContent = score;
            livesElement.textContent = lives;
            levelElement.textContent = level;
            
            player.x = canvas.width / 2;
            player.y = canvas.height - 60;
            player.isInvulnerable = true;
            player.invulnerableTimer = Date.now();
            
            startScreen.style.display = 'none';
            gameOverScreen.style.display = 'none';
            
            // Start game loop
            gameLoop();
        }
        
        // Game loop
        function gameLoop() {
            if (!gameRunning) return;
            
            // Clear canvas
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            // Draw starfield background
            drawStarfield();
            
            // Spawn enemies
            const now = Date.now();
            if (now - lastEnemySpawn > enemySpawnRate) {
                spawnEnemy();
                lastEnemySpawn = now;
                
                // Increase difficulty
                if (score > 0 && score % 1000 === 0) {
                    level++;
                    levelElement.textContent = level;
                    enemySpawnRate = Math.max(500, enemySpawnRate - 200);
                }
            }
            
            // Update and draw player
            player.update();
            player.draw();
            
            // Update and draw bullets
            updateBullets();
            
            // Update and draw enemies
            updateEnemies();
            
            // Update and draw particles
            updateParticles();
            
            // Update and draw power-ups
            updatePowerUps();
            
            // Check collisions
            checkCollisions();
            
            // Continue game loop
            requestAnimationFrame(gameLoop);
        }
        
        // Draw starfield background
        function drawStarfield() {
            ctx.fillStyle = 'white';
            
            // Static stars
            for (let i = 0; i < 100; i++) {
                const x = Math.sin(i * 100) * canvas.width / 2 + canvas.width / 2;
                const y = i * canvas.height / 100;
                const size = Math.random() * 1.5;
                
                ctx.globalAlpha = Math.random() * 0.8 + 0.2;
                ctx.beginPath();
                ctx.arc(x, y, size, 0, Math.PI * 2);
                ctx.fill();
            }
            
            // Moving stars
            ctx.globalAlpha = 1;
            for (let i = 0; i < level * 5; i++) {
                const x = Math.random() * canvas.width;
                const y = (Date.now() / 10 + i * 100) % canvas.height;
                const size = Math.random() * 2;
                
                ctx.beginPath();
                ctx.arc(x, y, size, 0, Math.PI * 2);
                ctx.fill();
            }
            
            // Nebula effect
            const nebula = ctx.createRadialGradient(
                canvas.width / 2, canvas.height / 2, 0,
                canvas.width / 2, canvas.height / 2, canvas.width
            );
            nebula.addColorStop(0, 'rgba(0, 40, 100, 0.1)');
            nebula.addColorStop(1, 'rgba(0, 10, 30, 0.3)');
            
            ctx.fillStyle = nebula;
            ctx.fillRect(0, 0, canvas.width, canvas.height);
        }
        
        // Spawn enemy
        function spawnEnemy() {
            const size = 30 + Math.random() * 20;
            const type = Math.random() > 0.8 ? 'elite' : 'normal';
            
            enemies.push({
                x: Math.random() * (canvas.width - size) + size / 2,
                y: -size,
                width: size,
                height: size,
                speed: 1 + Math.random() * level / 2,
                color: type === 'elite' ? '#ff5555' : '#ffaa00',
                health: type === 'elite' ? 3 : 1,
                type: type,
                value: type === 'elite' ? 200 : 100,
                lastShot: 0,
                shootDelay: type === 'elite' ? 1500 : 3000,
                shoot: function() {
                    enemyShoot(this);
                }
            });
        }
        
        // Update bullets
        function updateBullets() {
            for (let i = bullets.length - 1; i >= 0; i--) {
                const bullet = bullets[i];
                bullet.y -= bullet.speed;
                
                // Draw bullet with glow
                ctx.save();
                const bulletGradient = ctx.createRadialGradient(
                    bullet.x, bullet.y, 0,
                    bullet.x, bullet.y, 10
                );
                bulletGradient.addColorStop(0, bullet.color);
                bulletGradient.addColorStop(1, 'rgba(0, 255, 170, 0)');
                
                ctx.fillStyle = bulletGradient;
                ctx.fillRect(bullet.x - bullet.width / 2, bullet.y - bullet.height, bullet.width, bullet.height);
                ctx.restore();
                
                // Remove bullets that are off screen
                if (bullet.y < 0) {
                    bullets.splice(i, 1);
                }
            }
        }
        
        // Update enemies
        function updateEnemies() {
            for (let i = enemies.length - 1; i >= 0; i--) {
                const enemy = enemies[i];
                enemy.y += enemy.speed;
                
                // Draw enemy
                ctx.save();
                
                // Enemy glow
                const enemyGlow = ctx.createRadialGradient(
                    enemy.x, enemy.y, enemy.width / 4,
                    enemy.x, enemy.y, enemy.width
                );
                enemyGlow.addColorStop(0, enemy.color);
                enemyGlow.addColorStop(1, 'rgba(255, 170, 0, 0)');
                
                ctx.fillStyle = enemyGlow;
                ctx.beginPath();
                ctx.arc(enemy.x, enemy.y, enemy.width, 0, Math.PI * 2);
                ctx.fill();
                
                // Enemy ship
                ctx.fillStyle = enemy.color;
                ctx.beginPath();
                ctx.moveTo(enemy.x, enemy.y + enemy.width / 2);
                ctx.lineTo(enemy.x - enemy.width / 2, enemy.y - enemy.width / 3);
                ctx.lineTo(enemy.x + enemy.width / 2, enemy.y - enemy.width / 3);
                ctx.closePath();
                ctx.fill();
                
                // Elite enemies have a different shape
                if (enemy.type === 'elite') {
                    ctx.fillStyle = '#ff0000';
                    ctx.beginPath();
                    ctx.arc(enemy.x, enemy.y, enemy.width / 3, 0, Math.PI * 2);
                    ctx.fill();
                }
                
                ctx.restore();
                
                // Enemy shooting
                if (Date.now() - enemy.lastShot > enemy.shootDelay && Math.random() > 0.95) {
                    enemy.shoot();
                    enemy.lastShot = Date.now();
                }
                
                // Remove enemies that are off screen
                if (enemy.y > canvas.height + enemy.height) {
                    enemies.splice(i, 1);
                }
            }
        }
        
        // Update particles
        function updateParticles() {
            for (let i = particles.length - 1; i >= 0; i--) {
                const p = particles[i];
                p.x += p.vx;
                p.y += p.vy;
                p.alpha -= 0.01;
                
                ctx.globalAlpha = p.alpha;
                ctx.fillStyle = p.color;
                ctx.beginPath();
                ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                ctx.fill();
                
                if (p.alpha <= 0) {
                    particles.splice(i, 1);
                }
            }
            ctx.globalAlpha = 1;
        }
        
        // Update power-ups
        function updatePowerUps() {
            for (let i = powerUps.length - 1; i >= 0; i--) {
                const p = powerUps[i];
                p.y += p.speed;
                
                ctx.save();
                
                // Power-up glow
                const glow = ctx.createRadialGradient(
                    p.x, p.y, 5,
                    p.x, p.y, 20
                );
                glow.addColorStop(0, p.color);
                glow.addColorStop(1, 'rgba(0, 255, 170, 0)');
                
                ctx.fillStyle = glow;
                ctx.beginPath();
                ctx.arc(p.x, p.y, 20, 0, Math.PI * 2);
                ctx.fill();
                
                // Power-up icon
                ctx.fillStyle = 'white';
                ctx.font = '20px Arial';
                ctx.textAlign = 'center';
                ctx.textBaseline = 'middle';
                ctx.fillText(p.type === 'extraLife' ? '♥' : '⚡', p.x, p.y);
                
                ctx.restore();
                
                // Remove power-ups that are off screen
                if (p.y > canvas.height + 30) {
                    powerUps.splice(i, 1);
                }
            }
        }
        
        // Check collisions
        function checkCollisions() {
            // Bullet-enemy collisions
            for (let i = bullets.length - 1; i >= 0; i--) {
                const bullet = bullets[i];
                
                for (let j = enemies.length - 1; j >= 0; j--) {
                    const enemy = enemies[j];
                    
                    if (bullet.speed > 0 && // Player bullets
                        bullet.x > enemy.x - enemy.width / 2 &&
                        bullet.x < enemy.x + enemy.width / 2 &&
                        bullet.y > enemy.y - enemy.height / 2 &&
                        bullet.y < enemy.y + enemy.height / 2) {
                        
                        // Hit enemy
                        enemy.health--;
                        
                        // Create hit effect
                        createExplosion(bullet.x, bullet.y, 10, enemy.color);
                        
                        // Remove bullet
                        bullets.splice(i, 1);
                        
                        // Check if enemy is destroyed
                        if (enemy.health <= 0) {
                            // Add score
                            score += enemy.value;
                            scoreElement.textContent = score;
                            
                            // Create explosion
                            createExplosion(enemy.x, enemy.y, enemy.width, enemy.color);
                            
                            // Chance to spawn power-up
                            if (Math.random() > 0.7) {
                                spawnPowerUp(enemy.x, enemy.y);
                            }
                            
                            // Remove enemy
                            enemies.splice(j, 1);
                        }
                        
                        break;
                    }
                }
            }
            
            // Player-enemy collisions
            if (!player.isInvulnerable) {
                for (let i = enemies.length - 1; i >= 0; i--) {
                    const enemy = enemies[i];
                    
                    const dx = player.x - enemy.x;
                    const dy = player.y - enemy.y;
                    const distance = Math.sqrt(dx * dx + dy * dy);
                    
                    if (distance < (player.width / 2 + enemy.width / 2)) {
                        // Player takes damage
                        player.takeDamage();
                        
                        // Create explosion
                        createExplosion(enemy.x, enemy.y, enemy.width, enemy.color);
                        
                        // Remove enemy
                        enemies.splice(i, 1);
                        
                        break;
                    }
                }
            }
            
            // Player-bullet collisions
            if (!player.isInvulnerable) {
                for (let i = bullets.length - 1; i >= 0; i--) {
                    const bullet = bullets[i];
                    
                    if (bullet.speed < 0 && // Enemy bullets
                        bullet.x > player.x - player.width / 2 &&
                        bullet.x < player.x + player.width / 2 &&
                        bullet.y > player.y - player.height / 2 &&
                        bullet.y < player.y + player.height / 2) {
                        
                        // Player takes damage
                        player.takeDamage();
                        
                        // Create hit effect
                        createExplosion(bullet.x, bullet.y, 10, bullet.color);
                        
                        // Remove bullet
                        bullets.splice(i, 1);
                        
                        break;
                    }
                }
            }
            
            // Player-power-up collisions
            for (let i = powerUps.length - 1; i >= 0; i--) {
                const p = powerUps[i];
                
                const dx = player.x - p.x;
                const dy = player.y - p.y;
                const distance = Math.sqrt(dx * dx + dy * dy);
                
                if (distance < (player.width / 2 + 20)) {
                    // Apply power-up
                    if (p.type === 'extraLife') {
                        lives++;
                        livesElement.textContent = lives;
                    } else if (p.type === 'rapidFire') {
                        player.shootDelay = Math.max(100, player.shootDelay - 100);
                    }
                    
                    // Create collection effect
                    createExplosion(p.x, p.y, 20, p.color);
                    
                    // Remove power-up
                    powerUps.splice(i, 1);
                }
            }
        }
        
        // Create explosion particles
        function createExplosion(x, y, size, color) {
            const particleCount = size * 2;
            
            for (let i = 0; i < particleCount; i++) {
                particles.push({
                    x: x,
                    y: y,
                    size: Math.random() * 3 + 1,
                    vx: Math.random() * 6 - 3,
                    vy: Math.random() * 6 - 3,
                    color: color,
                    alpha: 1
                });
            }
        }
        
        // Spawn power-up
        function spawnPowerUp(x, y) {
            const types = ['extraLife', 'rapidFire'];
            const type = types[Math.floor(Math.random() * types.length)];
            
            powerUps.push({
                x: x,
                y: y,
                speed: 2,
                type: type,
                color: type === 'extraLife' ? '#ff5555' : '#00ffaa'
            });
        }
        
        // Game over
        function gameOver() {
            gameRunning = false;
            finalScoreElement.textContent = `Score: ${score}`;
            gameOverScreen.style.display = 'flex';
        }
        
        // Event listeners
        window.addEventListener('keydown', (e) => {
            keys[e.key] = true;
            keys[e.code] = true;
        });
        
        window.addEventListener('keyup', (e) => {
            keys[e.key] = false;
            keys[e.code] = false;
        });
        
        startBtn.addEventListener('click', initGame);
        restartBtn.addEventListener('click', initGame);
        instructionsBtn.addEventListener('click', () => {
            alert("Controls:\n\nArrow Keys or WASD: Move\nSpace or Z: Shoot\n\nDestroy enemies to score points. Collect power-ups for bonuses. Survive as long as possible!");
        });
    </script>
</body>
</html>

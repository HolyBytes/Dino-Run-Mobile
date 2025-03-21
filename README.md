## **Dino Run Mobile** 🦖🔥  

**Dino Run Mobile** adalah game endless runner di mana kamu mengontrol seekor dinosaurus kecil yang harus melompati rintangan dan bertahan selama mungkin. Game ini terinspirasi dari **dino game di Google Chrome**, tapi dengan tampilan lebih keren, fitur tambahan, dan efek visual yang lebih hidup.  

Game ini bisa dimainkan **di HP maupun PC**, dengan kontrol yang mudah dan gameplay yang semakin cepat seiring bertambahnya skor.  

---

## **Cara Main** 🎮  

1️⃣ **Lompat Hindari Rintangan**  
   - **Di HP:** Tekan tombol **"LOMPAT"** atau tap layar.  
   - **Di PC:** Tekan **spasi** untuk melompat.  

2️⃣ **Game Over**  
   - Kalau dino menabrak rintangan, game berakhir.  
   - Skor akhir akan muncul di layar.  

3️⃣ **Restart Game**  
   - **Di HP:** Tekan tombol **"RESTART"**.  
   - **Di PC:** Tekan **R** untuk mulai lagi.  

4️⃣ **Mode Malam**  
   - Tekan **ikon bulan 🌙** di kiri atas buat ganti ke mode malam.  
   - Tekan lagi buat kembali ke mode siang.  

---

## **Fitur Menarik** 🌟  
✅ **Grafik Berwarna-warni** – Latar belakang gradasi yang bikin lebih menarik.  
✅ **Mode Siang & Malam** – Ganti tampilan sesuai mood kamu.  
✅ **Awan Bergerak** – Efek awan yang berjalan otomatis.  
✅ **Makin Lama, Makin Cepat** – Game jadi semakin menantang.  
✅ **Bisa Dimainkan di Mobile & PC** – Kontrol responsif di semua perangkat.  

---

## **Fungsi-Fungsi di Dalam Game** 🛠️  

### **1. Fungsi Melompat (jump)**  
🡆 Bikin dino melompat untuk menghindari rintangan.  

```js
function jump() {
    if (isJumping || gameOver) return;
    isJumping = true;
    dino.classList.add('jump');
    
    setTimeout(() => {
        dino.classList.remove('jump');
        isJumping = false;
    }, 800);
}
```

---

### **2. Fungsi Membuat Rintangan (createObstacle)**  
🡆 Rintangan muncul secara otomatis dan bergerak ke kiri.  

```js
function createObstacle() {
    const obstacle = document.createElement('div');
    obstacle.classList.add('obstacle');
    gameContainer.appendChild(obstacle);
    let obstaclePosition = gameContainer.clientWidth;

    const moveObstacle = setInterval(() => {
        if (gameOver) {
            clearInterval(moveObstacle);
            return;
        }

        obstaclePosition -= gameSpeed;
        obstacle.style.left = obstaclePosition + 'px';

        // Deteksi tabrakan
        const dinoRect = dino.getBoundingClientRect();
        const obstacleRect = obstacle.getBoundingClientRect();

        if (dinoRect.right > obstacleRect.left &&
            dinoRect.left < obstacleRect.right &&
            dinoRect.bottom > obstacleRect.top) {
            endGame();
        }
    }, 20);
}
```

---

### **3. Fungsi Mode Malam (Day/Night Toggle)**  
🡆 Mengubah tampilan game ke mode malam atau kembali ke mode siang.  

```js
dayNightToggle.addEventListener('click', () => {
    isNightMode = !isNightMode;
    document.body.classList.toggle('night-mode');
    toggleIcon.className = isNightMode ? 'fas fa-sun' : 'fas fa-moon';
});
```

---

### **4. Fungsi Skor (startScoring)**  
🡆 Menambah skor pemain dan meningkatkan kecepatan game setiap 100 poin.  

```js
function startScoring() {
    scoreInterval = setInterval(() => {
        if (!gameOver) {
            score++;
            scoreDisplay.innerText = `Score: ${score}`;

            if (score % 100 === 0 && gameSpeed < 12) {
                gameSpeed += 0.5;
            }
        }
    }, 200);
}
```

---

### **5. Fungsi Game Over (endGame)**  
🡆 Menghentikan game saat dino menabrak rintangan.  

```js
function endGame() {
    gameOver = true;
    gameOverText.style.display = 'block';
    finalScoreDisplay.innerText = `Score: ${score}`;
    clearInterval(obstacleInterval);
    clearInterval(scoreInterval);
    dino.style.animation = 'shake 0.5s';
}
```

---

### **6. Fungsi Restart Game (restartGame)**  
🡆 Memulai ulang game setelah game over.  

```js
function restartGame() {
    gameOver = false;
    score = 0;
    gameSpeed = 5;
    scoreDisplay.innerText = 'Score: 0';
    gameOverText.style.display = 'none';

    gameContainer.querySelectorAll('.obstacle').forEach((obstacle) => obstacle.remove());
    dino.style.animation = '';
    clearInterval(obstacleInterval);
    clearInterval(scoreInterval);
    startObstacles();
    startScoring();
}
```

---

### **7. Fungsi Keyboard Control (PC Only)**  
🡆 Kontrol dino dengan tombol di keyboard.  

```js
document.addEventListener('keydown', (e) => {
    if (e.code === 'Space') jump();
    if (e.code === 'KeyR' && gameOver) restartGame();
});
```

---

## **Tips Supaya Skor Tinggi** 💡  
🔥 **Perhatikan Pola Rintangan** – Jangan asal lompat, tunggu timing yang pas.  
🔥 **Mode Malam = Fokus Lebih Baik** – Kalau terlalu terang, ganti ke mode malam.  
🔥 **Sabar & Konsisten** – Jangan buru-buru lompat kalau nggak perlu.  

---

## **Kesimpulan** 🎯  
💯 **Dino Run Mobile** adalah game ringan yang seru dimainkan di HP maupun PC.  
💯 Cocok buat ngisi waktu luang sambil ngejar skor tertinggi.  
💯 Dengan fitur **mode malam, rintangan otomatis, dan gameplay yang semakin cepat**, game ini bakal bikin kamu ketagihan!  

Ayo coba mainkan **Dino Run Mobile** sekarang dan pecahkan rekor tertinggi kamu! 🚀🦖

<h1 class="text">Hi, I am a Front-end Developer</h1>

<div class="ball"></div>
<div class="ball"></div>
<div class="ball"></div>
<div class="ball"></div>
<div class="ball"></div>

<style>
  .text {
    font-family: Montserrat, sans-serif;
    font-size: 20px;
    font-weight: 700;
    line-height: 20px;
    color: #fff;
    text-shadow: 0 0 3px #000, 0 0 5px #000;
    position: relative;
    z-index: 2;
}

.ball {
    width: 50px;
    height: 50px;
    background-color: red;
    border-radius: 10px;
    position: absolute;
    transition: background-color 0.5s, border-radius 0.5s;
}
</style>

<script>
  const balls = document.getElementsByClassName('ball');
const ballSize = 50; // розмір кулі
const speed = 1; // базова швидкість

for (let i = 0; i < balls.length; i++) {
   const ball = balls[i];
   let x = Math.random() * (window.innerWidth - ballSize);
   let y = Math.random() * (window.innerHeight - ballSize);
   let dx = (Math.random() < 0.5 ? -1 : 1) * speed; // випадковий напрямок по x
   let dy = (Math.random() < 0.5 ? -1 : 1) * speed; // випадковий напрямок по y

   function getRandomColor() {
      const letters = '0123456789ABCDEF';
      let color = '#';
      for (let j = 0; j < 6; j++) {
         color += letters[Math.floor(Math.random() * 16)];
      }
      return color;
   }

   function getRandomInt(min, max) {
   return Math.floor(Math.random() * (100 - 30 + 1)) + 30;
}

function getRandomShape() {
   return `${getRandomInt()}% ${getRandomInt()}% ${getRandomInt()}% ${getRandomInt()}% / ${getRandomInt()}% ${getRandomInt()}% ${getRandomInt()}% ${getRandomInt()}%`;
}

   function moveBall() {
      x += dx;
      y += dy;

      // Відбивання від стінок
      if (x <= 0 || x >= window.innerWidth - ballSize) {
         dx = -dx;
      }
      if (y <= 0 || y >= window.innerHeight - ballSize) {
         dy = -dy;
      }

      ball.style.left = x + 'px';
      ball.style.top = y + 'px';

      requestAnimationFrame(moveBall);
   }

   moveBall();
   setInterval(()=>{ball.style.backgroundColor = getRandomColor()}, 1000);
setInterval(()=>{ball.style.borderRadius = getRandomShape()}, 1000);
}
</script>

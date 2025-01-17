document.addEventListener('DOMContentLoaded',() => {
createSunBall();
createH2OBall();

const rootStyles = getComputedStyle(document.documentElement);
const duration = parseFloat(rootStyles.getPropertyValue('--duration')) \* 1000;
const intervalTime = Math.round(duration / 7);

setInterval(createSunBall,intervalTime);
setInterval(createH2OBall,intervalTime);
});

// SUN BALLS ANIMATION
const ballTemplate = `

  <div class="sun-ball absolute top-1/2 translate-y-[-10%] size-2 sm:size-4 rounded-full bg-orange-400 blur-[0.1px]">
    <div class="absolute top-[30%] z-1 left-0 bg-yellow-400 blur-[0.5px] rounded-full size-[50%]"></div>
  </div>
`;
function createSunBall () {
  const container = document.getElementById('sun-ball-container');
  container.insertAdjacentHTML('beforeend',ballTemplate);
  const ball = container.lastElementChild;
  ball.addEventListener('animationend',() => ball.remove());
}

function createH2OBall () {
const ball = document.createElement('div');
ball.className = 'BLUE_H2O_BALL moveBlueH2OBalls';
ball.innerHTML = `        <div class="border rounded-full p-[80%] bg-indigo-500 text-white size-[225%] flex items-center justify-center aspect-square">O</div>
        <div class="absolute top-[75%] left-[-75%] bg-red-500 border text-white w-[125%] aspect-square rounded-full flex items-center justify-center text-[8px]">H</div>
        <div class="absolute top-[75%] right-[-200%] bg-red-500 border text-white w-[125%] aspect-square rounded-full flex items-center justify-center text-[8px]">H</div>
   `;
ball.addEventListener('animationend',() => {
ball.remove();
});
const h2oLabel = document.querySelector('.BLUE_H2O_BALLS_ANIMATIONS');
h2oLabel.appendChild(ball);
}

<script>
	import src from '/static/images/gear.svg';

  let inputIsActive = true;
  let timerStarted = true;

  let totalTime = undefined;
  let timeInMinutes = '15';
  let timeInSeconds = '00';

  let buttonValue = 'start';

  let timer;

  const toggleInput = () => {
    inputIsActive = !inputIsActive;
  }

  const toggleTimer = () => {
    timerStarted = !timerStarted;

    if(timerStarted) {

      buttonValue = 'stop';

      //Calc the time in seconds
      totalTime = parseInt(timeInMinutes) * 60 + parseInt(timeInSeconds);

      //1sec timer
      timer = setInterval(() => {
        totalTime--;
        timeInMinutes = zeroFill(Math.floor(totalTime / 60));
        timeInSeconds = zeroFill(totalTime % 60);

        if(totalTime == 0) {
          clearInterval(timer);
          alert('Time is up');
          return;
        }
      }, 1000);
    }
    else {
      buttonValue = 'start';
      clearInterval(timer);
    }

  }

  const zeroFill = (number) => {
    let str = number.toString();
    console.log(number);
    return str.length < 2 ? "0" + number.toString() : number.toString();
  }

</script>

<!-- HTML -->
<svelte:head>
  <title>AoJS - Pomodoro</title>
</svelte:head>
<div class="wrapper">
  <div class={totalTime == 0 ? 'ring ending' : 'ring'}>
    <svg width="518" height="518" viewBox="0 0 518 518">
      <circle stroke-width="9px" x="0" y="y" cx="259" cy="259" r="254" />
    </svg>
  </div>

  <div class="timer">
    <div class="time">
      <div class="minutes">
        <input bind:value="{timeInMinutes}" type="text"  disabled={inputIsActive} />
      </div>
      <div class="colon">:</div>
      <div class="seconds">
        <input bind:value="{timeInSeconds}" type="text" disabled={inputIsActive} />
      </div>
    </div>
    <button class="start" on:click="{toggleTimer}">{buttonValue}</button>
    <button class="settings" on:click="{toggleInput}">
      <img src={src} alt="Settings" />
    </button>
  </div>
</div>

<!-- CSS -->
<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@700&display=swap');

@font-face {
  font-family: "bebas";
  src: url('/static/fonts/bebasneue-book-webfont.woff') format('woff'),
       url('/static/fonts/bebasneue-book-webfont.woff2') format('woff2');
}

:global(body) {
  align-items: center;
  background: #2B2A30;
  display: flex;
  justify-content: center;
  margin: 0;
  min-height: 100vh;
  min-width: 100vw;
  padding: 0;
}

/* outer glow */
.wrapper {
  align-items: center;
  border-radius: 50%;
  box-shadow: -5px 14px 44px #000000, 5px -16px 50px rgba(255, 255, 255, 0.15);
  display: flex;
  height: 518px;
  justify-content: center;
  position: relative;
  width: 518px;
}

.ring {
  position: absolute;
  left: 0;
  stroke: #09A65A;
  top: 0;
  z-index: 1;
}

.ring.ending circle {
  stroke: #900A0A;
}

/* inner circle */
.timer {
  align-items: center;
  background: radial-gradient(71.4% 71.4% at 51.7% 28.6%, #3A393F 0%, #17171A 100%);
  border-radius: 50%;
  box-shadow: inset 0px 0px 114px rgba(0, 0, 0, 0.45);
  color: white;
  display: flex;
  flex-direction: column;
  height: 500px;
  justify-content: center;
  position: relative;
  width: 500px;
  z-index: 2;
}

/* actual time */
.time {
  display: flex;
  font-family: "bebas";
  font-size: 196px;
  margin: 30px auto;
  position: relative;
  top: 30px;
}

input[type="text"] {
  border: 0;
  border-bottom: 1px dashed white;
  background: none;
  color: white;
  font-family: "bebas";
  font-size: 196px;
  height: 170px;
  width: 150px;
  text-align: center;
  outline: none;
}

input[type=text]:disabled {
  border-bottom: none;
}

.start {
  cursor: pointer;
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  letter-spacing: 10px;
  line-height: 20px;
  background: none;
  color: white;
  opacity: .5;
  border: none;
  text-transform: uppercase;
  margin-bottom: 20px;
}

.start:hover {
  opacity: 1;
}

.settings {
  border: none;
  background: none;
  cursor: pointer;
  opacity: 0.3;
}

.settings:hover {
  opacity: 1;
}
</style>
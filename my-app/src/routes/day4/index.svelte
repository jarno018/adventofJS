<script>
  import {onMount} from 'svelte';

  let targetKey;

  let allKeys;


  onMount(() => {
    targetKey = document.querySelector('.jiggle');

    allKeys = document.querySelectorAll('.key');

    document.addEventListener('keyup', (e) => {
      let pressedKey = e.key.toUpperCase();

      if(targetKey.getAttribute('data-key') === pressedKey) {
          //@ts-ignore
          targetKey.classList.remove('jiggle');

          let rand = Math.round(Math.random() * (allKeys.length - 1));

          allKeys[rand].classList.add('jiggle');
          targetKey = allKeys[rand];
      }
    });
  })


</script>

<svelte:head>
  <title>AoJS - Keyboard</title>
</svelte:head>
<div class="keyboard">
  <h1>Eyes on the Screen</h1>
  <div class="row">
    <button class="key" data-key="`">`</button>
    <button class="key" data-key="1">1</button>
    <button class="key" data-key="2">2</button>
    <button class="key" data-key="3">3</button>
    <button class="key" data-key="4">4</button>
    <button class="key" data-key="5">5</button>
    <button class="key" data-key="6">6</button>
    <button class="key" data-key="7">7</button>
    <button class="key" data-key="8">8</button>
    <button class="key" data-key="9">9</button>
    <button class="key" data-key="0">0</button>
    <button class="key" data-key="-">-</button>
    <button class="key" data-key="=">=</button>
    <button class="key" data-key="BACKSPACE">DEL</button>
  </div>
  <div class="row">
    <button class="key utility" data-key="TAB">Tab</button>
    <button class="key" data-key="Q">Q</button>
    <button class="key" data-key="W">W</button>
    <button class="key" data-key="E">E</button>
    <button class="key jiggle" data-key="R">R</button>
    <button class="key" data-key="T">T</button>
    <button class="key" data-key="Y">Y</button>
    <button class="key" data-key="U">U</button>
    <button class="key" data-key="I">I</button>
    <button class="key" data-key="O">O</button>
    <button class="key" data-key="P">P</button>
    <button class="key" data-key="[">[</button>
    <button class="key" data-key="]">]</button>
    <button class="key" data-key="\">\</button>
  </div>
  <div class="row">
    <button class="key utility" data-key="CAPSLOCK">CAPS</button>
    <button class="key" data-key="A">A</button>
    <button class="key" data-key="S">S</button>
    <button class="key" data-key="D">D</button>
    <button class="key" data-key="F">F</button>
    <button class="key" data-key="G">G</button>
    <button class="key" data-key="H">H</button>
    <button class="key" data-key="J">J</button>
    <button class="key" data-key="K">K</button>
    <button class="key" data-key="L">L</button>
    <button class="key" data-key=";">;</button>
    <button class="key" data-key="'">'</button>
    <button class="key utility" data-key="ENTER">ENTER</button>
  </div>
  <div class="row">
    <button class="key utility" data-key="SHIFT">SHIFT</button>
    <button class="key" data-key="Z">Z</button>
    <button class="key" data-key="X">X</button>
    <button class="key" data-key="C">C</button>
    <button class="key" data-key="V">V</button>
    <button class="key" data-key="B">B</button>
    <button class="key" data-key="N">N</button>
    <button class="key" data-key="M">M</button>
    <button class="key" data-key=",">,</button>
    <button class="key" data-key=".">.</button>
    <button class="key" data-key="/">/</button>
    <button class="key utility" data-key="SHIFT">SHIFT</button>
  </div>
</div>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@700&display=swap');

  :global(body) {
    align-items: center;
    display: flex;
    justify-content: center;
    min-height: 100vh;
    min-width: 100vw;
    margin: 0;
    padding: 0;
  }

  .keyboard {
    background: #F6F6F6;
    padding: 45px 50px;
    border-radius: 50px;
    position: relative;
  }

  h1 {
    color: #60C1B6;
    font-family: 'Inter', sans-serif;
    text-transform: uppercase;
    letter-spacing: 3px;
    font-weight: bold;
    font-size: .75rem;
    text-align: center;
    position: absolute;
    top: -50px;
    left: 50%;
    width: 100vw;
    transform: translateX(-50%);
  }

  .row {
    display: flex;
    justify-content: space-between;
    gap: 12px;
    margin-bottom: 12px;
    width: 1110px;
  }

  .key {
    background: #FFFFFF;
    box-shadow: 0px 1px 8px rgba(0, 0, 0, 0.05);
    border: none;
    border-radius: 16px;
    color: #60C1B6;
    cursor: pointer;
    display: flex;
    font-family: 'Inter', sans-serif;
    font-size: 1.5rem;
    font-weight: bold;
    justify-content: center;
    min-width: 65px;
    align-items: center;
    padding: 18px 24px;
    height: 65px;
    box-sizing: border-box;
  }

  .utility {
    color: #868888;
    flex: auto;
  }

  .key:hover {
    background:  #ffd200;
    color: black;
  }

  .jiggle {
    animation: jiggle 1s;
    animation-iteration-count: infinite;
    background: #60C1B6;
    color: white;
  }

  @keyframes jiggle {
    0% { transform: translate(1px, 1px) rotate(0deg); }
    10% { transform: translate(-1px, -2px) rotate(-1deg); }
    20% { transform: translate(-3px, 0px) rotate(1deg); }
    30% { transform: translate(3px, 2px) rotate(0deg); }
    40% { transform: translate(1px, -1px) rotate(1deg); }
    50% { transform: translate(-1px, 2px) rotate(-1deg); }
    60% { transform: translate(-3px, 1px) rotate(0deg); }
    70% { transform: translate(3px, 1px) rotate(-1deg); }
    80% { transform: translate(-1px, -1px) rotate(1deg); }
    90% { transform: translate(1px, 2px) rotate(0deg); }
    100% { transform: translate(1px, -2px) rotate(-1deg); }
  }
</style>
<script>

let sliderValue = 50;



</script>

<svelte:head>
  <title>AoJS - Day6</title>
</svelte:head>
<div class="wrapper">
  <div class="amount">
    <sup>$</sup>
    <span class="dollars">{sliderValue / 100}</span>
  </div>
  <input type="range" id="priceRange" min="0" max="10000" step="1" bind:value={sliderValue} />
  <br />
  <button>Buy Now</button>
</div>

<style>
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@700&display=swap');

:global(body) {
  background: #262529;
  display: flex;
  align-items: center;
  justify-content: center;
  min-width: 100vw;
  min-height: 100vh;
  font-family: 'Source Sans Pro', sans-serif;
}

.wrapper {
  background: #262529;
  box-shadow: 0px 0px 250px #000000;
  border-radius: 20px;
  padding: 60px 80px;
  text-align: center;
}

.amount {
  color: #FFC700;
  font-weight: bold;
  font-size: 6rem;
}

.dollar-sign {
  font-size: 5.5rem;
}

.dollars {

}

input[type=range] {
  -webkit-appearance: none;
  appearance: none;
  border-radius: 10px;
  width: 700px;
  height: 14px;
  background: #4D4C53;
  outline: none;
  margin: 70px 0;
}

/* slider handle */
input[type=range]::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 50px;
  height: 50px;
  background: #EA346F;
  cursor: pointer;
  border-radius: 50%;
  outline: 15px solid rgba(234, 52, 111, .2);
}

input[type=range]::-moz-range-thumb {
  -webkit-appearance: none;
  appearance: none;
  border: none; /* firefox needs this */
  width: 50px;
  height: 50px;
  background: #EA346F;
  cursor: pointer;
  border-radius: 50%;
  outline: 15px solid rgba(234, 52, 111, .2);
}

/* progress (before knob) within Firefox */
input[type=range]::-moz-range-progress {
  background: #EA346F;
  border-top-left-radius: 10px;
  border-bottom-left-radius: 10px;
  height: 14px;
}


button {
  font-family: 'Source Sans Pro', sans-serif;
  border: none;
  color: white;
  font-size: 1.5rem;
  text-transform: uppercase;
  padding: 20px 40px;
  background: #333139;
  border-radius: 100px;
  letter-spacing: 1px;
  cursor: pointer;
}

button:hover {
  background: white;
  color: black;
}
</style>
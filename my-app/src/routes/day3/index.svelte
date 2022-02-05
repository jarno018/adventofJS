<script>
  import keys from './paths'

  let count = 0;

  const handleWhiteClick = (number) => {
    let audio = new Audio('/static/audio/key-' + number + '.mp3');
    audio.play();
  }

  const handleBlackClick = (number) => {
    let audio = new Audio('/static/audio/key-' + number + '.mp3');
    audio.play();
  }

</script>

<svelte:head>
  <title>AoJS - Piano</title>
</svelte:head>
<div class="piano">
  <svg width="1387" height="467" viewBox="0 0 1387 467" fill="none" xmlns="http://www.w3.org/2000/svg">

    <!-- white keys -->
    {#each keys.whiteKeys as key, index}
      <a on:click="{() => handleWhiteClick(index + 1)}" href="#">
        <path class="white-keys" d= {key}/>
      </a>
      {count = index + 1}
    {/each}

    <!-- black keys -->
    {#each keys.blackKeys as key, index}
      <a on:click="{() => handleBlackClick(count + index + 1)}" href="#">
        <path class="black-keys" d={key} />
      </a>
    {/each}

  </svg>

</div>

<style>
  :global(body) {
    background-color: aqua;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
  .black-keys {
    fill: black;
  }
  .white-keys {
    fill: white;
  }
  .black-keys:hover {
    fill: #f40082;
  }
  .white-keys:hover {
    fill: #ffd200;
  }

</style>
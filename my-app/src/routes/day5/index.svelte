<script>
  //@ts-nocheck
import { onMount } from "svelte";

  let lastSelectedIndex = undefined;

  let checkboxes = [];

  const findIndex = (arr, compareValue) => {

    let returnValue = undefined;

    arr.forEach((element, index) => {
      if(element === compareValue) returnValue = index;
    });

    return returnValue;
  }

  onMount(() => {

    checkboxes = document.querySelectorAll('input[type=checkbox]');

    checkboxes.forEach(box => {
      box.addEventListener('click', (e) => {
        if(e.target.checked) {

          let selectedIndex = findIndex(checkboxes, e.target);
          console.log(selectedIndex + ' ' + lastSelectedIndex);

          if(lastSelectedIndex !== undefined && e.shiftKey) {
            if(selectedIndex > lastSelectedIndex) {
              
              for(let i = lastSelectedIndex; i <= selectedIndex; i++) {
                console.log(checkboxes[i]);
                checkboxes[i].checked = true;
              }
            }
            else {
              for(let i = selectedIndex; i >= lastSelectedIndex; i--) {
                checkboxes[i].checked = true;
              }
            }
          }


          lastSelectedIndex = findIndex(checkboxes, e.target);
        }
      })
    })

  })
</script>

<svelte:head>
  <title>AoJS - Album</title>
</svelte:head>
<div class="wrapper">
  <div class="cover">
    <img src="./images/podcast-cover.png" alt="Compressed.fm" />
  </div>
  <div class="content">
    <h1>Listen to all the Compressed.fm Episodes</h1>

    <ul class="episodes">
      <li>
        <label for="episode-1">
          <input type="checkbox" name="episode-1" id="episode-1" />
          <span>1 || Trailer</span>
        </label>
      </li>
      <li>
        <label for="episode-2">
          <input type="checkbox" name="episode-2" id="episode-2" />
          <span>2 || James Q Quick Origin Story</span>
        </label>
      </li>
      <li>
        <label for="episode-3">
          <input type="checkbox" name="episode-3" id="episode-3" />
          <span>3 || Amy Dutton's Origin Story</span>
        </label>
      </li>
      <li>
        <label for="episode-4">
          <input type="checkbox" name="episode-4" id="episode-4" />
          <span>4 || Starting a New Development Project</span>
        </label>
      </li>
      <li>
        <label for="episode-5">
          <input type="checkbox" name="episode-5" id="episode-5" />
          <span>5 || How Do you Start a New Design Project?</span>
        </label>
      </li>
      <li>
        <label for="episode-6">
          <input type="checkbox" name="episode-6" id="episode-6" />
          <span>6 || Freelancing (Part 1)</span>
        </label>
      </li>
      <li>
        <label for="episode-7">
          <input type="checkbox" name="episode-7" id="episode-7" />
          <span>7 || Freelancing (Part 2)</span>
        </label>
      </li>
      <li>
        <label for="episode-8">
          <input type="checkbox" name="episode-8" id="episode-8" />
          <span>8 || The Tech Behind jamesqquick.com</span>
        </label>
      </li>
      <li>
        <label for="episode-9">
          <input type="checkbox" name="episode-9" id="episode-9" />
          <span>9 || The Tech Behind SelfTeach.me</span>
        </label>
      </li>
      <li>
        <label for="episode-10">
          <input type="checkbox" name="episode-10" id="episode-10" />
          <span>10 || Tech Behind SelfTeach.me</span>
        </label>
      </li>
    </ul>
  </div>
</div>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@400;700&display=swap');

:global(body) {
  background: #F3F3F3;
  color: #4E4E4E;
  min-width: 100vw;
  min-height: 100vh;
  display: flex;
  align-items: center;
  font-family: 'Nunito Sans', sans-serif;
  justify-content: center;
}

.wrapper {
  display: flex;
  align-items: center;
}

.cover {
  filter: drop-shadow(0px 4px 24px #453F3F);
}

.content {
  background: white;
  border-top-right-radius: 32px;
  border-bottom-right-radius: 32px;
  padding: 60px 80px;
  height: 450px;
  overflow-y: scroll;
}

h1 {
  font-weight: bold;
  font-size: .75rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: #A7A7A7;
  margin: 0 0 40px 0;
  padding: 0;
}

input[type="checkbox"] {
  display: none;
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

li {
  margin-bottom: 24px;
  font-size: 1rem;
}

label {
  cursor: pointer;
}

input[type="checkbox"] + span {
  background: url('./images/checkbox--unchecked.svg') left top no-repeat;
  background-size: 20px 20px;
  min-height: 20px;
  padding-left: 30px;
}

input[type="checkbox"]:checked + span {
  background-image: url('images/checkbox--checked.svg');
  text-decoration: line-through;
  color: #C9CDD1;
}

button {
  background: #8C59FF;
  border: none;
  border-radius: 24px;
  text-transform: uppercase;
  font-family: 'Nunito Sans', sans-serif;
  font-weight: bold;
  padding: 8px 25px;
  color: white;
  line-height: 1;
  letter-spacing: 2px;
  cursor: pointer;
}

button:hover {
  background: #543599;
}

</style>
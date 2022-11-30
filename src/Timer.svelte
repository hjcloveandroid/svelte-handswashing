<script>
    import { createEventDispatcher } from "svelte";
  import ProgressBar from "./ProgressBar.svelte";

  const totalSeconds = 10;
  let secondSeconds = totalSeconds;
  let timer = null;

  $: progress = ((totalSeconds - secondSeconds)/totalSeconds)*100;
  const dispatcher = createEventDispatcher();
  function startTimer() {
    if (timer) return;
    timer = setInterval(() => {
      secondSeconds--;
      if (secondSeconds == 0) {
        clearInterval(timer);
        secondSeconds = totalSeconds;
        dispatcher('end', 'washing is end...');
      }
    }, 1000);
  }
</script>

<div bp="grid">
  <h2 bp="offset-5@md 4@md 12@sm">Seconds left: {secondSeconds}</h2>
</div>
<!-- <h2>{progress}</h2> -->
<ProgressBar {progress}/>
<div bp="grid">
  <button disabled={secondSeconds!== 10} on:click={startTimer} class="start" bp="offset-5@md 4@md 12@sm"
    >Start</button
  >
</div>

<style>
  h2 {
    margin: 0;
  }
  .start {
    background-color: rgb(154, 73, 73);
    /*         width: 100%;
        margin: 10px 0; */
  }
  .start[disabled] {
    background-color: rgb(194, 194, 194);
    cursor:not-allowed;
  }
</style>

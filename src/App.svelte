<script>
  import Timer from "./Timer.svelte";
  import Howto from "./Howto.svelte";
  import Clock from "./Clock.svelte";
</script>

<h1>7 Steps Handwashing</h1>

<!-- <Clock /> -->
<Timer
  on:end={(evt) => {
    console.log(evt);
	alert(evt.detail);
  }}
/>

<Howto />

<style>
  h1 {
    text-align: center;
  }
</style>

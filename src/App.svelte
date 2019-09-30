<script>
	export let name;
  import Countdown from './Countdown.svelte';
  import Background from './Background.svelte';

</script>

<style lang="scss">
  .container-fluid {
    margin-left: 0;
    margin-right: 0;
    padding-left: 0;
    padding-right: 0;
  }
</style>

<div class="container-fluid">
  <Background/>
  <Countdown/>
</div>

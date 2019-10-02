<script>
  import Countdown from './Countdown.svelte';
  import Background from './Background.svelte';
  import Footer from './Footer.svelte';

  let photo;

  function handlePhoto(event) {
    photo=event.detail.photo;
  }

</script>

<style lang="scss">
  .container-fluid {
    margin-left: 0;
    margin-right: 0;
    padding-left: 0;
    padding-right: 0;
  }
</style>

<Background on:photo="{handlePhoto}" />

<main role="main" class="flex-shrink-0">
  <div class="container">
    <Countdown/>
  </div>
</main>

<Footer photo={photo}/>

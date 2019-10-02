<script>
  export let photo;
</script>

<style lang="scss">
  .container {
    background-color: black;
  }
</style>

<footer class="footer mt-auto py-0">
  <div class="container">
    {#if photo}
    <span class="text-white">📸 by <a href="{photo.links.html}" target="_blank">{photo.user.first_name} {photo.user.last_name}</a></span>
    {/if}
  </div>
</footer>

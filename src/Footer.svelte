<script>
  export let photo;
</script>

<style lang="scss">
  .footer {
    background-color: black;
  }
</style>

<footer class="footer mt-auto py-0">
  <div class="container-fluid pl-4">
    {#if photo}
    <span class="text-white text-center">📸 by <a href="{photo.links.html}" target="_blank">{photo.user.first_name} {photo.user.last_name}</a></span>
    {/if}
  </div>
</footer>

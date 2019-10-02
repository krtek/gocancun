<script>
  import { createEventDispatcher } from 'svelte';

  const API_KEY = '68bf6ef0426d5bb9b6502455c0b76fa8ae0f38ad4e38adabc6cf14438b2c61a1';
  const QUERY = 'mexico';
  const dispatch = createEventDispatcher();

  function toCssUrl(photo) {
    return 'https://farm' + photo.farm + '.staticflickr.com/' +
        photo.server + '/' + photo.id + '_' + photo.secret + '_b.jpg';
  };

  let photos;

  async function loadPhotos() {
    const response = await fetch('https://api.unsplash.com/search/photos/' +
      '?client_id=' + API_KEY +
      '&query=' + QUERY +
      '&per_page=100');
      let json = await response.json();
      photos = json.results;
      let photo = photos[Math.floor(Math.random() * photos.length)];
      await fetch(photo.urls.regular);
      //Send event with current photo to other components
      dispatch('photo', { photo });
      document.body.style.backgroundImage = "url('" + photo.urls.regular + "')";
  }

  loadPhotos();

</script>

<style lang="scss">
  :global(body) {
    background-repeat: no-repeat;
    background-attachment: scroll;
    background-position: center;
    background-size: cover;
    opacity: 0.9;
  }

</style>

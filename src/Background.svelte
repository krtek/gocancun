<script>
  const API_KEY = '5d4e7b2733ce0572a15b412c36bbf941';
  const PHOTOSET_IDS = ['72157689002978926'];

  function toCssUrl(photo) {
    return 'https://farm' + photo.farm + '.staticflickr.com/' +
        photo.server + '/' + photo.id + '_' + photo.secret + '_b.jpg';
  };

  let photos;

  async function loadPhotos() {
    const response = await fetch('https://api.flickr.com/services/rest/?method=flickr.photosets.getPhotos&' +
      'api_key=' + API_KEY +
      '&photoset_id=' + PHOTOSET_IDS[0] +
      '&format=json&nojsoncallback=1');
      let json = await response.json();
      photos = json.photoset.photo;
      let photo = photos[Math.floor(Math.random() * photos.length)];
      document.body.style.backgroundImage = "url('" + toCssUrl(photo) + "')";
  }

  loadPhotos();

</script>

<style lang="scss">
  :global(body) {
    background-repeat: no-repeat;
    background-attachment: scroll;
    background-position: center;
    background-size: cover;
    height: 100vh;
    opacity: 0.9;
  }

</style>

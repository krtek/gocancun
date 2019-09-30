<script>
  import moment from 'moment';

  const departure = moment("201911131520", "YYYYMMDDHHmm");
  let days, hours, minutes, seconds, millis = '';


  function animate() {
    let now = moment();
    days = departure.diff(now, 'days');
    now.add(days, 'days');
    hours = (departure.diff(now, 'hours') + '').padStart(2, '0');
    now.add(hours, 'hours');
    minutes = (departure.diff(now, 'minutes') + '').padStart(2, '0');
    now.add(minutes, 'minutes');
    seconds = (departure.diff(now, 'seconds') + '').padStart(2, '0');
    now.add(seconds, 'seconds');
    millis = (departure.diff(now, 'millis') + '').padStart(3, '0');

    window.requestAnimationFrame(animate);
  }
  animate();
</script>

<style lang="scss">
  .countdown {
    padding-top: 5rem;
    font-family: Montserrat,"Helvetica Neue",Helvetica,Arial,sans-serif;
    text-transform: uppercase;
    font-weight: 300;
    font-size: 3rem;
    line-height: 4rem;
    color: white;
    text-align: center;
    text-shadow: 1px 1px darkgray;
  }

  @media (min-width: 400px) {
    .countdown {
      font-size: 4rem;
      line-height: 6rem;
    }
  }


  @media (min-width: 768px) {
    .countdown {
      padding-top: 25rem;
      font-size: 7.5rem;
      line-height: 6rem;
    }
  }

</style>

<div class="countdown">
  {days} dní, {hours}:{minutes}:{seconds},{millis}
</div>

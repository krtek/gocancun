<script>
  import moment from 'moment';

  const departure = moment.parseZone("2020-11-13T15:20:00+01:00");
  let days, hours, minutes, seconds, millis = '';
  let now;


  function animate() {
    now = moment();
    //clone now to temp variable to allow modification
    let temp = now.clone();
    days = departure.diff(temp, 'days');
    temp.add(days, 'days');
    hours = (departure.diff(temp, 'hours') + '').padStart(2, '0');
    temp.add(hours, 'hours');
    minutes = (departure.diff(temp, 'minutes') + '').padStart(2, '0');
    temp.add(minutes, 'minutes');
    seconds = (departure.diff(temp, 'seconds') + '').padStart(2, '0');
    temp.add(seconds, 'seconds');
    millis = (departure.diff(temp, 'millis') + '').padStart(3, '0');

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
  {#if days>0}
  {days} dní,
  {/if}
  {#if now.isBefore(departure)}
  {hours}:{minutes}:{seconds},{millis}
  {/if}
</div>

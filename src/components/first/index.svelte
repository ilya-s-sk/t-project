<script>
  import style from './style.pcss';

  const audiosSources = [
    'https://orangefreesounds.com/wp-content/uploads/2022/08/Short-meow-sound-effect.mp3?_=1',
    'https://orangefreesounds.com/wp-content/uploads/2022/05/Cute-cat-meow-sound.mp3?_=1',
    'https://www.orangefreesounds.com/wp-content/uploads/2022/04/Cat-sound-meow.mp3?_=1',
    'https://www.orangefreesounds.com/wp-content/uploads/2014/12/Cat-meow.mp3?_=1',
    'https://www.orangefreesounds.com/wp-content/uploads/2014/06/Angry-cat-hissing-sound.mp3?_=1',
  ]

  let audio;
  let button;

  let step = 0;

  let position = 0;

  $: isEnough = step === audiosSources.length;

  function handleClick() {
    if (isEnough) return;

    audio.pause();
    audio.src = audiosSources[step];
    audio.play();

    step++;
  }

  function leave() {
    if (!isEnough) return;

    position += 20;
    button.style.left = `${position}px`;
  }
</script>

<section class={style.root}>

  <h1 class={style.title}>
    Добро пожаловать<br>
    на&nbsp;персональную страницу<br>
    <span class={style.highlight}>&laquo;Танечка самый лучший котёнок&raquo;</span> 
  </h1>
  <div class={style.inner}>
    <button
      class={`${style.icon} ${isEnough ? style.icon_enough : ''}`}
      on:click={handleClick}
      on:mousemove={leave}
      bind:this={button}
      title="Танечка котёнок"
    />
    <p class={style.text}>Здесь вы&nbsp;узнаете, почему Танечка&nbsp;&mdash; самый лучший котёнок на&nbsp;свете</p>
  </div>
  <audio bind:this={audio} src="" />
</section>
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
  let innerWidth;

  let step = 0;
  let sign = '';
  
  $: isMobile = innerWidth <= 650;
  $: isEnough = step === audiosSources.length;

  function handleClick() {
    if (isEnough) {
      leave()
      return;
    };

    if (step === 0) {
      alert('Включи звук!')
    }

    audio.pause();
    audio.src = audiosSources[step];
    audio.play();

    step++;
  }

  function leave() {
    if (!isEnough) return;

    const minValue = isMobile ? 50 : 200;
    const maxValue = isMobile ? 200 : 500;

    const value = Math.random() * (maxValue - minValue) + minValue;
    button.style = `transform: translateX(${sign}${value}px);`
    sign = sign === '' ? '-' : '';
  }
</script>

<svelte:window bind:innerWidth={innerWidth}/>
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
      on:mouseenter={!isMobile && leave}
      bind:this={button}
      title="Танечка котёнок"
    />
    <p class={style.text}>Здесь вы&nbsp;узнаете, почему Танечка&nbsp;&mdash; самый лучший котёнок на&nbsp;свете</p>
  </div>
  <audio bind:this={audio} src="" />
</section>
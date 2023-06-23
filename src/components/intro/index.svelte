<script>
  import Section from '../atoms/section/index.svelte';
  import style from './style.pcss';

  const audiosSources = [
    'https://orangefreesounds.com/wp-content/uploads/2022/08/Short-meow-sound-effect.mp3?_=1',
    'https://orangefreesounds.com/wp-content/uploads/2022/05/Cute-cat-meow-sound.mp3?_=1',
    'https://www.orangefreesounds.com/wp-content/uploads/2022/04/Cat-sound-meow.mp3?_=1',
    'https://www.orangefreesounds.com/wp-content/uploads/2014/12/Cat-meow.mp3?_=1',
    'https://www.orangefreesounds.com/wp-content/uploads/2014/06/Angry-cat-hissing-sound.mp3?_=1',
  ];

  const messages = [
    'Нажми сюда!',
    'Ещё нажми!',
    'Нажми опять!',
    'Нажми ещё раз!',
    'И ещё!',
    'Мне уже не нравится!'
  ]

  let button;
  let innerWidth;

  const audioObj = {};

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
      alert('Не забудь включить звук!')
    }

    if (step !== 0) {
      audioObj[step - 1].pause();
    }
    audioObj[step].play();

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
<Section isAnimated={false} class={style.root}>
  <h1 class={style.title}>
    Добро пожаловать<br>
    на&nbsp;персональную страничку<br>
    <span class={`gradientText ${style.highlight}`}>&laquo;Танечка самый лучший котёнок&raquo;</span> 
  </h1>
  <div class={style.inner}>
    <button
      class={`${style.icon} ${isEnough ? style.icon_enough : ''}`}
      on:click={handleClick}
      on:mouseenter={!isMobile && leave}
      bind:this={button}
      title="Танечка котёнок"
    >
      <span class={style.message}>{messages[step]}</span>
    </button>
    <p class={style.text}>Здесь вы&nbsp;узнаете,<br>почему Танечка&nbsp;&mdash;<br>самый лучший котёнок на&nbsp;свете</p>
  </div>
  {#each audiosSources as audio, index}
    <audio bind:this={audioObj[index]} src={audio} />
  {/each}
  <div class={style.heart} />
</Section>
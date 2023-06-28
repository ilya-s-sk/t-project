<script>
  import { onMount } from 'svelte';
  import Section from "../atoms/section/index.svelte";
  import style from "./style.pcss";

  let el, audio;

  let isPlaying = false;

  function handleScroll() {

    const { y, bottom, height } = el.getBoundingClientRect();
    const isElVisible = window.innerHeight - y >= 20 && bottom >= 20;

    if (isElVisible) {
      if (!isPlaying) {
        audio.play();
      }
      isPlaying = true;
      if (window.innerHeight - y < window.innerHeight) {
        const percent = 100 / window.innerHeight * (window.innerHeight - y);
        audio.volume = percent / 100;
      } else {
        const percent = bottom / (height / 100);
        audio.volume = percent / 100;
      }
    } else {
      if (isPlaying) {
        audio.pause();
      }
      isPlaying = false;
    }
  }

  function play() {
    console.log('play');
    audio.play()
  }

  onMount(() => {
    window.addEventListener('scroll', handleScroll);
  })
</script>

<Section class={style.sex} bind:element={el}>
  <div class={style.bg} />
  <div class={style.inner}>
    <div class={style.scrollBlock}>
      <div class={style.titleBlock}>
        <h2 class={ `gradientText ${style.title}`}>
          Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс
          Таня секс Таня секс
        </h2>
      </div>
    </div>
    <div class={style.scrollBlock}>
      <div class={style.titleBlock}>
        <h2 class={ `gradientText ${style.title}`}>
          Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс
          Таня секс Таня секс
        </h2>
      </div>
    </div>
    <div class={style.scrollBlock}>
      <div class={style.titleBlock}>
        <h2 class={ `gradientText ${style.title}`}>
          Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс
          Таня секс Таня секс
        </h2>
      </div>
    </div>
    <div class={style.scrollBlock}>
      <div class={style.titleBlock}>
        <h2 class={ `gradientText ${style.title}`}>
          Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс
          Таня секс Таня секс
        </h2>
      </div>
    </div>
    <div class={style.scrollBlock}>
      <div class={style.titleBlock}>
        <h2 class={ `gradientText ${style.title}`}>
          Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс
          Таня секс Таня секс
        </h2>
      </div>
    </div>
    <div class={style.scrollBlock}>
      <div class={style.titleBlock}>
        <h2 class={ `gradientText ${style.title}`}>
          Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс
          Таня секс Таня секс
        </h2>
      </div>
    </div>
    <div class={style.scrollBlock}>
      <div class={style.titleBlock}>
        <h2 class={ `gradientText ${style.title}`}>
          Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс
          Таня секс Таня секс
        </h2>
      </div>
    </div>
    <div class={style.scrollBlock}>
      <div class={style.titleBlock}>
        <h2 class={ `gradientText ${style.title}`}>
          Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс Таня секс
          Таня секс Таня секс
        </h2>
      </div>
    </div>
  </div>
  <audio src="https://dl2.mp3party.net/online/10848410.mp3" bind:this={audio} loop="true"></audio>
</Section>

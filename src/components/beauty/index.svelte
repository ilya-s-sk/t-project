<script>
  import { fade } from 'svelte/transition';

  import Section from '../atoms/section/index.svelte';
  import Title from '../atoms/title/index.svelte';
  import style from './style.pcss';

  import img from '../../assets/photos/beauty.jpg'
  import img2 from '../../assets/photos/beauty-2.jpg'
  import kitty from '../../assets/kitty.jpg';

  let isCold = false;

  let isKittyHidden = true;

  function showKitty() {
    setTimeout(() => {isKittyHidden = false;}, 500)
  }
</script>

<div class={style.root}>

  <img class={`${style.kitty} ${isKittyHidden ? style.hidden : '' }`} src={kitty} alt="Танечка на розовой подушечке">
  <Section class={style.beauty} on:intersect={showKitty}>
    <div class={style.inner}>
  
      <Title
        class={style.title}
        content="Танечка очень красивая"
        count={1}
      />
      <p class={style.text}>И при любой температуре!</p>
    </div>
      <div class={style.imageBlock}>
        {#if isCold}
          <div transition:fade>
            <img 
              class={style.image}
              src={img2}
              alt="Танчека красивая в шапке"
            >
            <div class={style.snow} />
          </div>
        {:else}
          <div transition:fade>
            <img
              class={style.image}
              src={img}
              alt="Танечка красивая просто"
            >
            <div class={style.sun} />
          </div>
        {/if}
      </div>
    <div class={style.toggleBox}>
      <p class={style.toggleDescr}>
        сделать {isCold ? 'потеплее' : 'похолоднее'}
      </p>
      <input class={style.input} bind:value={isCold} bind:checked={isCold} type="checkbox" id="season">
      <label class={style.toggleBar} for="season">
        <span class={style.toggler}></span>
      </label>
    </div>
  
  </Section>
</div>
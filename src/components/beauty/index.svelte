<script>
  import { fade } from 'svelte/transition';
  import Section from '../atoms/section/index.svelte';
  import style from './style.pcss';
  import img from '../../assets/photos/beauty.jpg'
  import img2 from '../../assets/photos/beauty-2.jpg'

  let isCold = false;
</script>

<Section class={style.root}>
  <div class={style.inner}>

    <h2 class={style.title}>
      <span class={`gradientText ${style.count}`}>1</span><br>
      Танечка очень красивая
    </h2>
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
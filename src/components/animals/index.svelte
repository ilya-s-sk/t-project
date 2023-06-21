<script>
  import { onMount } from "svelte";
  import Glide from '@glidejs/glide'

  import Section from "../atoms/section/index.svelte";
  import Title from "../atoms/title/index.svelte";
  import style from "./style.pcss";


  import img1 from "../../assets/photos/animals-1.jpeg";
  import img2 from "../../assets/photos/animals-2.jpeg";
  import img3 from "../../assets/photos/animals-3.jpeg";
  import img4 from "../../assets/photos/animals-4.jpeg";
  import img5 from "../../assets/photos/animals-5.jpeg";
  import img6 from "../../assets/photos/animals-6.jpeg";
  
  const slides = [img1, img2, img3, img4, img5, img6];

  onMount(() => {
    new Glide('.glide', {
      type: 'carousel',
      autoplay: 2000
    }).mount()
  })
</script>

<Section class={style.animals}>
  <Title class={style.title} count={5} content="Таню очень любят животные!" />
  <div class="glide">
    <div class={"glide__track" + ` ${style.slider}`} data-glide-el="track">
      <ul class="glide__slides">
        {#each slides as slide}  
          <li class="glide__slide">
            <img class={style.image} src={slide} alt="">
          </li>
        {/each}
      </ul>
      <div class={`glide__arrows ${style.controls}`} data-glide-el="controls">
        <button class={"glide__arrow glide__arrow--left"  + ` ${style.controlButton}`} data-glide-dir="<">туда</button>
        <button class={"glide__arrow glide__arrow--right" + ` ${style.controlButton}`} data-glide-dir=">">сюда</button>
      </div>
    </div>
  </div>
</Section>

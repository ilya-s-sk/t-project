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
  import img7 from "../../assets/photos/animals-7.jpeg";
  import img8 from "../../assets/photos/animals-8.jpeg";
  import img9 from "../../assets/photos/animals-9.jpeg";
  import img10 from "../../assets/photos/animals-10.jpeg";
  import img11 from "../../assets/photos/animals-11.jpeg";
  
  const slides = [img2, img7, img1, img8, img3, img9, img4, img10, img5, img6, img11];

  onMount(() => {
    new Glide('.glide', {
      type: 'carousel',
      peek: 15,
      gap: 20,
      // autoplay: 2000
    }).mount()
  })
</script>

<Section class={style.animals}>
  <Title class={style.title} count={5} content="Танечку очень любят животные!" />
  <div class={style.emoji}>
    <span>🐈</span> <span>🐕</span>
  </div>
  <div class="glide">
    <div class={"glide__track" + ` ${style.slider}`} data-glide-el="track">
      <ul class={"glide__slides" + ` ${style.slides}`}>
        {#each slides as slide}  
          <li class={"glide__slide" + ` ${style.slide}`}>
            <img class={style.image} src={slide} alt="">
          </li>
        {/each}
      </ul>
      <div class={`glide__arrows ${style.controls}`} data-glide-el="controls">
        <button class={"glide__arrow glide__arrow--left"  + ` ${style.controlButton}`} data-glide-dir="<">&lt; туда</button>
        <button class={"glide__arrow glide__arrow--right" + ` ${style.controlButton}`} data-glide-dir=">">сюда &gt;</button>
      </div>
    </div>
  </div>
</Section>

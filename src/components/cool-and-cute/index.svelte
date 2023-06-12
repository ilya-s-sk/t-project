<script>
  import { fly } from "svelte/transition";

  import Section from "../atoms/section/index.svelte";
  import Title from '../atoms/title/index.svelte';
  import style from "./style.pcss";

  import img1 from "../../assets/photos/cool-and-cute-1.jpeg";
  import img2 from "../../assets/photos/cool-and-cute-2.jpeg";
  import img3 from "../../assets/photos/cool-and-cute-3.jpeg";

  const images = [
    null,
    {
      src: img1,
      alt: "Танечка крутая",
    },
    {
      src: img3,
      alt: "Танечка нежная",
    },
    {
      src: img2,
      alt: "Танечка нежная и крутая",
    },
  ];

  const texts = [
    "Какая же она?",
    "Она крутая!",
    "Она нежная!",
    "Она и крутая, и нежная!",
  ];

  let currentStep = 0;

  function handleClick() {
    currentStep = currentStep === images.length - 1 ? 0 : currentStep + 1;
  }
</script>

<Section class={style.coolAndCute}>
  <span class={style.emoji}>😍</span>
  <Title
  class={style.title}
    count={2}
    content="Танечка может быть какой угодно"
  />
  <div class={style.card}>
    {#each images as image, index}
      {#if index <= currentStep && image}
        <img
          in:fly={{
            duration: 300,
            x: 400,
          }}
          out:fly={{
            x: -400
          }}
          class={style.image}
          src={image.src}
          alt={image.alt}
        />
      {/if}
    {/each}
    <span class={`gradientText ${style.cardText}`}>?</span>
  </div>
  <p class={style.text}>{texts[currentStep]}</p>
  <button class={style.button} on:click={handleClick}>
    {currentStep === 0
      ? "Узнать какая она"
      : currentStep === images.length - 1
      ? "Такого не может быть!"
      : "А ещё?"}
  </button>
</Section>

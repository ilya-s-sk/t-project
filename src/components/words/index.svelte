<script>
  import Section from "../atoms/section/index.svelte"
  import style from "./style.pcss";

  import { words } from './data';

  $: define = words[randIndex] || '???';

  let randIndex = null;

  let isChanging = false;
  let isAnimationStart = false;

  function defineWord() {
    if (isChanging) return;
    isChanging = true;

    isAnimationStart = true;
    

    setTimeout(() => {
      let newRandInd = Math.floor(Math.random() * words.length);
      while (randIndex === newRandInd) {
        newRandInd = Math.floor(Math.random() * words.length);
      }
      randIndex = newRandInd;
      isAnimationStart = false;
      isChanging = false;
    }, 500)
  }
</script>

<Section class={style.words}>
  <p class={style.text}>
    Танечка настолько хороша, что пунктов, чтобы перечислить все её достоинства не хватит, но можно попробовать их назвать
  </p>
  <h2 class={`${style.define} ${isAnimationStart ? style.animation : ''}`}>
    Танечка &mdash;<br><span class={style.defineText}>{define}</span>
  </h2>
  <button on:click={defineWord}>
    Какая?
  </button>
</Section>
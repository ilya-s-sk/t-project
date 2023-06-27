<script>
  import Section from "../atoms/section/index.svelte"
  import style from "./style.pcss";

  import { words } from './data';

  shuffle(words);

  $: define = words[currentIndex] || '???';

  let currentIndex = null;

  let isChanging = false;
  let isAnimationStart = false;

  function defineWord() {
    if (isChanging) return;
    isChanging = true;

    isAnimationStart = true;


    setTimeout(() => {
      if (currentIndex === words.length - 1) {
        shuffle(words);
        currentIndex = null;
      }
      currentIndex = typeof currentIndex === 'number' ? currentIndex + 1 : 0;
      isAnimationStart = false;
      isChanging = false;
    }, 500)
  }

  function shuffle(array) {
    for (let i = array.length - 1; i > 0; i--) {
      let j = Math.floor(Math.random() * (i + 1));
      [array[i], array[j]] = [array[j], array[i]];
    }
  }

</script>

<Section class={style.words}>
  <p class={style.text}>
    Танечка настолько хороша, что пунктов, чтобы перечислить все её достоинства не хватит, но можно попробовать их назвать
  </p>
  <h2 class={`${style.define} ${isAnimationStart ? style.animation : ''}`}>
    Танечка &mdash;<br><span class={style.defineText}>{define}</span>
  </h2>
  <button class={style.button} on:click={defineWord}>
    Какая?
  </button>
</Section>
<script>
  import { onMount, createEventDispatcher } from "svelte";
  import style from './style.pcss';

  export let isAnimated = true;
  export let once = true;
  export let element = null;

  let comp;
  let isHidden = true;

  const dispatch = createEventDispatcher();

  onMount(() => {
    element = comp;

    if (!isAnimated) {
      return
    };

    const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            once && observer.unobserve(entry.target); 
            dispatch('intersect');
            isHidden = false;
          }
        });
      }, {
        threshold: 0.7,
      });
    
    observer.observe(comp);

    return () => {
      observer.unobserve(comp);
    }
  })
</script>

<section bind:this={comp} class={`${$$props.class} ${style.section} ${(isHidden && isAnimated) ? style.hidden : ''}`}>
  <slot />
</section>
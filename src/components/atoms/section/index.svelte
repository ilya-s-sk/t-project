<script>
  import { onMount, createEventDispatcher } from "svelte";
  import style from './style.pcss';

  export let isAnimated = true;

  let comp;
  let isHidden = true;

  const dispatch = createEventDispatcher();

  onMount(() => {
    if (!isAnimated) {
      return
    };

    const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            observer.unobserve(entry.target);
            dispatch('intersect');
            isHidden = false;
          }
        });
      }, {
        threshold: 0.8,
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
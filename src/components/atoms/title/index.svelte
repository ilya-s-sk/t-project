<script>
  import style from './style.pcss';

  export let count = '';
  export let content = '';
</script>

<h2 class={`${style.title} ${$$props.class}`}>
  <span class={`gradientText ${style.count}`}>{count}</span><br />
  {content}
</h2>

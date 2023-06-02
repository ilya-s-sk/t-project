<script>
  import Section from '../atoms/section/index.svelte';
  import style from './style.pcss';

  import img1 from '../../assets/photos/cool-and-cute-1.jpeg';
  import img2 from '../../assets/photos/cool-and-cute-2.jpeg';
  import img3 from '../../assets/photos/cool-and-cute-3.jpeg';
</script>

<Section>
  <div class={style.imageBlock}>
    <img class={`${style.image} ${style.imageLeft}`} src={img1} alt="Танечка крутая">
    <img class={style.image} src={img2} alt="Танечка нежная и крутая">
    <img class={`${style.image} ${style.imageRight}`} src={img3} alt="Танечка нежная">
  </div>
</Section>
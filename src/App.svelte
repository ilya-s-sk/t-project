<script>
	import style from './app.pcss';
	import Intro from './components/intro/index.svelte';
	import Beauty from './components/beauty/index.svelte';
	import CoolAndCute from './components/cool-and-cute/index.svelte';
	import Sex from './components/sex/index.svelte';
	import Quiz from './components/quiz/index.svelte';
</script>

<main class={style.main}>
	<Intro />
	<Beauty />
	<CoolAndCute />
	<Sex />
	<Quiz />
</main>

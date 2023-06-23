<script>
	import style from './app.pcss';

	import Intro from './components/intro/index.svelte';
	import Beauty from './components/beauty/index.svelte';
	import CoolAndCute from './components/cool-and-cute/index.svelte';
	import Sex from './components/sex/index.svelte';
	import Quiz from './components/quiz/index.svelte';
	import Animals from './components/animals/index.svelte';
	import Words from './components/words/index.svelte';
</script>

<main class={style.main}>
	<Intro />
	<Beauty />
	<CoolAndCute />
	<Sex />
	<Quiz />
	<Animals />
	<Words />
</main>

<script>
	export let name;
	import Nested from './Nested.svelte';
	import Header from './header.svelte';
	import Content from './content.svelte';
	import Footer from './footer.svelte';

	let count = 0; // state(상태값)

	const handleClick = () => count = count + 1; // count를 count + 1로 재할당

	let my = {
		name: '박문우',
		age: 37,
		sex: 'male',
	}
</script>
<Header />
<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<Nested />
	<Content />
	<Content />
	<button on:click={handleClick}>
		클릭수 {count} <!-- { } 기호로 마크업에 상태값 표시-->
	</button>
	<h2>이름 : {my.name}</h2>
	<h2>나이 : {my.age}</h2>
	<h2>성별 : {my.sex}</h2>
</main>
<Footer />
<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
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

	let list = [
		{
			id:0,
			content: 'todo 1st',
			done: false,
		},
		{
			id:1,
			content: 'todo 2nd',
			done: false,
		},
		{
			id:2,
			content: 'todo 3rd',
			done: true,
		},
		{
			id:3,
			content: 'todo 4th',
			done: false,
		},
	]
	const handleAddTodo = () => {
		const todo = {
			id: list.length + 1,
			content: 'new todo',
			done: false
		}
		list = [...list, todo]
	}

	let count2 = 1;
	function handleClick2() {
		count2 += 1
	}
	$: doubled = count * 2
	$: {
		console.log( count )
		console.log( doubled )
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
		클릭수 {count} {count===1 ? 'time' : 'times'}<!-- { } 기호로 마크업에 상태값 표시-->
	</button>
	<p>{count}의 두 배 값 출력 : {doubled}</p>
	<h2>이름 : {my.name}</h2>
	<h2>나이 : {my.age}</h2>
	<h2>성별 : {my.sex}</h2>
	<h2>2023.09.01</h2>
	<ul>
		{#each list as item}
		<li>
			<p>{item.id}</p>
			<p>{item.content}</p>
			<p>{item.done}</p>
		</li>
		{/each}
	</ul>
	<button on:click={handleAddTodo}>할 일 추가</button>
	<button on:click={handleClick2}>
		클릭 수 {count2} {count2 === 1 ? 'time' : 'times'}
	</button>
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
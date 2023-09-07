<script>
	export let name;
	import Nested from './Nested.svelte';
	import Header from './header.svelte';
	import Content from './content.svelte';
	import Footer from './footer.svelte';
	import Child from './child.svelte';
	import Child2 from './child2.svelte';

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
	$: if(count>=10) {
		alert('카운트가 10을 넘었습니다. 처음으로 돌아갑니다.')
		count = 0
	}
	let m = { x:0, y:0};
	function handleMousemove(event){
		m.x = event.clientX;
		m.y = event.clientY;
	}
	function handleClick3(param){
		alert(`선택값 ${param}`)
	}
	function handleClick4(param){
		alert(`선택값은바로바로 ${param}`)
	}
	function handleClick5(param){
		alert('only one alert')
	}
	let count3 = 15;
	const handleClick6 = () => count3 += 1;
	let count4=0;
	const handleClick8= () => count4 += 1;
</script>
<Header />
<Child carryValue={12} />
<Child carryValue={count3} handleClick6={handleClick6} />
<Child2 {count4} {handleClick8} />
<main>
	<button on:click={handleClick6}>클릭</button>
	<button on:click|once={handleClick5}>한 번만 경고창이 뜨는 버튼</button>
	<button on:click={() => handleClick3('버튼1')}>	버튼1번을눌러보세요 </button>
	<button on:click={() => handleClick4('버튼2')}> 버튼2번을눌러보세요 </button>
	<button on:click={() => handleClick3('버튼3')}> 버튼3번을눌러보세요 </button>
	
	<!-- 인자값을 넘겨야 하는데 화살표함수를 쓰지 않은 이벤트는 코드 실행과 동시에 발동해 버린다. 주의!
		<button on:click={handleClick3('버튼3')}> 버튼3번을누르면어떤일이 </button>
		<button on:click={handleClick3('버튼4')}> 버튼4번은 3번과 같은 이벤트로 지정되어 있고 화살표함수를 쓰지 않음 </button>
	-->
	<div class='one' on:mousemove={handleMousemove}>
		The mouse position is {m.x} x {m.y}
	</div>
	<div class="two" on:mousemove="{e => m = {x: e.clientX, y: e.clientY}}">
		Second function mouse position is {m.x} x {m.y}
	</div>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<Nested />
	<Content />
	<Content />
	<button on:click={handleClick}>
		클릭수 {count} {count<=1 ? 'time' : 'times'}<!-- { } 기호로 마크업에 상태값 표시-->
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
	div.one {
		width:500px; height:500px;
		background-color: black;
		}
		.two {
			width:200px; height: 200px;
			background-color: red;
		}
</style>
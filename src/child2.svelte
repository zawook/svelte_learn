<script>
    export let count4;
    export let handleClick8;
    import Childchild from './childchild.svelte';
</script>

<p>전달된 값 확인 : { count4 }</p>
<button on:click={handleClick8}>Child2 클릭</button>

<Childchild {count4} {handleClick8} />
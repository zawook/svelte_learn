<script>
    export let carryValue;
    export let handleClick6;
    const handleClick7 = () => carryValue += 1;
</script>

<p>전달된 값은 {carryValue} 입니다.</p>

<button on:click={handleClick6}>전달된 const 클릭</button>
<button on:click={handleClick7}>이걸 누르면 위에 전달된 값이 증가하나?</button>
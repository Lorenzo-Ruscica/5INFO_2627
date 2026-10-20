<script>
    import Counter from "#lib/components/counter.svelte";
    import DoubleCounter from "#lib/components/double_counter.svelte";
    let contatore = 1;
    let double_counter = 0;
    let numeri = [1, 7, 2, 6, 9, 10]
</script>
<h1>Pagina Counter</h1>

{#if contatore < 5}
    <h2 class="rosso">Il valore del contatore vale: {contatore}</h2>
{:else if contatore > 10}
    <h2 class="blu">Il valore del contatore vale: {contatore}</h2>
{:else}
    <h2 class="verde">Il valore del contatore vale: {contatore}</h2>
{/if}
<Counter bind:counter={contatore} />

<ul>
    {#each numeri as numero, indice}
        <li>numeri[{indice}]: {numero}</li>
    {/each}
</ul>

<h2>Il valore del contatore vale: {double_counter}</h2>
<DoubleCounter bind:counter={double_counter} />

<style>
    .rosso { color: red;}
    .verde { color: green;}
    .blu   { color: blue}
</style>    




<script>
    import Counter from "#lib/components/counter.svelte";
    import DoubleCounter from "#lib/components/double_counter.svelte";
    let contatore = 1;
    let double_counter
</script>
<h1>Pagina Counter</h1>
<h2>Il valore del contatore vale: {contatore}</h2>
<Counter bind:counter={contatore} />
<h2>Il valore del contatore vale: {double_counter}</h2>
<DoubleCounter bind:counter={double_counter} />
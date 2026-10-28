<script>
	import Dropdown from '#lib/components/dropdown.svelte';

	let regione = '';
	let citta_scelta = '';
	let nazione = '';

	let regioni = ['Piemonte', 'Lombardia', 'Veneto'];
	let citta = ['Torino', 'Milano', 'Venezia'];
	let nazioni = ['Italia', 'Francia', 'Germania'];
</script>

<h1>DROP DOWN TESTER</h1>

<Dropdown title="Regione" items={regioni} bind:selezionato={regione} />
<Dropdown title="Città" items={citta} bind:selezionato={citta_scelta} />
<Dropdown title="Nazione" items={nazioni} bind:selezionato={nazione} />

{#if regione !== ''}
	<h2>Hai selezionato la regione: {regione}</h2>
{/if}

{#if citta_scelta !== ''}
	<h2>Hai selezionato la città: {citta_scelta}</h2>
{/if}

{#if nazione !== ''}
	<h2>Hai selezionato la nazione: {nazione}</h2>
{/if}
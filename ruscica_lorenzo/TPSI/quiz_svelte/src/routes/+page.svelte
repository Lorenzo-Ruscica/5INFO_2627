<script>
	import Domanda from '../lib/components/domanda.svelte';

	let domande = [
		{
			testo: "In Svelte 4, come si dichiara una prop in un componente?",
			opzioni: ["props nome;", "export let nome;", "let prop nome;", "import nome;"],
			corretta: 1
		},
		{
			testo: "Quale costrutto permette di iterare un array in Svelte?",
			opzioni: ["{#for}", "{#loop}", "{#each}", "{#map}"],
			corretta: 2
		},
		{
			testo: "Come si introduce una dichiarazione reattiva in Svelte?",
			opzioni: ["$:", "@:", "#:", "!:"],
			corretta: 0
		},
		{
			testo: "Come si gestisce l'evento click su un pulsante in Svelte?",
			opzioni: ["onclick={fn}", "on:click={fn}", "@click={fn}", "v-on:click={fn}"],
			corretta: 1
		},
		{
			testo: "Quale funzione si usa per emettere Component Events?",
			opzioni: ["createEvent()", "emitEvent()", "createEventDispatcher()", "dispatchEvent()"],
			corretta: 2
		},
		{
			testo: "Quale direttiva applica una classe CSS in base a una condizione?",
			opzioni: ["style:nome", "bind:class", "use:class", "class:nome"],
			corretta: 3
		}
	];

	let indice = 0;
	let punteggio = 0;
	let risposteDate = [];
	let finito = false;

	$: totale = domande.length;
	$: domandaCorrente = domande[indice];
	$: rispostaCorrente = risposteDate[indice];
	$: ultima = indice === totale - 1;
	$: percentuale = Math.round((punteggio / totale) * 100);

	function salvaRisposta(event) {
		risposteDate[indice] = event.detail;
		if (event.detail === domandaCorrente.corretta) {
			punteggio++;
		}
	}

	function vaiAvanti() {
		if (ultima) {
			finito = true;
		} else {
			indice++;
		}
	}

	function ricomincia() {
		indice = 0;
		punteggio = 0;
		risposteDate = [];
		finito = false;
	}
</script>

<h1>Quiz Svelte</h1>

<p>Domanda {indice + 1} di {totale} · Punteggio: {punteggio}</p>
<progress value={indice + 1} max={totale}></progress>

{#if !finito}
	<Domanda
		domanda={domandaCorrente}
		rispostaData={rispostaCorrente}
		ultima={ultima}
		on:risposta={salvaRisposta}
		on:avanti={vaiAvanti}
	/>
{:else}
	<h2>Risultato: {punteggio} su {totale} ({percentuale}%)</h2>

	{#if percentuale === 100}
		<p>Giudizio: Ottimo</p>
	{:else if percentuale >= 60}
		<p>Giudizio: Sufficiente</p>
	{:else}
		<p>Giudizio: Insufficiente</p>
	{/if}

	{#each domande as dom, i}
		<p
			class:verde={risposteDate[i] === dom.corretta}
			class:rosso={risposteDate[i] !== dom.corretta}
		>
			{i + 1}. {dom.testo} - Risposta: {dom.opzioni[risposteDate[i]]}
		</p>
	{/each}

	<button on:click={ricomincia}>Ricomincia</button>
{/if}

<style>
	.verde {
		color: green;
	}
	.rosso {
		color: red;
	}
</style>
<script>
  	let a = 149.34;
	let b = 40;
	let c = 3;
	let s = false;
	let r = false;
</script>

<main>
<h1>Payment Calculator</h1>
<label>
	<input type=checkbox bind:checked={r}>
	Round up result
</label>
<p>If you pay:</p>
<input class="input" type=number bind:value={a}>
<p>and tip</p>
<input class="input" type=number bind:value={b}>%
<label>
	<p>then your Total is</p>
	{#if r}
		<h2>${Math.ceil(((a + ((a * (b/100)) < 0.01 ? 0 : a * (b/100)))/ c || 1))}</h2>{#if c>1}per person{/if}
	{:else}
		<h2>${((a + ((a * (b/100)) < 0.01 ? 0 : a * (b/100)))/ c || 1).toFixed(2)}</h2>{#if c>1}per person{/if}
	{/if}
</label>
<br>
<p/>
Split with <input class="input" type=number style="width: 50px;"  bind:value={c}> {#if c > 1}people{:else}person{/if}
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }
  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }

  h1 {
    color: #84DCCF;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  h2 {
    color: #84DCCF;
    text-transform: uppercase;
    font-size: 2rem;
    font-weight: 80;
    line-height: 1.08;
    margin: 1rem auto;
    max-width: 12rem;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  .input {
    font-family: inherit;
    font-size: inherit;
    padding: 1em 2em;
    color: #063D28;
    background-color: #c2e7d9;
    border-radius: 2em;
    border: 2px solid rgba(255, 62, 0, 0);
    outline: none;
    width: 200px;
    font-variant-numeric: tabular-nums;
    cursor: pointer;
  }

  .input:hover {
    border: 2px solid #c2ffd9;
  }

  .input:active {
    background-color: #c2e9d9;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }
</style>

<script>
	import BlueThing from './BlueThing.svelte';
	import GreenThing from './GreenThing.svelte';
	import RedThing from './RedThing.svelte';

	let isActive = 'BlueThing';

	const noFunc = () => {
		switch (isActive) {
			case 'BlueThing':
				isActive = 'RedThing';
				document.body.style.backgroundColor = "#19393e";
				break;
			case 'GreenThing':
				isActive = 'RedThing';
				document.body.style.backgroundColor = "#19393e";
				break;
			case 'RedThing':
				isActive = 'GreenThing';
        document.body.style.backgroundColor = "#5cbbca";
        break;
			default:
				break;
		}
	};
	
	const yesFunc = () => {
		switch (isActive) {
			case 'BlueThing':
				isActive = 'GreenThing';
				document.body.style.backgroundColor = "#5cbbca";
				break;
			case 'GreenThing':
				isActive = 'BlueThing';
				document.body.style.backgroundColor = "#0c1e21";
				break;
			case 'RedThing':
				isActive = 'BlueThing';
        document.body.style.backgroundColor = "#0c1e21";
        break;
			default:
				break;
		}
	};
</script>

<style>
	:root {
		--font-stack: 'Roboto', sans-serif;
		--dark-bg-color:  #0c1e21;
		--dark-text-color: #1c8c9e;
	}

	html {font-size: 100%;} /*16px*/

	body {
		/* background-color: white; */
		/* font-family: 'Poppins', sans-serif; */
		font-weight: 400;
		line-height: 1.65;
		/* color: #333; */
	}

	:global(html, body) {
		background-color: #0c1e21;
		color:  #1c8c9e;
		font-family: 'Poppins', sans-serif;
		font-weight: 400;
		margin: 0;
	}

	p {margin-bottom: 1.15rem;}

	h1, h2, h3, h4, h5 {
		margin: 2.75rem 0 1.05rem;
		font-family: 'Poppins', sans-serif;
		font-weight: 400;
		line-height: 1.15;
	}

	h1 {
		margin-top: 0;
		/* font-size: 4.209em; */
		/* font-size: 67.344px; */
		font-weight: 400!important;
	}

	h2 {font-size: 3.157em;}

	h3 {font-size: 2.369em;}

	h4 {font-size: 1.777em;}

	h5 {font-size: 1.333em;}

	small, .text_small {font-size: 0.75em;}

	html, body {
		background-color: var(--dark-bg-color);
		color: var(--dark-text-color);
		font-family: var(--font-stack);
		margin: 0;
	}

	.section-container {
		align-content: center;
	/*   border: 1px solid red; */
		display: flex;
		flex-direction: column;
		height: 100vh;
		justify-content: center;
	}

	.section-content {
		display: flex;
		flex-direction: column;
		justify-content: center;
		text-align: center;
	}

	button.btn {
		background: transparent;
		color: #fff;
		display: inline-block;
		border: 3px solid #fff;
		border-radius: 4px;
		font-size: 2.369em;
		margin: 25px;
		padding: 1rem;
		text-decoration: none;
		width: 300px;
	}

	button.btn:hover {
		background-color: rgba(255,255,255, .15);
		transition: all .3s ease-out;
	}
</style>

<section class="section-container">
  <div class="section-content">
  <h1 class="question">
		{#if isActive === 'BlueThing'}
			<BlueThing/>
		{:else if isActive === 'GreenThing'}
			<GreenThing/>
		{:else if isActive === 'RedThing'}
			<RedThing/>
		{/if}
	</h1>
    <div class="button-group">
			{#if isActive === 'BlueThing'}
				<button class="btn" on:click={yesFunc}>
					Yes
				</button>
				<button class="btn" on:click={noFunc}>
					No
				</button>
			{:else if isActive === 'GreenThing'}
				<button class="btn" on:click={yesFunc}>
					Continue
				</button>
			{:else if isActive === 'RedThing'}
				<button class="btn" on:click={yesFunc}>
					Very sure.
				</button>
				<button class="btn" on:click={noFunc}>
					I'll try again!
				</button>
			{/if}
    </div>
  </div>
</section>
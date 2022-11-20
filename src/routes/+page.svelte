<script lang="ts">
	import Card from '@smui/card';
	import Textfield from '@smui/textfield';
	import { goto } from '$app/navigation';

	import Button from '@smui/button';


	let firstName = '';
	let email= '';
	let show = false;

</script>

<main>
	
	<section>
		<Card padded>
			<h1>Welcome on the Yearbook app</h1>
			<h3>Connect to access 🤖</h3>
			<Textfield variant="outlined" bind:value={firstName} label="First Name">
			</Textfield>
			<br />
			<Textfield variant="outlined" input$maxlength={100} bind:value={email} label="email">
			</Textfield>
			<br />
				<label for="pw">Password</label>
				<div class="pw">
					<input id="pw" type={show ? "text" : "password"} placeholder="Enter your password "/> 
					<button id="eye" on:click|preventDefault={() => show = !show}>
						{#if show}
						<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="red">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13.875 18.825A10.05 10.05 0 0112 19c-4.478 0-8.268-2.943-9.543-7a9.97 9.97 0 011.563-3.029m5.858.908a3 3 0 114.243 4.243M9.878 9.878l4.242 4.242M9.88 9.88l-3.29-3.29m7.532 7.532l3.29 3.29M3 3l3.59 3.59m0 0A9.953 9.953 0 0112 5c4.478 0 8.268 2.943 9.543 7a10.025 10.025 0 01-4.132 5.411m0 0L21 21" />
						</svg>
						{:else}
						<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z" />
						</svg>
						{/if}
					</button>
				</div>
			<br />
			<Button on:click={() => goto('/yearbook')} >Connect</Button>

	</Card>
	</section>
</main>

<style>
	button svg {
		width: 20px;
		height: 0.75rem;
	}
	#eye {
		margin: -10px;
	}
</style>
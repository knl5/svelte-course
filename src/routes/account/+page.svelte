<script>
	import Card from '@smui/card';
	import Textfield from '@smui/textfield';
	import Button from '@smui/button';
	import { goto } from '$app/navigation';

	let firstName = 'Kanelle';
	let email= 'kanelle@test.com';
	let num= '0628000000';
</script>



<main>
	
	<section>
		<Card padded>
			<h1>My profil</h1>
			<h3>My informations</h3>

			<Textfield disabled variant="outlined" label="First Name" bind:value={firstName}>
			</Textfield>
			<br>
			<Textfield disabled variant="outlined" input$maxlength={100} bind:value={email} label="email">
			</Textfield>
			<br>
			<Textfield disabled type=number variant="outlined" input$maxlength={10} bind:value={num} label="number">
			</Textfield>


			<div style="display:flex; justify-content:space-between">
				<Button on:click={() => goto('/yearbook')}> Disconnect </Button>
			</div>
			
		</Card>
	</section>
</main>
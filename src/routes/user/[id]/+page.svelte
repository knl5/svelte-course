<script>
	import Button from '@smui/button';
	/** @type {import('./$types').PageData} */
	export let data;
	import Textfield from '@smui/textfield';
	
	import Card from '@smui/card';
	import CharacterCounter from '@smui/textfield/character-counter';
	import { goto } from '$app/navigation';

	let firstName = data.firstName;
	let email = data.email;
	let skills = data.skills;

	async function editUser() {
			const res = await fetch(`https://api.fake-rest.refine.dev/user/${data.id}`, {
					method: 'PATCH',
					headers: {
							'Content-Type': 'application/json'
					},
					body: JSON.stringify({
							firstName: firstName,
							email: email,
							skills: skills
					})
			}).then((res) => {
					res.json();
					goto('/yearbook');
			});
	}
</script>

<div class="card-display">
	<div class="card-container">
			<Card padded>
					<Textfield variant="outlined" bind:value={firstName} label="Edit FirstName">
									
							</Textfield>
							<br />
							<Textfield textarea input$maxlength={200} bind:value={email} label="Edit Email">
									<CharacterCounter slot="internalCounter">0 / 100</CharacterCounter>
							</Textfield>
							<br />
							<Textfield variant="outlined" bind:value={skills} label="Edit Skills">
								
							</Textfield>
							<br />
					<Button on:click={editUser}>Edit</Button>
			</Card>
	</div>
</div>
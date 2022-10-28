<script lang="ts">
	// @ts-nocheck
	import Dialog, { Title, Content, Actions } from '@smui/dialog';
	import Textfield from '@smui/textfield';
	import HelperText from '@smui/textfield/helper-text';
	import CharacterCounter from '@smui/textfield/character-counter';
	import Card from '@smui/card';
	import Button from '@smui/button';
	import { goto } from '$app/navigation';
	
	let firstName = '';
	let lastName = '';
	let email = '';
	let skills = '';
	
	export let open = false;

	async function createUser() {
    const res = await fetch(`https://api.fake-rest.refine.dev/users`, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            firstName,
						lastName,
            email,
						skills,
            createdAt: Date.now()
        })
    }).then((res) => {
            res.json();
            open = false;
						goto('/yearbook');
    });
}
	
	</script>
	<Dialog bind:open selection aria-labelledby="list-title" aria-describedby="list-content">
			<Title id="list-title">Create New User</Title>
			<Content id="mandatory-content">
					<Card padded>
							<Textfield variant="outlined" bind:value={firstName} label="firstName">
									<HelperText slot="FirstName">Helper Text</HelperText>
							</Textfield>
							<br />
							<Textfield variant="outlined" bind:value={lastName} label="lastName">
								<HelperText slot="LastName">Helper Text</HelperText>
							</Textfield>
							<br />
							<Textfield textarea input$maxlength={200} bind:value={email} label="email">
									<CharacterCounter slot="internalCounter">0 / 100</CharacterCounter>
							</Textfield>
							<br />
							<Textfield variant="outlined" bind:value={skills} label="skills">
								<HelperText slot="Skilles">Helper Text</HelperText>
							</Textfield>
							<br />
							<Button on:click={createUser}>Create</Button>
					</Card>
			</Content>
			<Actions>
					<Button action="accept">Close</Button>
			</Actions>
	</Dialog>
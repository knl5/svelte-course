<svelte:head>
	<title>Yearbook</title>
	<meta name="description" content="About this app" />
</svelte:head>

<script lang="ts">
  import { onMount } from 'svelte';
  import List from "./List.svelte";
	import Button from '@smui/button';
	import Dialog from './Popup.svelte';

  type User = {
    skills: string;
    image: any;
    content: string;
    name: string;
    id: number;
   };

    let items: User[] = [];
    let loaded = false;

    onMount(() => loadThings(false))

    function loadThings(wait: boolean) {
            if (typeof fetch !== 'undefined') {
                loaded = false;

                fetch('https://api.fake-rest.refine.dev/users')
                    .then((response) => response.json())
                    .then((json) =>
                        setTimeout(
                            () => {
                                items = json;
                                loaded = true;
                            },
                            wait ? 3000 : 0
                        )
                    );
            } 
						
    }

		let open = false;
</script>



<div style="display:flex; justify-content:space-between">
	<Button on:click={() => (open = true)}>Add New User</Button>
</div>
<List {items} {loaded}/>

<Dialog {open} />

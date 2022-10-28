<script lang="ts">
	import DataTable, { Head, Body, Row, Cell } from '@smui/data-table';
	import LinearProgress from '@smui/linear-progress';
	import Button from '@smui/button';

	export let items: any[] = []
	export let loaded = false

	async function deleteUser(id: number) {
    const res = await fetch(`https://api.fake-rest.refine.dev/users/${id}`, {
        method: 'DELETE'
    }).then((res) => {
        res.json();
        location.reload();
    });
}
</script>

<DataTable table$aria-label="User list" style="width: 100%;">
	<Head>
			<Row>
					<Cell numeric>ID</Cell>
					<Cell>Name</Cell>
					<Cell>Contact</Cell>
					<Cell>Image</Cell>
					<Cell>Skills</Cell>
					<Cell>Actions</Cell>
			</Row>
	</Head>
	<Body>
			{#each items as item (item.id)}
					<Row>
							<Cell numeric>{item.id}</Cell>
							<Cell><p>{item.firstName} {item.lastName}</p></Cell>
							<Cell>{item.email}</Cell>
							<Cell><img width="100" src={item.avatar?.[0]?.url} alt="" /></Cell>
							<Cell><strong>Development skills:</strong> {item.skills}</Cell>
							<Cell>
									<a href={`/user/${item.id}`}>Edit</a>
									<Button on:click={() => deleteUser(item.id)}>Delete</Button>
							</Cell>
					</Row>
			{/each}
	</Body>

	<LinearProgress
			indeterminate
			bind:closed={loaded}
			aria-label="Data is being loaded..."
			slot="progress"
	/>
</DataTable>
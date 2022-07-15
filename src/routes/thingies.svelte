<script>
    import { onMount } from 'svelte'

    let tasks = []
    const url = 'https://jsonplaceholder.typicode.com/todos/'

    onMount( async () => {
        fetch(url)
            .then( response => response.json() )
            .then( data => { tasks = data } )
    });
</script>

<table>
    <thead>
        <tr>
            <th>Task Id</th>
            <th>Task Name</th>
            <th>Status</th>
        </tr>
    </thead>

    {#each tasks as t}
        <tr>
            <td>{t.id}</td>
            <td>{t.title}</td>
            <td>{t.completed}</td>
        </tr>
    {/each}
</table>

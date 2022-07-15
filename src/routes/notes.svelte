<!-- load runs before the component is rendered -->
<script context="module">
  export const load = async ({ fetch }) => {
    const response = await fetch('http://localhost:8000/notes');
    const status = response.status;

    if (response.ok) {
      const items = await response.json();
      return {
        props: {
          items
        }
      };
    } else {
      const items = [];
      // throw new Error(response.status);
      return {
        props: {
          items,
          status
        }
      };
    }
  };
</script>

<!-- Per component script -->
<script>
  export let items;
  export let status;
</script>

<svelte:head>
  <title>Notes</title>
</svelte:head>

<div class="container">
  <h1>Notes</h1>
  {#if (status != 200)}
  <p>Status: {status}</p>
  {:else}
    {JSON.stringify(items[0])}
    <div class="items">
      <div class="items">
        <table border="border-collapse" role="grid">
          <thead>
            <th>details</th>
            <th><strong>email</strong></th>
            <th><strong>name</strong></th>
            <th><strong>surname</strong></th>
            <th><strong>deactivated</strong></th>
          </thead>
          <tbody>
              {#each items as item}
                <tr>
                  <td><a href={`/notes/${item.id}`}> view </a></td>
                  <!-- <td><a href={`/users/4`}> view </a></td> -->
                  <td>{item.email}</td>
                  <td>{item.name}</td>
                  <td>{item.surname}</td>
                  <td>{item.deactivated}</td>
                </tr>
              {/each}
          </tbody>
        </table>
      </div>
    </div>
  {/if}
</div>

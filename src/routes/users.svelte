<!-- load runs before the component is rendered -->
<script context="module">
  // export const load = async ({ fetch }) => {
  //   const res = await fetch('http://localhost:8000/users');
  //   const items = await res.json();
  //   return {
  //     props: {
  //       items
  //     }
  //   };
  // };

  // export const load = async ({ fetch }) => {
  //   const res = await fetch('http://localhost:8000/users');
  //   const items = (res.response == 200) ? await res.json() : [];
  //   return {
  //       props: {
  //         items
  //       }
  //     };
  // };

  export const load = async ({ fetch }) => {
    const response = await fetch('http://localhost:8000/users');
    const status = response.status;

    if (response.ok) {
      const items = await response.json();
      return {
        props: {
          items,
          status
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

  // import { onMount } from 'svelte'

  // let items = []
  // const url = 'http://localhost:8000/users'

  // onMount( async () => {
  //     fetch(url)
  //         .then( response => response.json() )
  //         .then( data => { items = data } )
  // });
</script>

<!-- src/routes/blog.svelte -->
<svelte:head>
  <title>Users</title>
</svelte:head>

<div class="container">
  <h1>Users</h1>
  {#if status != 200}
    <p>Status: {status}</p>
  {:else if items.length < 1}
    <p>No items found</p>
  {:else}
    <div class="items">
      <div class="items">
        <table border="border-collapse" role="grid" class="table-auto">
          <thead>
            <th><strong>details</strong></th>
            {#each Object.keys(items[0]) as key}
              <th><strong>{key}</strong></th>
            {/each}
          </thead>
          <tbody>
            {#each items as item}
              <tr>
                <td><a href={`/users/${item.id}`}> view </a></td>
                {#each Object.values(item) as val}
                  <td>{val}</td>
                {/each}
              </tr>
            {/each}
          </tbody>
        </table>
      </div>
    </div>
  {/if}
</div>

<style>
</style>

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
  <!-- <p>{items}</p> -->
  <h1>Users</h1>
  <div class="items">
    <div class="items">
      <table border="border-collapse" role="grid">
        <thead>
          <th><strong>details</strong></th>
          <th><strong>email</strong></th>
          <th><strong>name</strong></th>
          <th><strong>surname</strong></th>
          <th><strong>deactivated</strong></th>
        </thead>
        <tbody>
          {#if typeof items !== 'undefined'}
            {#each items as item}
              <tr>
                <td><a href={`/users/${item.id}`}> view </a></td>
                <!-- <td><a href={`/users/4`}> view </a></td> -->
                <td>{item.email}</td>
                <td>{item.name}</td>
                <td>{item.surname}</td>
                <td>{item.deactivated}</td>
              </tr>
            {/each}
          {/if}
        </tbody>
      </table>
    </div>
  </div>
</div>

<style>

</style>

<!-- src/routes/blog.svelte -->
<!-- load runs before the component is rendered -->
<script context="module">
    export const load = async ({ fetch }) => {
      const res = await fetch('http://localhost:8000/users');
      const items = await res.json();
      return {
        props: {
          items
        }
      };
    };
  </script>

  <!-- Per component script -->
  <script>
    export let items;
  </script>

  <!-- src/routes/blog.svelte -->
  <svelte:head>
    <title>Users</title>
  </svelte:head>

  <div class="container">
    <h1>Users</h1>
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
                  <!-- <td><a href={`/users/${item.id}`}> view </a></td> -->
                  <td><a href={`/users/4`}> view </a></td>
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
  </div>

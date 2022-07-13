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
    <title>Blog</title>
  </svelte:head>

  <div class="container">
    <h1>Users</h1>
    <div class="blogposts">
        <div class="item">
          <!-- <h2>{item.title.substring(0, 20)}</h2>
          <p>{item.body.substring(0, 80)}</p>
          <p class="readmore">
            <a style=" color: rgb(10, 10, 139);" href={`/blog/${post.id}`}> Read More </a>
          </p> -->

          <table border="border-collapse" role="grid">
            <thead>
              <th><strong>email</strong></th>
              <th><strong>name</strong></th>
              <th><strong>surname</strong></th>
              <th><strong>deactivated</strong></th>
            </thead>
            <tbody>
              {#each items as item}
                <tr>
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

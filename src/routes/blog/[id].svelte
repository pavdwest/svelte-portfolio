<script context="module">
  console.log("XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX")
  export const load = async ({ params, fetch }) => {
    // const res = await fetch(`https://jsonplaceholder.typicode.com/posts/${params.id}`);
    const res = await fetch(`http://localhost:8000/users/${params.id}`);

    const data = await res.json();

    console.log(data)
    return {
      props: {
        data
      }
    };
  };
</script>

<script>
    export let data;
</script>

<div class="container">
    <!-- <h1>{data.title}</h1>
    <p>{data.body}</p> -->


    <!-- Users -->
    <h1>{data.email}</h1>
    <p>{data.name}</p>

    <!-- Users -->
    <!-- <ul>
        {#each data as d}
            <li>{d.email}</li>
        {/each}
    </ul> -->
</div>

<style>
    .container {
        max-width: 900px;
        margin: 50px auto;
    }
</style>
Footer

<script context="module">
  export const load = async ({ params, fetch }) => {
    console.log(params.id);
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
    <!-- Users -->
    <h1>{data.email}</h1>
    <p>{data.name}</p>
</div>

<!-- <style>
    .container {
        max-width: 900px;
        margin: 50px auto;
    }
</style> -->
Footer

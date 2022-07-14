<script context="module">
  export const load = async ({ params, fetch }) => {
    console.log(params.id);
    const res = await fetch(`http://localhost:8000/notes/${params.id}`);
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
    <h1>{data.title}</h1>
    <p>{data.content}</p>
</div>

<!-- <style>
    .container {
        max-width: 900px;
        margin: 50px auto;
    }
</style> -->
Footer

<!-- src/routes/__layout.svelte -->
<nav>
  <ul>
    <li><a href="/" title="Back to Homepage">Gorbie Jarkensen</a></li>
  </ul>
  <ul>
    <li><a href="/about">About</a></li>
    <li><a href="/blog">Blog</a></li>
    <li><a href="/projects">Projects</a></li>
    <li><a href="/contact">Contact</a></li>
    <li><a href="/users">Users</a></li>
  </ul>
</nav>

<div class="container">
  <!-- Pages will be injected below -->
  <slot />
</div>

<style>
  /* .container {
    max-width: 1400px;
    margin: 25px auto;
  } */
</style>

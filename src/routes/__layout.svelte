<!-- src/routes/__layout.svelte -->

<nav>
  <ul>
    <li><a href="/" title="Back to Homepage">pureformance</a>
    <li><a href="/notes">notes</a></li>
    <li><a href="/projects">projects</a></li>
    <li><a href="/contact">contact</a></li>
    <li><a href="/users">users</a></li>
    <li><a href="/about">about</a></li>
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
  ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
  }

  li {
    float: left;
  }

  li a {
    display: block;
    padding: 8px;
  }
</style>

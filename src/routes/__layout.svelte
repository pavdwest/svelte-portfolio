<!-- src/routes/__layout.svelte -->

<nav>
  <ul>
    <li>
      <a href="/" title="Back to Homepage">pureformance</a>
      <!-- <a href="/">
        <i class="fa-solid fa-house"></i>
        <span>Gorbie Jarkensen</span>
      </a> -->
    </li>

  </ul>
  <ul class="flex border-b">
    <li><a href="/about">About</a></li>
    <li><a href="/notes">Notes</a></li>
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
  ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
  }

  li {
    float: right;
  }

  li a {
    display: block;
    padding: 8px;
  }
</style>

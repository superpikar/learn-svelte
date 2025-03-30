<script>
  import { Link } from "svelte5-router";
  let {
    url
  } = $props();

  let menus = $state([
    { link: '/', label: '🏠 Home' },
    { link: '/articles', label: '📃 Articles' },
    { link: '/about', label: '👤 About' },
  ])
</script>

<nav class="uk-navbar-container mt-10" uk-navbar>
  <div class="uk-navbar-left">
    <ul class="uk-navbar-nav flex">
      {#each menus as item }
        <li>
          <Link class="{['uk-btn uk-btn-default', item.link===url ? 'uk-active' : '']}" to="{item.link}">{item.label}</Link>
        </li>
      {/each}
    </ul>
  </div>
</nav>
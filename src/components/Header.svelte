<script lang="ts">
	import {Router, links } from "svelte-routing";
</script>

  
<nav class="navbar is-primary">
  <div class="navbar-brand">
    <a class="navbar-item" href="http://www.info.univ-tours.fr/diblois/">
      <img src="https://univ-tours.fr/jsp/images/logo.svg" alt="University of Tours" width="112" height="28">
    </a>
    <div class="navbar-burger" data-target="navbarExample">
      <span></span>
      <span></span>
    </div>
  </div>

  <Router >
    <div use:links id="navbarExample" class="navbar-menu">
      <div class="navbar-start">
        <a class="navbar-item" href="/">
          Home
        </a>
        <a class="navbar-item" href="azure">
          Server
        </a>
      </div>
    </div>
  </Router>
</nav>
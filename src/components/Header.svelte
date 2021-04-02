<script lang="ts">
	import {Router, links } from "svelte-routing";

  let isOpened = '';
  let navElements = document.getElementsByClassName('navbar-menu');

  function open(){
    if(isOpened == ''){
      isOpened = 'is-active';
    } else {
      isOpened = '';
    }
  }
</script>

  
<nav class="navbar is-primary">
  <div class="navbar-brand">
    <a class="navbar-item" href="http://www.info.univ-tours.fr/diblois/">
      <img src="https://univ-tours.fr/jsp/images/logo.svg" alt="University of Tours" width="112" height="28">
    </a>
    <div class="navbar-burger" data-target="navbarElements" on:click={open}>
      <span></span>
      <span></span>
    </div>
  </div>

  <div id="navbarElements" class="navbar-menu {isOpened}">
  <Router >
      <div use:links class="navbar-start is-active">
        <a class="navbar-item" href="/">
          Home
        </a>
        <a class="navbar-item" href="azure">
          Server
        </a>
      </div>
  </Router>
  </div>
</nav>
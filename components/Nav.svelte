<script>
  import { onMount, setContext } from "svelte";
  import { writable } from "svelte/store";
  import Icon from "./Icon.svelte";

  export let segment;
  export let page;
  export let logo;

  const current = writable(null);
  setContext("nav", current);

  let open = false;
  let visible = true;

  // hide nav whenever we navigate
  page.subscribe(() => {
    open = false;
  });

  function intercept_touchstart(event) {
    if (!open) {
      event.preventDefault();
      event.stopPropagation();
      open = true;
    }
  }

  // Prevents navbar to show/hide when clicking in docs sidebar
  let hash_changed = false;
  function handle_hashchange() {
    hash_changed = true;
  }

  let last_scroll = 0;
  function handle_scroll() {
    const scroll = window.pageYOffset;
    if (!hash_changed) {
      visible = scroll < 50 || scroll < last_scroll;
    }

    last_scroll = scroll;
    hash_changed = false;
  }

  $: $current = segment;
</script>

<style>

a {
	text-decoration: none;
	cursor: pointer;
	color: #ffffff;
}
</style>

<svelte:window on:hashchange={handle_hashchange} on:scroll={handle_scroll} />

<nav class="navbar navbar-expand-lg navbar-dark bg-primary">
  <a class="navbar-brand" href="/">Crostini Snacks</a>
  <button
    class="navbar-toggler"
    type="button"
    data-toggle="collapse"
    data-target="#navbarNav"
    aria-controls="navbarNav"
    aria-expanded="false"
    aria-label="Toggle navigation">
    <span class="navbar-toggler-icon" />
  </button>
  <div class="collapse navbar-collapse" id="navbarNav">
    <ul class="navbar-nav">
	<slot></slot>
    </ul>
  </div>
</nav>

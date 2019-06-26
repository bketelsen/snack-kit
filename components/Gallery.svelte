<script>
  import Card from "./Card.svelte";
  export let sections;
  export let base;
</script>

<style>

</style>

<div class="container-fluid">
  <div class="row">
    {#each sections as section}
      <div class="col-6 col-md-4 col-lg-3 my-4">
        <Card
          image="logo-192.png"
          target="/{base}/{section.slug}"
          title={section.metadata.title}
          content={section.metadata.description} />
      </div>
    {/each}
  </div>
</div>

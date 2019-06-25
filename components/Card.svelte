<script>
  export let title;
  export let content;
  export let image;
  export let target;
</script>

<style>
  
</style>

<div class="card p-3">
  <img src="{image}" class="card-img-top" alt="{title}">
  <div class="card-body">
    <h5 class="card-title">{title}</h5>
    <p class="card-text">{content}</p>
    <a href="{target}" class="btn btn-primary">View</a>
  </div>
</div>
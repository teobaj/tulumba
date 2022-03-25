<script lang="ts">

  function dispatch(){
    window.postMessage({type: 'transform'}, "*")
  }

</script>

<div class="topbar">
  <span>
    Response to TS interface
  </span>
  <button on:click={dispatch}>
    Transform
  </button>
</div>

<style>
.topbar {
  grid-column: 1/3;
  background-color: var(--bg-color, '#f3f');
  height:40px;
  border: 1px solid var(--tertiary-color);
  border-left: none;
  display: flex;
  padding: 0.5rem 1rem;
  justify-content: space-between;
  align-items: center;
  font-weight: 700;
  color: var(--primary-color)
}
button {
  padding: 8px 12px;
  border: none;
  border-radius: 4px;
  font-weight: 700;
  color: #fff;
  background-color: var(--primary-color)
}
</style>

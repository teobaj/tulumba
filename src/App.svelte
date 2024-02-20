<script lang="ts">
import JsonInput from "./lib/JsonInput.svelte";
import ResultInterface from "./lib/ResultInterface.svelte";
import SideBar from "./lib/SideBar.svelte";
import TopBar from "./lib/TopBar.svelte";

</script>


<main>
    <TopBar/>
    <JsonInput/>
    <ResultInterface/>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    --bg-color: #2E3047;
    --primary-color: #3bba9c;
    --secundary-color: #707793;
    --tertiary-color:#43455c;
    --code-bg-color: #1E2936;
  }
  main {
    height: 100vh;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: auto 1fr;
  }


</style>

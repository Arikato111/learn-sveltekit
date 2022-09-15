<script>
  let code = '@ <br> <div align="left">hello world</div>';
  let styleArea = code.length > 50 ? "get-light": "";
</script>

<svelte:head>
  <title>input code</title>
  <meta name="description" content="display html code on html code" />
</svelte:head>

<div>
  <textarea
    class="w-full p-2 focus:outline-none rounded {styleArea}"
    placeholder="input html code"
    rows="10"
    bind:value={code}
    on:keyup={()=> (styleArea = code.length > 50? "get-light": "")}
  />
  <div class="p-3 my-3 rounded bg-white">
    {#if code[0] && code[0] === "@"}
      <span>{@html code}</span>
    {:else}
      {#each code as c}
        <span>{c}</span>
      {/each}
    {/if}
  </div>
</div>

<style>
  .get-light {
    box-shadow: 0 0 10px 5px #f5f5f5;
    /* box-shadow: none; */
    /* border: px solid gray; */
    /* transform: translate(0, 10px); */
    transition: 0.2s;
  }
</style>

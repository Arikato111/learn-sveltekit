<script>
  let code = "@ <br> <div align=\"left\">hello world</div>";
</script>

<svelte:head>
    <title>input code</title>
    <meta name="description" content="display html code on html code">
</svelte:head>

<div>
  <textarea
    class="w-full p-2 focus:outline-none rounded"
    placeholder="input html code"
    rows="10"
    bind:value={code}
  ></textarea>
  <div class="p-3 my-3 rounded bg-white">
    {#if code[0] && code[0] ==='@'}
    <span>{@html code}</span>
    {:else}
    {#each code as c}
    <span>{c}</span>
    {/each}
    {/if}
  </div>
</div>

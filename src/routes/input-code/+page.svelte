<script>
  let code = "@ <br> <div align=\"left\">hello world</div>";
  addEventListener("keydown", function (e) {
    if (e.ctrlKey && e.key == "k") {
      /* Do whatever */
      console.log(e);
      // @ts-ignore
      window.document.getElementById("input").focus();
      e.preventDefault();
    }
  });
</script>

<div>
  <textarea
    id="input"
    placeholder="Ctrl + k to focus"
    class="w-full p-2 focus:outline-none rounded"
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

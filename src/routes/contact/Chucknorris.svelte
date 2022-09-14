<script>
  import axios from "axios";
  let data = "";
  async function fetchApi() {
    data = "loading...";
    axios.get("https://api.chucknorris.io/jokes/random").then((res) => {
      data = res.data.value ?? "can't send api";
    }).catch(err => {
        data = "loading failed"
    });
  }
  fetchApi();
</script>

<div class="text-center m-3">
  <button class="p-2 border-2 rounded bg-blue-300 text-white shadow-slate-600 shadow-md active:translate-y-1 transition-all active:shadow-none" on:click={fetchApi}>Refresh</button>
  <div class="m-3 text-lg text-slate-600">{data}</div>
</div>

<style>
</style>

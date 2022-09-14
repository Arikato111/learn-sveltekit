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

<div class="box">
  <div class="content">{data}</div>
  <button on:click={fetchApi}>Refresh</button>
</div>

<style>
  .box {
    text-align: center;
    background-color: #f2f2f2;
    padding: 7px;
    border-radius: 4px;
  }
  .content {
    margin: 10px;
  }
  button {
    padding: 7px;
    /* border: 1px solid gray; */
    border: none;
    border-radius: 4px;
    box-shadow: 0 2px 3px 1px gray;
    transition: .2s;
}
button:active {
    box-shadow: none;
    transform: translate(0, 4px);
    transition: .2s;
  }
</style>

<script>
  import Navbar from "./lib/Navbar.svelte";
	import { Router, Link, Route } from "svelte-navigator";
  import Comments from "./pages/Comments.svelte";

  let todoValue = "";

  let item = [];
  let newItemForStorage = [];

  function addToList() {
    item = [...item, todoValue];
    localStorage.setItem("todo", JSON.stringify(item));
    todoValue = "";
  }

  function getData() {
    newItemForStorage = JSON.parse(localStorage.getItem("todo"));
    item = [...newItemForStorage];
  }
</script>

<Router>
<Navbar/>


<Route path="/">
  <div class="centered">

    <button class="width" on:click={getData}>Get Data from storage</button> <br/>
    <input class="mt-2" type="text" bind:value={todoValue} />
    <input type="submit" on:click={addToList} />
  
    <div class="data">
      {#if item == null || item == []}
        {#each newItemForStorage as item}
          <li>{item}</li>
        {/each}
      {:else if item != null}
        {#each item as menu}
          <li>{menu}</li>
        {/each}
      {/if}
    </div>
  </div>
  
</Route>
<Route path="comment">
  <Comments/>
</Route>
</Router>

<style>

.centered {
  text-align: center;
}

.mt-2 {
  margin-top: 5rem;
}
.data {
  font-size: 28px;
    margin-top: 50px;
  }
</style>

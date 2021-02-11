<script>
  let search = 'enter your joke';
  let jokes = [];
  $: getData();

  async function getData() {
  let response  = await fetch('https://api.chucknorris.io/jokes/search?query=' + search);
  if(response.status === 200){
  var result = await response.json();
  jokes = result.result;
  }
  }
</script>

<svelte:head>
  <title>Jokes</title>
</svelte:head>

<div class="auth-page">

  <div class="container page">
    <div class="row">
      <input bind:value={search} on:input="{() =>
       getData() }" placeholder="enter your joke">
    </div>
      <div class="row">
        {#each jokes as joke}
        <div>{joke.value}</div>
        {/each}
      </div>
    </div>
</div>
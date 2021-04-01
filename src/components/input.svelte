<script>


    import Movie from './Movie.svelte'


  let inputValue = "";
  let apiResponse = [];

  function handleInput(e) {
    inputValue = e.target.value;
  }

  $: if (inputValue.length > 2) {
    fetch(`http://www.omdbapi.com/?s=${inputValue}&apikey=dad81ac`)
      .then((res) => res.json())
      .then((res) => {
        apiResponse = res.Search || [];
      });
  }

  
</script>

<div class="col-md-12 my-5">
  <input
    type="text"
    placeholder="Search movies here"
    value={inputValue}
    on:input={handleInput}
  />

  {#if apiResponse.length > 0}
    Tenemos {apiResponse.length} Peliculas
  {:else}
    No tenemos Peliculas
  {/if}
  
</div>

<div class="row">
    {#await apiResponse}
        <strong>Loading...</strong>
    {:then movies}
    {#each movies as { Title, Poster, Year }}
        <Movie 
            Title =  {Title}
            Poster = {Poster}
            Year = {Year}
        />
        {:else}
        <strong>No hay resultados</strong>
    {/each}
    {/await}
</div>

<script>
    export let Title, Poster, Year

</script>

<div class="col-md-4 my-2">
    <div class="card" style="width: 18rem;">
      <img src={Poster} class="card-img-top" alt={Title} />
      <div class="card-body">
        <h5 class="card-title">{Title}</h5>
        <p class="card-text">
          {Year}
        </p>
      </div>
    </div>
  </div>
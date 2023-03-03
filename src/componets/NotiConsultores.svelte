<script>
    import { onMount } from "svelte";
    import { apiData, drinkNames } from './store.js';
    
    onMount(async () => {
      fetch("https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Bourbon")
      .then(response => response.json())
      .then(data => {
            console.log(data);
        apiData.set(data);
      }).catch(error => {
        console.log(error);
        return [];
      });
    });
</script>

<div class="card">
    <h2>NotiConsultores</h2>
    <h5 style="text-align: right;"><a href="test">Visitar</a></h5>
    <img src="/img/just_products.jpg" alt="Avatar" style="width:100%">
    <h4><b>Periodo 6 | Semana 21 a 24</b></h4>
    <p>Del 1 de enero al 28 de enero </p>
    <button type="button">Compartir a consultora</button>
    
    <h1>Whiskey Drinks Menu</h1>
	<ul>
	{#each $drinkNames as drinkName}
		<li>{drinkName}</li>
	{/each}
	</ul>
  </div>


<style>
    .card {
        margin: auto;
        width: 50%;
        padding: 10px;
        background: #fff;
        padding: 20px;
        box-shadow: 0 3px 10px rgb(0 0 0 / 0.2);
        border-radius: 6px;
    }
    .center {
        margin: auto;
        width: 50%;
        border: 3px solid green;
        padding: 10px;
    }
</style>

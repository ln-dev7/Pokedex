<script>
  import BarreRecherche from "./BarreRecherche.svelte";
  import Carte from "./Carte.svelte";
  import { v4 as uuidv4 } from "uuid";

  let allPokemon = [];
  let tableauFin = [];

  function fetchPokemonBase() {
    fetch("https://pokeapi.co/api/v2/pokemon/?limit=301")
      .then((reponse) => reponse.json())
      .then((allPoke) => {
        allPoke.results.forEach((pokemon) => {
          fetchPokemonComplet(pokemon);
        });
      });
  }
  fetchPokemonBase();

  function fetchPokemonComplet(pokemon) {
    let objPokemonFull = {};
    let url = pokemon.url;
    let nameP = pokemon.name;

    fetch(url)
      .then((reponse) => reponse.json())
      .then(function (pokeData) {
        objPokemonFull.pic = pokeData.sprites.back_default;
      });

    fetch(`https://pokeapi.co/api/v2/pokemon-species/${nameP}/`)
      .then((reponse) => reponse.json())
      .then(function (pokeData) {
        objPokemonFull.name = pokeData.names[4].name;
        allPokemon.push(objPokemonFull);
      })
      .then(() => {
        tableauFin = allPokemon.slice(0, 50);
        allPokemon = allPokemon;
      });
  }

  function goRecherche(e) {
    let contenuRecherche = e.detail.txt;
    tableauFin = allPokemon.filter(el=> el.name.includes(contenuRecherche));
  }
</script>

<BarreRecherche on:recherche-poke={goRecherche} on:tout-poke={goRecherche} />
<div class="contenu">
  {#each tableauFin as pokemon (uuidv4())}
    <Carte name={pokemon.name} pic={pokemon.pic} />
  {/each}
</div>

<style>
  /* #2c6cb5
    #ffcc01 */
  .contenu {
    max-width: 1400px;
    width: 95%;
    padding: 0 50px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
</style>

<script>
  import "./global.css";
  import "./extraStyling/style.css"
  import { Route, Router } from "svelte-navigator";
  import Navbar from "./components/Navbar.svelte";
  import PokemonGrid from "./components/PokemonGrid.svelte";
  import Pokemon from "./components/Pokemon.svelte";
  import Meow from "./components/meow.svelte";

  let offset = 0;

  let limit = 151;

  let searchValue = "";

  let selectedType = "All types";
</script>

<Navbar bind:searchValue bind:offset bind:limit bind:selectedType />
<main class="p-4">
  <Router>
    <Meow />
    <Route to="/">
      <PokemonGrid {offset} {limit} {searchValue} {selectedType}/></Route
    >
    <Route path="/:name" let:params>
      <div class="flex flex-col items-center">
      <Pokemon name={params.name} />
    </div>
    </Route>
  </Router>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  }
</style>

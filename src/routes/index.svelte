<script context="module">
  export async function load({fetch}){
    const res = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=${import.meta.env.VITE_API}`);
    const data = await res.json();
      if(res.ok){
        return{
          props:{ popular: data.results }
    };
  }
}
</script>

<script>

  import PopularMovies from '../components/PopularMovies.svelte';
  import SearchMovies from '../components/SearchMovies.svelte';
  export let popular;
  import { fly } from 'svelte/transition'
</script>


<section transition:fly="{{ duration: 500}}" >
  <SearchMovies />
  <PopularMovies {popular}/>
</section>

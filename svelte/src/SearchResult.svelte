<script>
    import SearchResultMatch from './SearchResultMatch.svelte';

    export let result;
</script>

<h4>{ result.episode.title }</h4>
{#each result.matches as m}
    <SearchResultMatch result={result} match={m} />
{/each}

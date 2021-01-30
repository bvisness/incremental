<script>
    import SearchResult from './SearchResult.svelte';

    let query = '';
    $: [results, summary] = runSearch(query);
</script>

<input bind:value={query}>
<div>
    {#each results as r}
        <div>
            <SearchResult result={r} />
        </div>
    {/each}
</div>

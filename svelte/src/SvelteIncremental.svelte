<script>
    import { afterUpdate } from 'svelte';
    import SearchResult from './SearchResult.svelte';

    let query = '';
    let results = [];
    let maxIndex = 0;

    let lastQuery = query;
    let renderHandle = null;
    $: if (query !== lastQuery) {
        lastQuery = query;
        maxIndex = MAX_INCREMENTAL;

        clearTimeout(renderHandle);
        results = runSearch(query)[0];
    }

    afterUpdate(() => {
        if (maxIndex < results.length) {
            renderHandle = setTimeout(() => {
                maxIndex += MAX_INCREMENTAL;
            }, 0);
        } else {
            console.log('done with incremental render');
        }
    });

    $: resultSlice = results.slice(0, Math.min(maxIndex, results.length));
</script>

<input bind:value={query}>
<div>
    {#each resultSlice as r (r.episode.day)}
        <div>
            <SearchResult result={r} />
        </div>
    {/each}
</div>

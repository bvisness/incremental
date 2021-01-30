<script>
    export let result;
    export let match;

    let pieces = [];

    $: {
        pieces = [];

        let startIndex = 0;
        for (const highlightMatch of match.text.matchAll(result.query)) {
            pieces.push(match.text.slice(startIndex, highlightMatch.index));
            pieces.push(highlightMatch[0]);

            startIndex = highlightMatch.index + highlightMatch[0].length;
        }
        pieces.push(match.text.slice(startIndex));
    }
</script>

<p>
    {match.prettyTime}
    {#each pieces as piece, i}
        {#if i % 2 === 0}
            {piece}
        {:else}
            <span class="highlight">{piece}</span>
        {/if}
    {/each}
</p>

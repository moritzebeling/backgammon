<script>
    
    import Stone from "./Stone.svelte";
    import Field from "./Field.svelte";

    const columns = 12;
    const rows = 2;

    const stonesPerField = {
        0:  [0,0,0,0,0],
        11: [0,0],
        16: [0,0,0],
        18: [0,0,0,0,0],
        4:  [1,1,1],
        6:  [1,1,1,1,1],
        12: [1,1,1,1,1],
        23: [1,1]
    };

    const fields = [];

    for (let f = 0; f < (columns*rows); f++) {
        let row = Math.floor( f / columns );
        let col = f % columns;
        let stones = stonesPerField[f] || [];
        fields.push({
            field: f,
            row,
            col,
            stones,
            half: Math.floor( col / (columns/2) )
        });
    }

</script>
    
<main>
    {#each fields as field}
        <Field {...field}>
            <svelte:fragment slot="stones" let:stones>
                {#each stones as stone}
                    <Stone player={stone} />
                {/each}
            </svelte:fragment>
        </Field>
    {/each}
</main>

<style style="scss">

    main {
        position: fixed;
        top: 0;
        left: 0; 
        width: 100vw;
        height: 100vh;
        display: grid;
        grid-template-columns: repeat(12, 1fr);
        grid-template-rows: repeat(2, 1fr);
    }

</style>
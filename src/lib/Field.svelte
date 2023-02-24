<script>
    
    export let field;
    export let row;
    export let col;
    export let stones;
    export let half;

    console.log( field, stones );

</script>
    
<div class="field-{field} row-{row} col-{col} half-{half}">

    <slot name="stones" {stones} />

    <svg width="1200" height="1200" viewBox="0 0 1200 1200" preserveAspectRatio="none" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M600.006 1200L-0.000159643 5.45669e-06L1200 2.00272e-05L600.006 1200Z" fill="var(--color)"/>
    </svg>

</div>

<style style="scss">

    div {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: start;
        position: relative;
    }
    .half-0 {
        background-color: black;
        --color: white;
    }
    .half-1 {
        background-color: white;
        --color: black;
    }
    .row-1 {
        flex-direction: column-reverse;
        justify-content: end;
    }

    svg {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }
    .row-1 svg {
        transform: rotate(180deg);
    }

</style>
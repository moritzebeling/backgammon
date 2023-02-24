<script>
    
    import { onMount } from "svelte";

    export let player;
    
    let fixed = false;
    let stone;

    function fix(){
        let rect = stone.getBoundingClientRect();
        stone.style.top = (rect.top + (rect.height/2) ) + 'px';
        stone.style.left = (rect.left + (rect.width/2) ) + 'px';
        fixed = true;
    }

    function grab(){
        if( !fixed ){ fix(); }
        window.addEventListener('pointermove',move);
        window.addEventListener('pointerup',release);
    }

    function move( event ){
        stone.style.top = event.clientY + 'px';
        stone.style.left = event.clientX + 'px';
    }

    function release(){
        window.removeEventListener('pointermove',move);
        window.removeEventListener('pointerup',release);
    }

</script>

<div class="player-{player}" class:fixed bind:this={stone}
    on:pointerdown={grab}
></div>

<style>

    div {
        width: 5vw;
        height: 5vw;
        border-radius: 50%;
        z-index: 10;
        cursor: pointer;
    }
    
    div.fixed {
        position: fixed;
        transform: translate(-50%,-50%);
    }

    div.player-0 {
        background: #f00;
    }
    div.player-1 {
        background: #00f;
    }

</style>
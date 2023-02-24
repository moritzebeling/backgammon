<script>

    export let player;

</script>

<div class="player-{player}"></div>

<style>

    div {
        width: 5vw;
        height: 5vw;
        border-radius: 50%;
        z-index: 10;
    }
    
    div.fixed {
        position: fixed;
    }

    div.player-0 {
        background: #f00;
    }
    div.player-1 {
        background: #00f;
    }

</style>
<script>
    export let name;
    export let pic;
</script>

<div class="carte">
    <p class="nom">{name}</p>
    <img src={pic} alt="pokemon">
</div>

<style>
    .carte{
        width: 300px;
        height: 200px;
        border: 1px solid #ffcc01;
        background: rgba(44, 108, 181, 0.1);
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        margin: 5px;
        cursor: pointer;
    }

    .carte img{
        width: 100px;
    }

    .carte p{
        font-size: 25px;
    }
</style>
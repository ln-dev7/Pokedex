<script>

</script>

<form class="form-recherche">
    <label for="recherche">Chercher un Pokemeon</label>
    <input type="text" id="recherche" placeholder="Entrer son nom">
    <button type="submit">Rechercher</button>
</form>

<style>
    .form-recherche{
        margin: 100px auto 50px auto;
        max-width: 1100px;
        width: 100%;
        padding: 0 50px;
        display: flex;
        flex-direction: column;
    }
    .form-recherche, .form-recherche label{
        max-width: 1100px;
        width: 100%;
    }
    .form-recherche label{
        font-size: 25px;
        border: none;
        padding: 10px 0;
    }
     .form-recherche input{
        font-size: 20px;
        padding: 10px;
    }
    .form-recherche button{
        cursor: pointer;
        margin-top: 5px;
        padding: 10px 20px;
        background: #ffcc01;
        border: none;
        color: #333;
        font-size: 18px;
        margin-right: auto;
    }
</style>
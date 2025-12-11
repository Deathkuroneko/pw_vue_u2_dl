<template>
    <div>
        <img src="https://yesno.wtf/assets/yes/5-64c2804cc48057b94fd0b3eaf323d92c.gif" alt="No se peude">
        <br>
        <div class="pregunta-container">

            <input type="text" placeholder="Hazme una pregunta">

            
            <p>Recuerda terminar con una interrogacion</p>

            <h2 id="titulo">¿Sere millonario?</h2>
            <h1>Yes, No</h1>
        </div>

    </div>
</template>

<script>
export default{

}
</script>

<style>

/*div {
    display: row;
    justify-content: center;
    justify-items: center;
}*/
img{
    height: 100hv;
    width: 100vw;
    max-height: 100%;
    max-width: 100%;
    position: fixed;
    left: 0px;
    top: 0px;

}

.pregunta-container {
    position: relative;
    color: aliceblue;
    min-height: 100vh; /* altura de toda la pantalla */
    display: flex;
    flex-direction: column; /* elementos uno debajo del otro */
    justify-content: center; /* centrado vertical */
    align-items: center; /* centrado horizontal */
    text-align: center;
}
input{
    width: 250px;
    padding: 10px 15px;
    border-radius: 5px;
    border: none;
}
input:focus{
    outline: none;
}

h1,h2,p{
    color: aliceblue;
}

p{
    font-size: 20px;
}

h2{
    margin-top: 150px;
}
</style>

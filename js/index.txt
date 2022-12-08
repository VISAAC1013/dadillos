
var adivinaBtn = document.getElementById("adivinarBtn");


function isRange1_6  ( valor ){

    if ( valor >= 1 &&  valor <= 6 )
        return true;
    else
        return false;
}

function getRandomNumber (){
    //  regresa un numero entre 1 y 6
    var randNum = (Math.random()*100)%6 + 1; // 0 y 1 
    randNum = parseInt( randNum, 10);
    return randNum;
}



adivinaBtn.addEventListener( "click" , () => {

    document.getElementById("parrafo_fin").innerHTML = "";

    var valor = document.getElementById("guessNumber").value;

    valor = parseInt( valor, 10 );

    if ( isNaN( valor )  ){
        document.getElementById("parrafo_fin").innerHTML = "<h2> ¡El valor introducido no es valido!</h2>"
    }


    if ( isRange1_6( valor ) ){

        var randNum = getRandomNumber();

        if ( randNum == valor )
            document.getElementById("parrafo_fin").innerHTML = "<h2> ¡Adivinaste el numero!</h2>"    
        else
            document.getElementById("parrafo_fin").innerHTML = "<h2> ¡No adivinaste, intenta de nuevo!</h2>"    

        var ruta_random = "imagenes/dice"+randNum+".png";
        var ruta_usuario = "imagenes/dice"+valor+".png";

        var img_random = document.getElementById("img_random");
        img_random.setAttribute( "src",ruta_random );


        var img_usuario = document.getElementById("img_usuario");
        img_usuario.setAttribute( "src",ruta_usuario );


    } else{
        document.getElementById("parrafo_fin").innerHTML = "<h2> ¡El valor introducido esta fuera de rango!</h2>"
    }
    
});
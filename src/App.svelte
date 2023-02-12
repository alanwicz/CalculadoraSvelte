<script>

  let number = 0;
  let number1 = 0;
  let number2 = 0;
  let numberOptional = 0;
  let numberOptional2 = 0;
  let operacion = 0;
  let contador = 0;
  let visor1 = 0;
  let visor2 = 0;
  let resultado;
  let controlComa = 0;
  let Saver = [];
  let operacion2;

  function handleClick(id) {
    number = id;
    if (number1 <= 0 && number1 <= 9 && contador === 0) {
      if (number1 === 0 && controlComa === 1) {
        number1 = "0." + number;
        number1 = Number(number1);
        numberOptional = String(number1);
        visor1 = number1;
      } else {
        number1 = number;
        numberOptional = String(number1);
        visor1 = number1;
      }
    } else if (number1 <= 99 && contador === 0) {
      if (number1 > 0 && controlComa === 1) {
        number1 = number1 + "." + number;
        number1 = Number(number1);
        numberOptional = String(number1);

        visor1 = number1;
      } else {
        number1 = number1 + "" + number;
        number1 = Number(number1);
      }
     
      visor1 = number1;
    } else if (number2 <= 0 && contador === 1) {
      if (number2 === 0 && controlComa === 1) {
        number2 = "0." + number;
        number2 = Number(number2);
        numberOptional = String(number2);
        visor1 = number2;
        visor2 = number1 + " " + operacion + " ";
        numberOptional2 = number2;
      } else {
        number2 = number;
        visor1 = number2;
        visor2 = number1 + " " + operacion + " ";
        numberOptional2 = number2;
        numberOptional = String(number2);
      }
    } else if (number2 <= 99 && contador === 1) {
      if (controlComa === 1) {
        number2 = number2 + "." + number;
        number2 = Number(number2);
        numberOptional = String(number1);
        numberOptional2 = number2;
        visor1 = number2;
      } else {
        number2 = number2 + "" + number;
        number2 = Number(number2);
        visor1 = number2;
      }
    }
    controlComa = 0;
  }

  function Coma(id) {

    if (number1 <= 0 && number2 === 0 && contador === 0) {
      visor1 = "0.";
    } else if (number1 > 0 && number2 === 0 && contador === 0) {
      visor1 = number1 + ".";
      controlComa = 1;
    } else if (number1 > 0 && number2 === 0 && contador === 1) {
      visor1 = "0.";
      visor2 = number1 + " " + operacion;
      controlComa = 1;
    } else {
      visor1 = number2 + ".";
      visor2 = number1 + " " + operacion;
      controlComa = 1;
    }
  }

  function operation(id) {
    operacion = id;
    contador = 1;
    visor1 = operacion;
    visor2 = number1;
  }

  function operationPorcentaje(id) {
    number2 = (number2 * number1) / 100;
  }

  let contador2 = 0;

  function operationMasMenos(id) {
    if (contador === 0) {
      number1 = number1 * -1;
      visor1 = number1;
    } else {
      number2 = number2 * -1;
      visor1 = number2;
    }
  }
  





  let iders = 0;
  let SJ;
  function Results() {
    if (operacion === "+") {
      resultado = number1 + number2;
      visor2 = number1 + " " + operacion + " " + number2;
      operacion2 = visor2 + " = ";
    } else if (operacion === "-") {
      resultado = number1 - number2;
      visor2 = number1 + " " + operacion + " " + number2;
      operacion2 = visor2 + " = " + resultado;
    } else if (operacion === "*") {
      resultado = number1 * number2;
      visor2 = number1 + " " + operacion + " " + number2;
      operacion2 = visor2 + " = " + resultado;
    } else if (operacion === "/") {
      resultado = number1 / number2;
      operacion2 = visor2 + " = " + resultado;
    }
    visor1 = resultado;
    number1 = 0;
    number2 = 0;
    iders = iders + 1;
    Saver.push({
      id: iders,
      fecha: "1",
      operacion: operacion2,
      resultado: resultado,
    });

    console.log(Saver);
    SJ = JSON.stringify(Saver);
    console.log(SJ);
	saveData();

    let number = 0;
    number1 = 0;
    number2 = 0;
    numberOptional = 0;
    numberOptional2 = 0;
    operacion = 0;
    contador = 0;
    resultado;
    controlComa = 0;
    operacion2 = 0;
  }


const json = Saver;


function saveData() {
    localStorage.setItem('data', JSON.stringify(json));
    console.log('Data saved.');
	console.log(json)
  }





  function Reset(id) {
    number1 = 0;
    number2 = 0;
    visor1 = 0;
    visor2 = 0;
    contador = 0;
    contador2 = 0;
    operacion = 0;
    controlComa = 0;
  }

  function Return(id) {
    if (
      number1 > 0 &&
      number1 <= 9 &&
      number2 === 0 &&
      operacion === 0 &&
      contador === 0
    ) {
      number1 = 0;
      visor1 = 0;
    } else if (
      number1 > 9 &&
      number2 === 0 &&
      operacion === 0 &&
      contador === 0
    ) {
      number1 = numberOptional;
      visor1 = number1;
    }

    if (number1 > 0 && number2 === 0 && contador === 1) {
      contador = 0;
      operacion = 0;
      visor1 = number1;
      visor2 = 0;
    } else if (number1 > 9 && number2 <= 9 && contador === 1) {
      visor1 = operacion;
      visor2 = number1;
      number2 = 0;
    } else if (number1 > 9 && number2 > 9 && contador === 1) {
      visor2 = number1 + " " + operacion;
      number2 = numberOptional2;
      visor1 = number2;
    }
    controlComa = 0;
  }
</script>

<main>
  <div id="visor">
    <h2>{visor2}</h2>
    <h1>{visor1}</h1>
  </div>
  <div>
    <button on:click={() => Return("CE")} id="7">CE</button>
    <button on:click={() => Reset("C")} id="8">C</button>
    <button on:click={() => operationMasMenos("±")} id="±">±</button>
    <button on:click={() => operationPorcentaje("%")} id="%">%</button>
  </div>
  <div>
    <button on:click={() => handleClick(7)} id="7">7</button>
    <button on:click={() => handleClick(8)} id="8">8</button>
    <button on:click={() => handleClick(9)} id="9">9</button>
    <button on:click={() => operation("/")} id="/">/</button>
  </div>
  <div>
    <button on:click={() => handleClick(4)} id="4">4</button>
    <button on:click={() => handleClick(5)} id="5">5</button>
    <button on:click={() => handleClick(6)} id="6">6</button>
    <button on:click={() => operation("*")} id="*">×</button>
  </div>
  <div>
    <button on:click={() => handleClick(1)} id="1">1</button>
    <button on:click={() => handleClick(2)} id="2">2</button>
    <button on:click={() => handleClick(3)} id="3">3</button>
    <button on:click={() => operation("-")} id="-">-</button>
  </div>
  <div>
    <button on:click={() => handleClick(0)} id="0">0</button>
    <button on:click={() => Coma(".")} id=".">.</button>
    <button on:click={() => Results("=")} id="=">=</button>
    <button on:click={() => operation("+")} id="+">+</button>
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: rgb(17, 17, 17);
    width: 200px;
    border-radius: 10px;
  }
  #visor {
    display: flex;
    flex-direction: column;
    height: 50%;
    width: 180px;
    padding: 0 5px 0 5px;
    border-radius: 10px;
    margin-bottom: 10px;
    align-items: flex-end;
    background-color: rgb(235, 235, 235);
    box-sizing: border-box;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 3.5em;
    font-weight: 100;
    width: 100%;
    margin: 0px;
    line-height: 0.7;
    overflow: hidden;
    padding-bottom: 10px;
  }

  h2 {
    color: #ff3e00;
    font-size: 2em;
    margin: 0;
    font-weight: 200;
  }

  button {
    color: #ecf0f1;
    font-size: 17px;
    background-color: #e67e22;
    border: 1px solid #f39c12;
    border-radius: 5px;
    padding: 10px;
    box-shadow: 0px 6px 0px #d35400;
    transition: all 0.1s;
    width: 45px;
  }

  button:active {
    box-shadow: 0px 2px 0px #d35400;
    position: relative;
    top: 2px;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

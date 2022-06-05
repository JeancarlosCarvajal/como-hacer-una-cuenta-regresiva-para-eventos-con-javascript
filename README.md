# como-hacer-una-cuenta-regresiva-para-eventos-con-javascript
Como hacer una Cuenta Regresiva para Eventos con JavaScript

    <style> 
        body {
            text-align: center;
            margin-top: 250px;
        } 
        .input {
            margin-bottom: 10px;
            width: 250px;
        }
        .input:focus-visible {
            outline-offset: 0px;
        }
        .flex{
            display: flex!important;
        }
        .text-center{
            text-align: center!important;
        }
        .justify-center {
            justify-content: center;
        }
        .regresiva {
            list-style: none;
            column-gap: 20px;
        }
    </style> 

    <body>
        <div class="flex justify-center"> 
            <ul class="regresiva flex">
                <li> <strong id="dia">0</strong> <br> Días</li>
                <li> <strong id="hora">0</strong> <br>Horas</li>
                <li> <strong id="minuto">0</strong> <br>Minutos</li>
                <li> <strong id="segundo">0</strong> <br>Segundos</li>
            </ul>
        </div>
    </body> 
    <script> 
        // Comienza ejecutarse la Funcion
        const myInterval = setInterval(() => {
            // ano dia mes hora minuto del evento
            myTimer(2022, 13, 6, 8, 30);
        }, 1000); 
        function myTimer(ano, dia, mes, hora, minuto) {  
            // new Date(year, month, day, hours, minutes) 
            var fin_time = new Date(ano, (mes-1), dia, (hora), (minuto-1));
            // Aplicamos la funcion para ver el tiempo restante
            var result = getTime(fin_time); 
            if(result.days < 0 || result.seconds < 0){ 
                clearInterval(myInterval);
                return false;
            }
            // Ingresa los valores a los elementos del DOM
            document.getElementById("dia").innerHTML = result.days;
            document.getElementById("hora").innerHTML = result.hours;
            document.getElementById("minuto").innerHTML = result.minutes;
            document.getElementById("segundo").innerHTML = result.seconds; 
        } 
        // Funcion que resta el tiempo actual con el esperado
        const getTime = dateTo => {
            let now = (new Date()),
                time = (new Date(dateTo) - now + 1000) / 1000,
                seconds = ('0' + Math.floor(time % 60)).slice(-2),
                minutes = ('0' + Math.floor(time / 60 % 60)).slice(-2),
                hours = ('0' + Math.floor(time / 3600 % 24)).slice(-2),
                days = Math.floor(time / (3600 * 24));
            // Retorna varios valores
            return {
                seconds,
                minutes,
                hours,
                days,
                time
            }
        };  
    </script>  

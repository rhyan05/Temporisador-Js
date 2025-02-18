# Funcionamento

O timer tem 3 funções, sendo elas:
- Iniciar: Inica a contagem do Timer
- Pausar: Pausa a contagem do Timer
- Reiniciar: zera a contagem do Timer

# Design
![image](https://github.com/user-attachments/assets/a0072dd6-9d89-4335-97d2-7ae8e022c80f)

# Outra forma de realizar

Existe uma maneira mais simples de realizar esse timer, sendo ele:

``` javascript
function getTimeFromSeconds(segundos) {
    const data = new Date(segundos * 1000);
    return data.toLocaleTimeString('pt-BR', {
        hour12: false,
        timeZone: 'UTC'
    });
}

const relogio = document.querySelector('.relogio');
const iniciar = document.querySelector('.iniciar');
const pausar = document.querySelector('.pausar');
const zerar = document.querySelector('.zerar');

let segundos = 0;
let timer;

function iniciaRelogio() {
    timer = setInterval(() => {
        segundos++;
        relogio.innerHTML = getTimeFromSeconds(segundos);
    }, 1000);
}

iniciar.addEventListener('click', () => {
    relogio.classList.remove('pausado');
    clearInterval(timer);
    iniciaRelogio();
});

pausar.addEventListener('click', () => {
    clearInterval(timer);
    relogio.classList.add('pausado');
});

zerar.addEventListener('click', () => {
    clearInterval(timer);
    relogio.innerHTML = '00:00:00';
    relogio.classList.remove('pausado');
    segundos = 0;
});


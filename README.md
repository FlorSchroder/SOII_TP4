Se pide que, utilizando qemu[1], emulando un sistema Stellaris LM3S811 [2], se
desarrolle una aplicaci´on basada en FreeRTOS[3] que contenga las siguientes
caracter´ısticas.
1. Una tarea que simule un sensor de temperatura. Generando valores aleatorios, con una frecuencia de 10 Hz.
2. Una tarea que reciba los valores del sensor y aplique un filtro pasa bajos.
Donde cada valor resultante es el promedio de las ultimas N mediciones.
3. Una tarea que grafica en el display los valores de temperatura en el tiempo.
4. Se debe poder recibir comandos por la interfaz UART para cambiar el N
del filtro.
5. Calcular el stack necesario para cada task. Realizar el an´alisis utilizando
uxTaskGetStackHighWaterMark o vApplicationStackOverflowHook.
6. Implementar una tarea tipo top de linux, que muestre peri´odicamente
estad´ısticas de las tareas (uso de cpu, uso de memoria, etc).

# How to
## Instalar qemu:
```
sudo apt update
sudo apt install qemu qemu-system qemu-utils
```
Chequear que se haya instalado correctamente
<pre>(base) <font color="#8AE234"><b>florxha@florxha-Inspiron-7375</b></font>:<font color="#729FCF"><b>~</b></font>$ qemu-system-arm --version
QEMU emulator version 6.2.0 (Debian 1:6.2+dfsg-2ubuntu6.22)
Copyright (c) 2003-2021 Fabrice Bellard and the QEMU Project developers
</pre>

## FreeRTOS
En mi caso, preferi relizar un submodulo de freeRTOS
```
git submodule add https://github.com/FreeRTOS/FreeRTOS.git FreeRTOS

git submodule update --init --recursive
```
## Compilación
```
sudo apt install gcc-arm-none-eabi
``
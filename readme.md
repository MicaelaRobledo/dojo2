## Integrantes 
- Ariel Zubrzycki, Micaela Robledo, Facundo Villoldo.


## Proyecto: 
![Tinkercad](https://cdn.discordapp.com/attachments/1100044928576397382/1105170862551867402/image.png)



## Descripción
La empresa “UTN FRA Robotics” ganó la licitación de un proyecto, y deberá
Implementar un sistema que permita al usuario saber a qué estación de subte está
llegando, aparte el sistema muestra las estaciones que faltan hasta llegar a destino,
para ello debemos utilizar 4 LEDs y el display de 7 segmentos. Esta vez el buzzer
deberá emitir un sonido diferente cada vez que se llegue a una estación.
El sistema deberá arrancar apagado, luego de presionar el botón empezará y hará lo
pedido.

## Función principal
1- Implementar un sistema que permita al usuario saber a qué estación de subte está llegando.
2- El sistema muestra las estaciones que faltan hasta llegar a destino.
4- Utilizar 4 LEDs y el display de 7 segmentos.
5- El buzzer deberá emitir un sonido diferente cada vez que se llegue a una estación. 
6- El sistema deberá arrancar apagado, luego de presionar el botón empezará y hará lo pedido.


~~~ C++ (lenguaje en el que esta escrito)
//Nombre: Ariel Zubrzycki, Micaela Robledo, Facundo Villoldo
//EJ: DOJO 2-2

#define pin_ROJO 13
#define pin_AMARILLO 12
#define pin_NARANJA 11
#define pin_AZUL 10
#define LED_A 7
#define LED_B 8
#define LED_C A1
#define LED_D A2
#define LED_E A3
#define LED_F 6
#define LED_G 5

int secuencia = 0;
int estacion = 4;
  
void setup()
{
  Serial.begin(9600);
  pinMode(pin_ROJO, OUTPUT);
  pinMode(pin_AMARILLO, OUTPUT);
  pinMode(pin_NARANJA, OUTPUT);
  pinMode(pin_AZUL, OUTPUT);
  pinMode(LED_A, OUTPUT);
  pinMode(LED_B, OUTPUT);
  pinMode(LED_C, OUTPUT);
  pinMode(LED_D, OUTPUT);
  pinMode(LED_E, OUTPUT);
  pinMode(LED_F, OUTPUT);
  pinMode(LED_G, OUTPUT);
  pinMode(A0, OUTPUT);
  pinMode(9, INPUT_PULLUP);
}

void loop()
{
  int pulsador = digitalRead(9);
  
  if(pulsador == 0)
  {
    secuencia = 1;
  }
  
  while(secuencia == 1)
  {
    estacion -= 1;
    if(estacion < 0)
    {
      estacion = 3;
    }
    tone(A0, 500, 100);
    prender(estacion);
    delay(2000);
    
    Serial.print(estacion);

    if(pulsador == 1)
    {
      secuencia = 0;
    }

  }
}

void prender(int estacion)
{
  digitalWrite(LED_A,LOW);
  digitalWrite(LED_B,LOW);
  digitalWrite(LED_C,LOW);
  digitalWrite(LED_D,LOW);
  digitalWrite(LED_E,LOW);
  digitalWrite(LED_F,LOW);
  digitalWrite(LED_G,LOW);
  digitalWrite(pin_ROJO, LOW);
  digitalWrite(pin_AMARILLO, LOW);
  digitalWrite(pin_NARANJA, LOW);
  digitalWrite(pin_AZUL, LOW);
  
  switch(estacion)
    {
      case 0:
      digitalWrite(LED_A, HIGH);
      digitalWrite(LED_B, HIGH);
      digitalWrite(LED_F, HIGH);
      digitalWrite(LED_E, HIGH);
      digitalWrite(LED_D, HIGH);
      digitalWrite(LED_C, HIGH);
      digitalWrite(pin_AZUL, HIGH);
      break;
    
      case 1:
      digitalWrite(LED_B, HIGH);
      digitalWrite(LED_C, HIGH);
      digitalWrite(pin_NARANJA, HIGH);
      break;
    
      case 2:
      digitalWrite(LED_A, HIGH);
      digitalWrite(LED_B, HIGH);
      digitalWrite(LED_G,HIGH);
      digitalWrite(LED_E, HIGH);
      digitalWrite(LED_D, HIGH);
      digitalWrite(pin_AMARILLO, HIGH);
      break;
    
      case 3:
      digitalWrite(LED_A, HIGH);
      digitalWrite(LED_B, HIGH);
      digitalWrite(LED_G,HIGH);
      digitalWrite(LED_C, HIGH);
      digitalWrite(LED_D, HIGH);
      digitalWrite(pin_ROJO, HIGH);
      break;
  	}

}
~~~

## :robot: Link al proyecto
- [proyecto](https://www.tinkercad.com/things/kLSWQ8xen0J-epic-amur-rottis/editel?sharecode=yGe7JoNhzFZZntWk1Nmw2bO2M5H7eaMdJYq9L61Stuc&sharecode=yGe7JoNhzFZZntWk1Nmw2bO2M5H7eaMdJYq9L61Stuc)

---
### Fuentes
- Inchequeables(?)
# InterfazII

### Ejercicio n° 1 HOLA MUNDO! 

```js

void setup() {
  Serial.begin(9600); // Inicia la comunicación serie a 9600 bps
  Serial.println("Hola, Mundo!"); // Envía "Hola, Mundo!" al monitor serie
}

void loop() {
  // No es necesario poner nada en el loop para este ejemplo
}

```

#### Ejercicio n° 2 LED parpadeante 

```js

void setup() {  // Configuración inicial (ej: pines como entrada/salida)
  pinMode(13, OUTPUT);  // Pin 13 como salida
   pinMode(8, OUTPUT);  // Pin 8 como salida
}

void loop() {   // Se repite infinitamente
  digitalWrite(13, HIGH);  // Encender LED 1
  delay(500); // Esperar 1 segundo
  
  digitalWrite(8, LOW);   // Apagar LED 2
  delay(200);            //esperar 1 

   digitalWrite(8, HIGH);  // Encender LED 2
  delay(800);
  
  digitalWrite(13, LOW);   // Apagar LED 1
  delay(90);             // Esperar 1 segundo
  
              
}

```
<img src="https://raw.githubusercontent.com/AlexCR142/InterfazII/refs/heads/main/img/LED%20parpadea.png"/>

#### Ejercicio n° 3 LED boton 

```js
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
}
void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
  } else {
    digitalWrite(13, LOW);
  }
}

```
<img src="https://raw.githubusercontent.com/AlexCR142/InterfazII/refs/heads/main/img/LED%20boton.png"/>

#### Ejercicio n° 4 LED Potenciometro

```js
void setup() {
  pinMode(9, OUTPUT);  // Pin PWM (símbolo ~)
}
void loop() {
  int valor = analogRead(A0);           // Leer potenciómetro (0-1023)
  int brillo = map(valor, 0, 1023, 0, 255);  // Convertir a rango PWM
  analogWrite(9, brillo);               // Ajustar brillo
}
```
<img src="https://raw.githubusercontent.com/AlexCR142/InterfazII/refs/heads/main/img/LED%20potenciometro.png"/>

### Ejercicio n° 5 Semaforo

```js
// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  //digitalWrite(LED_4, LOW);   // Verde peatones apagado
  //digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  //delay(2000); // 2 segundos
}
```
<img src="https://raw.githubusercontent.com/AlexCR142/InterfazII/refs/heads/main/img/tinkercad%20semaforo.png"/>

### Ejercicio n° 6 Semaforo parpadeo peaton 

```js

// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
   digitalWrite(LED_4, HIGH); 
  delay(5000); // 5 segundos
   digitalWrite(LED_4, LOW);  // Verde peatones comienza a parpadear
  delay(500);
   digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(500) ; 
   digitalWrite(LED_4, LOW);  // Verde peatones apagado
  delay(500);
   digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(500) ; 
   digitalWrite(LED_4, LOW);  // Verde peatones parpadea mas rapido
  delay(200);
   digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(200) ; 
   digitalWrite(LED_4, LOW);  // Verde peatones apagado
  delay(200);
   digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(200) ; 
   digitalWrite(LED_4, LOW);  // Verde peatones apagado
  delay(200);
   digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(200) ; 
  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  //digitalWrite(LED_4, LOW);   // Verde peatones apagado
  //digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  //delay(2000); // 2 segundos
}
```
### Ejercicio n° 7 Arduino boton processing

#### Codigo Arduino 

```js
int buttonPin = 2;  // Pin del botón
int buttonState = 0;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {   // Botón presionado
    Serial.println(1);        // Enviar un "1" a Processing
    delay(200);               // Evitar rebotes
  }
}
```

#### Codigo Processing


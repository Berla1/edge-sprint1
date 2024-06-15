
# Jogo de cartas com RFID

## O problema

A empresa Mahindra Racing, equipe de Fórmula E, está enfrentando problemas de popularidade no Brasil. O grupo E-fficency trouxe como uma das soluções a criação de um jogo de cartas, utilizando RFID.

### Como jogar

Cada carta é uma equipe da Fórmula E e dois jogam um contra o outro. Ambos os jogadores devem ter um bolo de cartas com a quantidade igual. Durante uma rodada um dos jogadores deve anunciar o atributo desejado, quem tiver com o maior número nesse atributo vence a rodada e ganha a carta do adversário. Em caso de empate outra característica deve ser comparada.

## Como funciona o RFID

Todo cartão ou tag RFID possui um código de identificação único. Baseando-se nessa informação, é possível criar resultados diferentes para cada cartão que é escaneado pelo leitor. Sendo assim, podendo criar de maneira digital as cartas do jogo para um exibição simplória e um comparação de atributos automática. 

## Simulação do Tinkercad

Na plataforma do Tinkercad não é existe um leitor ou identificador RFID, então por conta disso, é necessário usar métodos alternativos que simulam o seu funcionamento.

https://www.tinkercad.com/things/8tu755pKA9J-simulacao-rfid

Nesta simulação no Arduino da esquerda, conectado a um botão, quando pressionado, envia um sinal para o Arduino a sua direita, isso faz com que um led se acenda. O Arduino, que envia o sinal simula um cartão ou uma tag, enquanto o Arduino que recebe esse sinal e acende o led, simula o leitor. 

[imagem da simulação]

## Simulação real

Cada cartão ou tag tem seu código próprio, é exibido cada atributo de cada carta ao ser escaneado

### Código-fonte
```
#include <SPI.h>
#include <MFRC522.h>
#include <Wire.h>
  
#define SS_PIN 10 // Pino 10 do Arduino ligado ao Slave Select
#define RST_PIN 9 // Pino 9 do Arduino ligado ao Reset
MFRC522 mfrc522(SS_PIN, RST_PIN); // Cria a instancia MFRC522
  
char st[20]; // Matriz st com 20 elementos
  
void setup() {
  Serial.begin(9600); // Inicia a serial
  SPI.begin(); // Inicia a comunicacao SPI  
     
  // A biblioteca MFRC522 funciona com SPI
  mfrc522.PCD_Init(); // Inicia MFRC522
  Serial.println("Leitor pronto");
  Serial.println();
}
  
void loop() 
{
  // Interroga se existe um novo cartao RFID no leitor
  if ( ! mfrc522.PICC_IsNewCardPresent()) 
  {
    return;
  }
  // Le um cartao RFID colocado no leitor
  if ( ! mfrc522.PICC_ReadCardSerial()) 
  {
    return;
  }
  //Mostra UID na serial
  //Serial.print("UID da tag :");
  String conteudo= ""; // String de nome conteudo
  byte letra;
   
  // mfrc522.uid.size com o tamanho da UID
  // mfrc522.uid.uidByte[i] com os bytes da UID
  // A UID do cartao RFID é formada por bytes
   
  // Imprime no monitor do PC os bytes da UID 
  for (byte i = 0; i < mfrc522.uid.size; i++)  
  {
     //Serial.print(mfrc522.uid.uidByte[i] < 0x10 ? " 0" : " ");
     //Serial.print(mfrc522.uid.uidByte[i], HEX);
     conteudo.concat(String(mfrc522.uid.uidByte[i] < 0x10 ? " 0" : " "));
     conteudo.concat(String(mfrc522.uid.uidByte[i], HEX));
  }
   
 
  // Altera o conteudo do string conteudo para letras maiusculas
  conteudo.toUpperCase();

  if (conteudo.substring(1) == "43 98 90 79")
  {
    Serial.println("Carta: Mahindra Racing");
    Serial.println();

  }
}
```


## Participantes

- [Camila Feitosa](https://github.com/camfeitosa) RM: 558808
- [Gabriel Matiolli](https://github.com/m4tiolli) RM: 558963
- [Gustavo Berlanga](https://www.github.com/berla1) RM: 555298
- [Leonardo Taschin](https://github.com/LeoTaschin) RM: 554583
- [Vinicius Gardim](https://www.github.com/gardim1) RM: 556013

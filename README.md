
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


## Participantes

- [Camila Feitosa](https://github.com/camfeitosa) RM: 558808
- [Gabriel Matiolli](https://github.com/m4tiolli) RM: 558963
- [Gustavo Berlanga](https://www.github.com/berla1) RM: 555298
- [Leonardo Taschin](https://github.com/LeoTaschin) RM: 554583
- [Vinicius Gardim](https://www.github.com/gardim1) RM: 556013

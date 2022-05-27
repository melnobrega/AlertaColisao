# Alerta de Colisão
Este é um projeto utilizando a plataforma arduino UNO R3 cujo objetivo é criar um protótipo de sensor de proximidade que detecta objetos próximos e emite avisos sonoros, visuais e notificação por e-mail de acordo com a distância do objeto detectado, afim de evitar colisões.

# Hardwares utilizados:
- Arduino UNO R3
O Arduino Uno R3 é uma placa baseada no microcontrolador Tmega328. Ele tem 14 pinos de entrada/saída digital (dos quais 6 podem ser usados como saídas PWM), 6 entradas analógicas, um cristal oscilador de 16MHz, uma conexão USB, uma entrada de alimentação, uma conexão ICSP e um botão de reset. Ele contém todos os componentes necessários para suportar o microcontrolador, simplesmente conecte a um computador pela porta USB ou alimentar com uma fonte ou com uma bateria e tudo pronto para começar. O Arduino Uno R3 difere de todas as placas antecessoras no sentido de não utilizar o chip FTDI cara conversão do sinal serial. Utiliza no seu lugar um Atmega8U2 programado como conversor de USB para serial.

- Speaker para Arduino
Speaker para arduino é um módulo que será usado neste projeto como buzzer. O buzzer é um componente eletrônico que converte um sinal elétrico em onda sonora. Este dispositivo é utilizado para sinalização sonora, sendo aplicado em computadores, despertadores, carros, entre outros. Ou seja, através do recebimento de corrente elétrica ele é ativado e podemos regular a frequência que será emitida, para isso utilizamos o método tone() e noTone().

- Protoboard 800 pontos
É uma placa com furos e conexões condutoras utilizada para a montagem de protótipos e projetos em estado inicial. A grande vantagem da protoboard na montagem de circuitos eletrônicos é a facilidade de inserção de componentes, uma vez que não necessita soldagem. As placas variam de 400 furos até 6000 furos, tendo conexões verticais e horizontais. 
	Na superfície de uma matriz de contato há uma base de plástico em que existem centenas de orifícios onde são encaixados os componentes. Em sua parte inferior são instalados contatos metálicos que interligam eletricamente os componentes inseridos na placa. Geralmente suportam correntes entre 1 A e 3 A.
	A protoboard possui faixas de terminais, que são faixas de contato no qual são instalados os componentes eletrônicos, parte central da protoboard; e faixas de barramentos, que são usadas para o fornecimento de tensão ao circuito, constituídas de duas colunas nas laterais, uma utilizada para o condutor negativo ou terra e outra para o positivo.

- Diodo Emissor de Luz
O diodo emissor de luz (sigla LED, em inglês: light-emitting diode), é usado para a emissão de luz em locais e instrumentos onde se torna mais conveniente a sua utilização no lugar de uma lâmpada. Especialmente utilizado em produtos de microeletrônica como sinalizador de avisos, também pode ser encontrado em tamanho maior, como em alguns modelos de semáforos.
	Utilizaremos os LEDs como atuadores no nosso projeto, que ao receber a informação de proximidade irá ser aceso para aviso da distância detectada. Para isso utilizaremos três cores de LED: verde para uma distância segura, de até 50cm; laranja para distância de atenção, entre 50cm e 30cm; e vermelha para informar perigo, distância menor que 30cm.
	Os LEDs serão fixados na protoboard e utilizamos o método digitalWrite(pin, LOW) para apagar o LED e  digitalWrite(pin, HIGH) para acender o LED.

- Sensor Ultrasônico HC-SR04
	Sensores ultrassônicos são aplicados como detectores de objetos e são muito populares principalmente na robótica, onde são utilizados para identificar obstáculos e corrigir continuamente o trajeto feito por um robô. Por meio da emissão de sinais ultrassônicos, é possível especificar a distância do sensor até um determinado obstáculo. O range de atuação é da ordem de 4 metros, com distância mínima de medição de 2 cm e incluindo obstáculos entre de um ângulo de abertura de 15 graus.
	O princípio de funcionamento do HC-SR04 consiste na emissão de sinais ultrassônicos pelo sensor e na leitura do sinal de retorno (reflexo/eco) desse mesmo sinal. A distância entre o sensor e o objeto que refletiu o sinal é calculada com base no tempo entre o envio e a leitura de retorno. Como o ouvido humano só consegue identificar ondas mecânicas até a frequência de 20KHz, os sinais emitidos pelo sensor ultrassônico não podem ser escutados por nós.
O sensor HC-SR04 é composto de três partes principais:
Transmissor Ultrassônico – Emite as ondas ultrassônicas que serão refletidas pelos obstáculos;
Um receptor – Identifica o eco do sinal emitido pelo transmissor;
Circuito de controle – Controla o conjunto transmissor/receptor, calcula o tempo entre a emissão e recepção do sinal;
Temos um pino de VCC, alimentado com 5V, um GND, e os dois pinos de controle e leitura do sensor: O Trigger, no qual nós aplicamos o sinal para comandar o envio dos pulsos ultrassônicos, e o Echo, que retorna para o Arduino os pulsos com o tempo de duração entre o envio e recepção do sinal de retorno. A corrente elétrica de operação do sensor é de 15 mA, portanto é uma aplicação de baixo consumo energético.
	Iremos utilizar os pins 6 e 7 para a recepção das informações do sensor ultrasônico, sendo o pino Echo ligado no pin 6 como recebimento [pinMode(6, INPUT)] e o pino Trigger conectado no pin 7 como resposta [pinMode(7, OUTPUT)] para o cálculo da distância [time = pulseIn(6, HIGH) e distancia = (time*0.0001*340)/2].


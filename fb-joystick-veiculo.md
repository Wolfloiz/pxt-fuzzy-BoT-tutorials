### @diffs true
# FuzzyBoT Joystick - Veículo

## Passo 1
Neste tutorial, construiremos o código do veículo (FuzzyBoT) que receberá os sinais de rádio vindos do Joystick.
Dessa forma, os sinais de rádio recebidos serão transformados em movimentos do carrinho.

## Passo 2
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Comece indo até a aba ``||radio:Rádio||``, e arrastando o bloco ``||radio:definir grupo do rádio (1)||`` para dentro do laço ``||basic:no iniciar||``. 
Altere o número de **1** para **255** (ou o número que você usou no Joystick). 

 **ATENÇÃO:** Tenha certeza de que esse número seja **IGUAL** ao colocado no **Joystick**, para que eles se comuniquem entre si.

```blocks
radio.setGroup(255)
```

## Passo 4 
Em seguida, acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Nomeie essa variável como ``||variables:velocidade||``. Por fim, adicione o bloco ``||variables:definir velocidade para 0||`` que
aparecerá ao criá-la para dentro do laço ``||basic:no iniciar||``. 

```blocks
radio.setGroup(255)
let velocidade = 0
```

## Passo 5

Na aba ``||radio:Rádio||``, arraste o laço ``||radio:ao receber rádio name value||`` para dentro do código. 
Esse laço será executado sempre que o Micro:bit receber um pacote com ``||radio:name e value||`` via rádio. 
Ou seja, neste caso, quando ele receber os dados enviados pelo Joystick.

```blocks
radio.onReceivedValue(function (name, value) {
	
})
radio.setGroup(255)
let velocidade = 0
```

## Passo 6
A partir daqui, construiremos testes condicionais para cada possibilidade de ``||radio:name e value||`` enviada pelo Joystick.
Para isso, acesse o menu de ``||Logic:Lógica||`` e adicione um laço ``||Logic:se então||`` dentro do ``||radio:ao receber rádio name value||``.
Em seguida, retorne à aba ``||Logic:Lógica||`` e utilize o comparador ``||Logic:0 = 0||`` para substituir o campo ``||Logic:verdadeiro||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (0 == 0) {
    	
    }
})
radio.setGroup(255)
let velocidade = 0
```

## Passo 7
Clique sobre o bloco redondo ``||variables:name||`` do laço ``||radio:ao receber rádio name value||`` e o arraste para substituir o primeiro campo do comparador.
Em seguida, clique em ``||advanced:Avançado||`` para abrir outras categorias de blocos, clique em ``||text:Texto||`` e selecione o bloco redondo de aspas duplas: ``||text:" "||``.
Posicione-o no segundo campo do comparador e escreva a letra **"E"** em seu centro.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
    	
    }
})
radio.setGroup(255)
let velocidade = 0
```

## Passo 8
Feito isso, vamos definir o que acontece com o FuzzyBoT quando ele recebe a combinação ``||radio:name = "E"||``.
Para isso, retorne ao menu ``||variables:Variáveis||`` e arraste o bloco ``||variables:definir velocidade para 0||`` para dentro do 
``||Logic:então||``. Altere o valor de **0** para o bloco redondo ``||variables:value||`` clicando e arrastando a partir do laço ``||radio:ao receber rádio name value||``. 

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 9
Agora, clique com o botão direito do mouse e duplique todo esse laço ``||Logic:se então||``.
Posicione o novo bloco abaixo do anterior, não dentro!

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "E") {
        velocidade = value
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 10
Apague o bloco de definição da variável dentro do ``||Logic:então||``. Em seguida,
modifique o texto de ``||text:"E"||`` para ``||text:"DIR"||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
    	
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 11
Retorne à aba ``||Logic:Lógica||`` e adicione um laço ``||Logic:se verdadeiro então... senão||`` **DENTRO** do anterior.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (true) {
        	
        } else {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 12
Retorne à aba ``||Logic:Lógica||`` e use um comparador ``||Logic:0 = 0||`` para substituir o campo ``||Logic:verdadeiro||``.
O primeiro campo desse comparador deve ser o bloco ``||variables:value||`` retirado do laço ``||radio:ao receber rádio name value||``. 

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
        	
        } else {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 13
Quando o ``||variables:"value"||`` recebido para o ``||variables:"name"||`` ``||text:"DIR"||`` for igual a **0**,
devemos parar o carrinho. Para isso, acesse o menu ``||fuzzyBot: FuzzyBoT||`` e adicione o bloco 
``||fuzzyBot: parar motor esquerdo||`` dentro do ``||Logic:então||``. Altere de motor ``||fuzzyBot:esquerdo||`` 
para ``||fuzzyBot:todos||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 14
Agora, clique **quatro** vezes no sinal de **(+)** desse laço para adicionar sequências de ``||Logic:senão se ... então||``. Feito isso,
clique no sinal de **(-)** para retirar o laço ``||Logic:senão||``. Consulte a dica na lâmpada para verificar seu código.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (false) {
        	
        } else if (false) {
        	
        } else if (false) {
        	
        } else if (false) {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 15
Dentro de cada espaço triangular desse laços, ou seja, nos testes condicionais, devemos colocar os casos restantes de valores para 
a variável ``||variables:value||``. Duplique o comparador ``||logic:value = 0||`` do primeiro e altere para os valores a seguir: 

- value = 1;
- value = 2;
- value = 3;
- value = 4;

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
        	
        } else if (value == 2) {
        	
        } else if (value == 3) {
        	
        } else if (value == 4) {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 16
Agora, vamos definir o que deve acontecer dentro do primeiro ``||logic:então||``, para quando ``||logic:value = 1||``.
Acesse o menu ``||fuzzyBot:FuzzyBoT||`` e adicione dois blocos ``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||``
dentro desse ``||logic:então||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
        	
        } else if (value == 3) {
        	
        } else if (value == 4) {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 17
Altere o primeiro bloco para o ``||fuzzyBot:Motor direito||`` e o valor de velocidade para a 
``||variables:variável velocidade||``, localizada no menu de ``||variables:Variáveis||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
        	
        } else if (value == 3) {
        	
        } else if (value == 4) {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 18
Prosseguindo ao caso em que ``||logic:value = 2||``, vamos duplicar os dois blocos de controle dos motores do laço
anterior. Entretanto, altere os motores de cada bloco: de **direito** para **esquerda** e vice-versa. Assim, 
o ``||fuzzyBot:Motor esquerdo||`` receberá o valor de ``||variables:velocidade||`` e o ``||fuzzyBot:Motor direito||`` receberá **0**.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
        	
        } else if (value == 4) {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 19
Feito isso, avance para o próximo ``||logic:então||``, para quando  ``||logic:value = 3||``.
Insira apenas um bloco ``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||``.
Em seguida, modifique:
- o motor de ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``;
- seu sentido de ``||fuzzyBot:frente||`` para ``||fuzzyBot:trás||``;
- e a velocidade de **0** para a ``||variables:variável velocidade||``.   

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 20
Para o último caso dentro desse laço ``||variables:"name"||`` ``||text:"DIR"||``, quando ``||logic:value = 4||``, apenas duplique
o bloco do caso anterior e altere o sentido de rotação de ``||fuzzyBot:trás||`` para ``||fuzzyBot:frente||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 21
Assim, finalizamos o laço ``||logic:se então||`` para quando o rádio recebe ``||variables:"name"||`` ``||text:"DIR"||``.
Volte ao início do laço ``||radio:ao receber rádio name value||`` e duplique todo o laço  ``||logic:se name = "E" então||``. 
Cole a cópia no final do ``||radio:ao receber rádio name value||``, **abaixo** do  ``||logic:se name = "DIR" então||``.
Confira seu código clicando na dica da lâmpada...

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "E") {
        velocidade = value
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 22
Dentro do comparador, altere o segundo campo de ``||text:"E"||`` para ``||text:"C"||``.
Em seguida, exclua o bloco de definição da velocidade dentro do ``||logic:então||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
    	
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 23
Dentro desse laço, adicione um ``||logic:se então... senão||`` localizado na aba ``||logic:Lógica||``.
No seu teste condicional (espaço triangular escrito verdadeiro), insira um comparador com os dados ``||logic:value = 0||``.
Para facilitar, esse comparador pode ser duplicado de etapas anteriores do código.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
        	
        } else {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 24
Preencha o ``||logic:então||`` e o ``||logic:senão||`` desse laço com blocos ``||fuzzyBot:LED esquerdo definir para Ligado||``. Em seguida,
altere o estado de ``||fuzzyBot:Ligado||`` para ``||fuzzyBot:Desligado||`` dentro do ``||logic:senão||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 25
Duplique todo o laço ``||logic:se name = "C" então||`` e cole **abaixo** do anterior. 
Modifique o texto de ``||text:"C"||`` para ``||text:"D"||`` e ambos os blocos de controle dos LEDs
de ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:direito||``. 

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

## Passo 26
Agora seu código está pronto! Baixe-o para o micro:bit do FuzzyBoT e teste a combinação do Joystick
para controlar o carrinho com este código! Lembre-se de ligar ambos os dispositivos e conectá-laços
no mesmo grupo de rádio.

```blocks
```

## Passo 27
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "E") {
        velocidade = value
    }
    if (name == "DIR") {
        if (value == 0) {
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (value == 1) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "C") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
        }
    }
    if (name == "D") {
        if (value == 0) {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
        } else {
            fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
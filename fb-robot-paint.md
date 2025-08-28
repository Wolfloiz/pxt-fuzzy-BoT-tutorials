### @diffs true
# Robô Pintor

## Passo 1
Nesse tutorial, vamos adaptar o código do FuzzyBoT controlado pelo Joystick
para transformá-lo em um robô pintor! Para isso, iremos criar condições que
permitam movimentar um servomotor quando pressionarmos os botões A ou B do 
Joystick.

```template
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

## Passo 2
Para começar, verifique se a biblioteca da Fuzzy Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

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

## Passo 3
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Nomeie essa variável como ``||variables:angulo||``. Por fim, adicione o bloco 
``||variables:definir angulo para 0||`` que aparecerá ao criá-la 
para dentro do bloco ``||basic:no iniciar||``. 

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
let angulo = 0
```

## Passo 4
Altere o valor da variável ``||variables:angulo||`` nesse bloco de definição de
**0** para **50**.

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
let angulo = 50
```

## Passo 5
Acesse o menu ``||fuzzyBot:FuzzyBoT||`` e insira o comando 
``||fuzzyBot:servo S1 definir para ângulo 0||`` dentro do ``||basic:no iniciar||``. 

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
let angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
```

## Passo 6
Acesse o menu ``||variables:Variáveis||`` e utilize o bloco ``||variables:angulo||`` 
para subsitituir o valor **0** do bloco de controle do servomotor. Nos próximos 
passos vamos fazer pequenas alterações nos comandos de movimentação do FuzzyBoT,
especificamente nos blocos em que ele vira para a esquerda e para a direita.

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
let angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 7
Procure o condicional ``||logic:se name = "DIR"||``. Em seguida, procure o 
condicional ``||logic:se valor = 1||``. Dentro desse ``||logic:então||``,
clique na segunda seta do bloco ``||fuzzyBot:Motor esquerdo||`` para alterar 
o sentido de rotação de ``||fuzzyBot:frente||`` para ``||fuzzyBot:trás||``.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 0)
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
let angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 8
Altere o valor de velocidade desse bloco de **0** para a própria variável
``||variables:velocidade||``, localizada na aba ``||variables:Variáveis||``.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
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
let angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 9
Agora, procure o condicional ``||logic:se valor = 2||``. Dentro desse 
``||logic:então||``, clique na segunda seta do bloco 
``||fuzzyBot:Motor direito||`` para alterar 
o sentido de rotação de ``||fuzzyBot:frente||`` para ``||fuzzyBot:trás||``.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, 0)
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
let angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 10
Altere o valor de velocidade desse bloco de **0** para a própria variável
``||variables:velocidade||``, localizada na aba ``||variables:Variáveis||``.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
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
let angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 11
A partir daqui, construiremos novos testes condicionais para controlar o 
servomotor a partir de pares ``||radio:name e value||`` enviados pelo Joystick.
Para isso, acesse o menu de ``||Logic:Lógica||`` e adicione um bloco 
``||Logic:se então||`` dentro do ``||radio:ao receber rádio name value||``.

 **Atenção:** Ele deve ser posicionado abaixo dos outros blocos ``||Logic:se então||``,
 não podendo estar dentro de nenhum deles.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (true) {
    	
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
let angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 12
Em seguida, retorne à aba ``||Logic:Lógica||`` e utilize o comparador 
``||Logic:0 = 0||`` para substituir o campo ``||Logic:verdadeiro||``.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (0 == 0) {
    	
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
let angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 13
Clique sobre o bloco redondo ``||variables:name||`` do laço 
``||radio:ao receber rádio name valor||`` e arraste-o para substituir o primeiro
campo do comparador. Em seguida, clique em ``||advanced:Avançado||`` para abrir 
outras categorias de blocos, clique em ``||text:Texto||`` e selecione o bloco 
redondo de aspas duplas: ``||text:" "||``. Posicione-o no segundo campo do 
comparador e escreva a letra **"A"** em seu centro.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
    	
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
let angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 14
Retorne à aba ``||Logic:Lógica||`` e adicione um laço 
``||Logic:se então||`` **DENTRO** do anterior.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (true) {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
let angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 15
Retorne à aba ``||Logic:Lógica||`` e use um comparador ``||Logic:0 = 0||`` 
para substituir o campo ``||Logic:verdadeiro||``. O primeiro campo desse 
comparador deve ser o bloco ``||variables:valor||`` retirado do laço 
``||radio:ao receber rádio name valor||``. 

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (value == 0) {
        	
        }
    }
})
let velocidade = 0
radio.setGroup(255)
velocidade = 0
let angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 16
Retorne ao menu ``||variables:Variáveis||`` e arraste o bloco 
``||variables:definir angulo para 0||`` para dentro do ``||Logic:então||``. 

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = 0
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 17
Vá à ``||math:Matemática||`` e insira o bloco 
``||math:constrain 0 between 0 and 0||`` no campo de valor do bloco de 
definição da variável ``||variables:angulo||``, substituindo o **0**.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(0, 0, 0)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 18
Volte à aba ``||math:Matemática||`` e insira um bloco de adição dentro do 
primeiro **0** do bloco ``||math:constrain 0 between 0 and 0||``.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(0 + 0, 0, 0)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 19
Modifique o primeiro campo da adição para a variável ``||variables:angulo||``,
localizada na aba ``||variables:Variáveis||``. Em seguida, altere o segundo 
campo da adição de **0** para **5**.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 5, 0, 0)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 20
Altere o último valor do bloco ``||math:constrain||`` de **0** para **180**.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 5, 0, 180)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 21
Ainda dentro desse ``||logic:então||``, adicione um comando
``||fuzzyBot:servo S1 definir para ângulo 0||``, localizado na aba 
``||fuzzyBot:fuzzyBot||``.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 5, 0, 180)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, 0)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 22
Acesse o menu ``||variables:Variáveis||`` e utilize o bloco 
``||variables:angulo||`` para substituir o valor **0** do bloco de controle 
do servomotor.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 5, 0, 180)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 23
Agora, clique com o botão direito do mouse e duplique todo o laço 
``||Logic:se então||`` do ``||Logic:name = "A"||``. 
Posicione o novo bloco abaixo do anterior, não dentro!

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 5, 0, 180)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 5, 0, 180)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 24
Modifique o texto do comparador de ``||text:"A"||`` para ``||text:"B"||``.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 5, 0, 180)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
    if (name == "B") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 5, 0, 180)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 25
Clique na seta do bloco de adição dentro do bloco ``||math:constrain||`` para
alterar de uma operação de adição para uma operação de ``||math:subtração||``.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 5, 0, 180)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
    if (name == "B") {
        if (value == 0) {
            angulo = Math.constrain(angulo - 5, 0, 180)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

## Passo 26

Agora seu código está pronto! Baixe-o para o micro:bit do FuzzyBoT e teste 
os botões A e B do Joystick para controlar o servomotor do carrinho! 
Lembre-se de ligar ambos os dispositivos e conectá-los no mesmo grupo de rádio.

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
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 2) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 3) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, velocidade)
        } else if (value == 4) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
    if (name == "A") {
        if (value == 0) {
            angulo = Math.constrain(angulo + 5, 0, 180)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
    if (name == "B") {
        if (value == 0) {
            angulo = Math.constrain(angulo - 5, 0, 180)
            fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
        }
    }
})
let angulo = 0
let velocidade = 0
radio.setGroup(255)
velocidade = 0
angulo = 50
fuzzyBot.servoRun(fuzzyBot.Servos.S1, angulo)
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```

### @diffs true
# Seguidor de Cor

## Passo 1
Neste projeto, vamos programar o Fuzzy BoT para que ele seja capaz de seguir 
determinadas cores. Isso será especialmente útil para que ele consiga 
seguir e se aproximar de balões.

## Passo 2
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||basic:Básico||`` e adicione um bloco 
``||basic:pausa (ms) 100||`` no bloco ``||basic:no iniciar||``.
Modifique a duração da pausa de **100 ms** para **2000 ms** (2 segundos).

```blocks
basic.pause(2000)
```

## Passo 4
Vá ao menu ``||Advanced:Avançado||``, acesse ``||Camera:Sensor Câmera||`` 
e selecione o bloco ``||Camera:Inicializar câmera - Porta I2C - Endereço 0x60||``. 
Posicione o bloco abaixo da ``||basic:pausa||``. 

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
```

## Passo 5
Retorne à categoria ``||Camera:Sensor Câmera||`` e adicione o bloco 
``||Camera:Definir quantidade de configurações do modo Cor: 1||`` 
no bloco ``||basic:no iniciar||``.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionColor, 1)
basic.forever(function () {
	
})
```

## Passo 6
Clique na seta desse bloco para alterar de ``||Camera:Cor||`` para 
``||Camera:Blob||``. Em seguida, altere a quantidade de parâmetros de **1** 
para **2**.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
basic.forever(function () {
	
})
```

## Passo 7
Retorne à categoria ``||Camera:Sensor Câmera||`` e adicione dois blocos 
``||Camera:Definir parâmetros do modo Blob: largura mínima 3 altura mínima 4 cor Vermelho ID 1||``, 
um abaixo do outro dentro do ``||basic:no iniciar||``.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(3, 4, color_label_e.kColorRed, 1)
Camera.SetBlobParam(3, 4, color_label_e.kColorRed, 1)
basic.forever(function () {
	
})
```

## Passo 8
Altere os valores de ``||Camera:largura||`` e ``||Camera:altura||`` mínimas 
para **5** em ambos os blocos. Em seguida, modifique a cor do segundo bloco 
de ``||Camera:Vermelho||`` para ``||Camera:Verde||`` e o ``||Camera:ID||`` do
segundo para **2**.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
basic.forever(function () {
	
})
```

## Passo 9
Retorne à categoria ``||Camera:Sensor Câmera||`` e adicione o bloco 
``||Camera:Definir número máximo de blobs por cor (1-5): 1||`` dentro do 
``||basic:no iniciar||``. Altere a quantidade máxima de **1** para **5**.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
basic.forever(function () {
	
})
```

## Passo 10
Volte mais uma vez ao menu ``||Camera:Sensor Câmera||`` e adicione o bloco 
``||Camera:Habilitar modo Cor||`` dentro do ``||basic:no iniciar||``.
Clique na seta para alterar de ``||Camera:Cor||`` para ``||Camera:Blob||``.  

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
basic.forever(function () {
	
})
```

## Passo 11
Acesse a aba ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Crie as quatro variáveis que serão usadas nesse código: 
``||variables:ligado||``, ``||variables:largura||``, ``||variables:x||`` e 
``||variables:velocidade||``. Depois de criadas, adicione um bloco 
``||variables:definir velocidade para 0||`` dentro do ``||basic:no iniciar||``.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 0
basic.forever(function () {
	
})
```

## Passo 12
Altere o valor da variável ``||variables:velocidade||`` de **0** para **40**.
Em seguida, adicione um bloco ``||basic:pausa (ms)||`` com duração de **2000 ms**
(2 segundos) finalizando o ``||basic:no iniciar||``.

```blocks
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 13
Feito isso, vamos criar uma ``||Functions:Função||`` para seguir cores.
Para isso, clique no menu ``||Advanced:Avançado||``, acesse 
``||Functions:Funções||`` e clique em **Fazer uma função...**.
Clique no campo editável do bloco azul para criar uma função chamada 
``||Functions:segue_cor||``. Um novo laço referente à função criada é 
adicionado automaticamente ao código.

```blocks
function segue_cor () {
	
}
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 14
Acesse o menu ``||Logic:Lógica||`` e adicione um bloco  
``||Logic:se então senão||`` dentro do laço da ``||Functions:Função||``.

```blocks
function segue_cor () {
    if (true) {
    	
    } else {
    	
    }
}
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 15
Retorne à ``||Logic:Lógica||`` e utilize um comparador ``||Logic:0 < 0||``
para substituir o **verdadeiro** do ``||Logic:se então senão||``. Clique em sua 
seta para alterar o sinal de **<** para **>=**.

```blocks
function segue_cor () {
    if (0 >= 0) {
    	
    } else {
    	
    }
}
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 16
O primeiro campo desse comparador deverá ser a variável ``||variables:largura||``,
enquanto o segundo deve ser alterado do valor **0** para **80**.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
    	
    } else {
    	
    }
}
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 17
Acesse a categoria ``||fuzzyBot:FuzzyBoT||`` e adicione o comando 
``||fuzzyBot:parar motor esquerdo||`` dentro do ``||logic:então||``.
Clique em sua seta para alterar de motor ``||fuzzyBot:esquerdo||`` 
para ``||fuzzyBot:todos||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
    	
    }
}
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 18
Agora, dentro do ``||Logic:senão||``, adicione um novo laço 
``||Logic:se então senão||``. Clique no sinal de **+** desse bloco para 
adicionar dois ``||Logic:senão se||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        if (true) {
        	
        } else if (false) {
        	
        } else if (false) {
        	
        } else {
        	
        }
    }
}
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 19
Retorne à aba ``||Logic:Lógica||`` e adicione um operador Booleano 
``||Logic:E||`` dentro do campo **verdadeiro** desse bloco ``||Logic:Se então||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        if (false && false) {
        	
        } else if (false) {
        	
        } else if (false) {
        	
        } else {
        	
        }
    }
}
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 20
Agora, insira comparadores ``||Logic:0 < 0||`` dentro de todos os quatro campos
de bordas triangulares do ``||Logic:se então||`` e do ``||Logic:senão se||``.  

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        if (0 < 0 && 0 < 0) {
        	
        } else if (0 < 0) {
        	
        } else if (0 < 0) {
        	
        } else {
        	
        }
    }
}
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 21
Edite os sinais dos comparadores para a seguinte ordem:
- **>=**;
- **<=**;
- **<**;
- **>**.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        if (0 >= 0 && 0 <= 0) {
        	
        } else if (0 < 0) {
        	
        } else if (0 > 0) {
        	
        } else {
        	
        }
    }
}
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 22
Utilize a variável ``||variables:x||`` dentro do primeiro campo de cada um 
dos comparadores.  

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 0 && x <= 0) {
        	
        } else if (x < 0) {
        	
        } else if (x > 0) {
        	
        } else {
        	
        }
    }
}
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 23
Edite o segundo valor dos comparadores para a seguinte configuração:
- **x >= 40**;
- **x <= 60**;
- **x < 40**;
- **x > 60**.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
        	
        } else if (x < 40) {
        	
        } else if (x > 60) {
        	
        } else {
        	
        }
    }
}
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 24
A partir daqui, vamos programar o que acontece dentro do ``||logic:então||``
de cada condição. Começando pela primeira condição, na qual temos o operador Booleano
``||logic:E||``, insira o comando 
``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||``. Clique na 
seta desse bloco para alterar de motor ``||fuzzyBot:esquerdo||`` para 
``||fuzzyBot:todos||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 0)
        } else if (x < 40) {
        	
        } else if (x > 60) {
        	
        } else {
        	
        }
    }
}
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
let velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 25
Altere o campo de valor da velocidade de **0** para a variável 
``||variables:velocidade||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
        	
        } else if (x > 60) {
        	
        } else {
        	
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 26
Prosseguindo para o segundo ``||logic:então||`` (**x < 40**), insira dois blocos 
``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||``. Clique na 
seta do primeiro bloco para alterar de motor ``||fuzzyBot:esquerdo||`` para 
``||fuzzyBot:direito||``. Em seguida, clique na seta de direção do segundo bloco
para alterar de ``||fuzzyBot:frente||`` para ``||fuzzyBot:trás||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 0)
        } else if (x > 60) {
        	
        } else {
        	
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 27
Acesse o menu ``||math:Matemática||`` e insira blocos de subtração 
``||math:0 - 0||`` no campo de valor da velocidade de ambos os blocos 
dos motores, substituindo os valores **0**.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0 - 0)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, 0 - 0)
        } else if (x > 60) {
        	
        } else {
        	
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 28
Em ambos as subtrações, insira a variável ``||variables:velocidade||`` no 
primeiro campo e altere o segundo de **0** para **5**.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
        } else if (x > 60) {
        	
        } else {
        	
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 29
Acesse a categoria ``||basic:Básico||`` para adicionar uma 
``||basic:pausa (ms) 100||``. Altere a duração dessa pausa de **100 ms** para
**50 ms**.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
        } else if (x > 60) {
        	
        } else {
        	
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 30
Retorne à aba ``||fuzzyBot:FuzzyBoT||`` e adicione um comando 
``||fuzzyBot:parar motor esquerdo||``. Clique na 
seta desse bloco para alterar de motor ``||fuzzyBot:esquerdo||`` para 
``||fuzzyBot:todos||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
        	
        } else {
        	
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```
## Passo 31
Prosseguindo para o próximo ``||logic:então||``, em que (**x > 60**), vamos 
duplicar os quatro blocos que posicionamos no ``||logic:então||`` anterior.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
        	
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 32
Entretanto, clique na primeira seta do primeiro comando do motor, 
``||fuzzyBot:Motor direito mover para frente com a velocidade||``,
para alterar de motor ``||fuzzyBot:direito||`` para ``||fuzzyBot:esquerdo||``.
Em seguida, inverta o segundo comando de ``||fuzzyBot:esquerdo||`` para 
``||fuzzyBot:direito||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
        	
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 33
Agora, dentro do ``||logic:senão||``, adicione um bloco de movimento dos motores:
``||fuzzyBot:Motor todos mover para frente com a velocidade 0||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 0)
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 34
Certifique-se de que estão selecionados todos os motores e, em seguida, altere
a velocidade de **0** para a própria variável ``||variables:velocidade||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
	
})
```

## Passo 35
Agora, prossiga para o laço ``||basic:sempre||``. Se necessário, adicione-o 
ao seu código a partir da aba ``||basic:Básico||``. Acesse a aba 
``||logic:Lógica||`` e adicione um ``||logic:se então senão||`` dentro desse
``||basic:sempre||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 36
Retorne à aba ``||logic:Lógica||`` e utilize um comparador 
``||logic:0 = 0||`` para substituir o **verdadeiro** desse bloco 
``||logic:se então||``. Modifique o primeiro valor desse comparador para a variável
``||variables:ligado||``, e o segundo para o número **1**.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
    	
    } else {
    	
    }
})
```

## Passo 37
Antes de prosseguir para o ``||logic:então||`` desse bloco, vamos 
definir o que acontece em seu ``||logic:senão||``. Para isso, insira um comando
``||fuzzyBot:parar motor esquerdo||`` nesse ``||logic:senão||``. Clique na seta
para alterar de motor ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
    	
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 38
Retorne à ``||logic:Lógica||`` e adicione outro ``||logic:se então senão||`` 
dentro do anterior. Insira um comparador ``||logic:0 < 0||`` no campo 
**verdadeiro** desse bloco. Em seguida, altere o sinal desse comparador de **<**
para **>**.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
        if (0 > 0) {
        	
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 39
Vá ao menu ``||Advanced:Avançado||``, acesse ``||Camera:Sensor Câmera||`` 
e selecione o bloco ``||Camera:Resultados detectados no modo Cor||`` para
substituir o primeiro campo do comparador. Clique na seta para alterar de modo 
``||Camera:Cor||`` para ``||Camera:Blob||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
        	
        } else {
        	
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 40
Aqui também vamos definir o que acontece no ``||logic:senão||`` desse novo bloco
antes de prosseguirmos ao ``||logic:então||``. Para isso, acesse a aba 
``||fuzzyBot:FuzzyBoT||`` e insira um comando
``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||`` 
nesse ``||logic:senão||``. Clique na seta para alterar de motor 
``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
        	
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 0)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 41
Substitua o valor de velocidade desse bloco de **0** pela própria variável 
``||variables:velocidade||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
        	
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 42
Agora, prosseguimos para dentro do ``||logic:então||`` desse bloco. Acesse a 
categoria ``||logic:Lógica||`` e adicione um ``||logic:se então||`` dentro do
anterior. Retorne à ``||Logic:Lógica||`` e adicione um operador Booleano ``||Logic:OU||`` 
dentro do campo **verdadeiro** desse bloco ``||Logic:Se então||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
            if (false || false) {
            	
            }
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 43
Retorne ao menu ``||Camera:Sensor Câmera||`` e adicione um bloco de bordas 
triangulares ``||Camera:Blob Vermelho detectado do resultado 1||`` em cada 
lado do operador Booleano ``||Logic:OU||``. Clique na seta do segundo para 
alterar a cor de **Vermelho** para **Verde**.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        let x = 0
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
            if (Camera.DetectedBlob(color_label_e.kColorRed, 1) || Camera.DetectedBlob(color_label_e.kColorGreen, 1)) {
            	
            }
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 44
Dentro do ``||logic:então||`` desse bloco, adicione um comando 
``||variables:definir (variável) para 0||``, localizado no menu 
``||variables:Variáveis||``. Clique na seta desse bloco para alterar para a 
variável ``||variables:x||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let x = 0
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
            if (Camera.DetectedBlob(color_label_e.kColorRed, 1) || Camera.DetectedBlob(color_label_e.kColorGreen, 1)) {
                x = 0
            }
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 45
Volte à aba ``||Camera:Sensor Câmera||`` e utilize um bloco 
``||Camera:coordenada X do resultado 1 do modo Blob||`` para substituir o valor
**0** do bloco de definição da variável ``||variables:x||``.

```blocks
function segue_cor () {
    let largura = 0
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let x = 0
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
            if (Camera.DetectedBlob(color_label_e.kColorRed, 1) || Camera.DetectedBlob(color_label_e.kColorGreen, 1)) {
                x = Camera.GetValue(sentry_obj_info_e.kXValue, 1, sengo_vision_e_1.kVisionBlob)
            }
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 46
Adicione outro bloco de definição de variável abaixo do anterior, desta vez 
para a variável ``||variables:largura||``.

```blocks
function segue_cor () {
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let x = 0
let largura = 0
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
            if (Camera.DetectedBlob(color_label_e.kColorRed, 1) || Camera.DetectedBlob(color_label_e.kColorGreen, 1)) {
                x = Camera.GetValue(sentry_obj_info_e.kXValue, 1, sengo_vision_e_1.kVisionBlob)
                largura = 0
            }
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 47
Volte à aba ``||Camera:Sensor Câmera||`` e utilize um bloco 
``||Camera:coordenada X do resultado 1 do modo Blob||`` para substituir o valor
**0** do bloco de definição da variável ``||variables:largura||``. Clique na seta
desse bloco para alterar de ``||Camera:coordenada X||`` para 
``||Camera:largura||``.

```blocks
function segue_cor () {
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let x = 0
let largura = 0
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
            if (Camera.DetectedBlob(color_label_e.kColorRed, 1) || Camera.DetectedBlob(color_label_e.kColorGreen, 1)) {
                x = Camera.GetValue(sentry_obj_info_e.kXValue, 1, sengo_vision_e_1.kVisionBlob)
                largura = Camera.GetValue(sentry_obj_info_e.kWidthValue, 1, sengo_vision_e_1.kVisionBlob)
            }
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 48
Acesse o menu ``||Functions:Funções||``, dentro de ``||Advanced:Avançado||`` e 
adicione o comando ``||Functions:ligar segue_cor||`` ainda dentro desse 
``||logic:então||``.

```blocks
function segue_cor () {
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let x = 0
let largura = 0
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
            if (Camera.DetectedBlob(color_label_e.kColorRed, 1) || Camera.DetectedBlob(color_label_e.kColorGreen, 1)) {
                x = Camera.GetValue(sentry_obj_info_e.kXValue, 1, sengo_vision_e_1.kVisionBlob)
                largura = Camera.GetValue(sentry_obj_info_e.kWidthValue, 1, sengo_vision_e_1.kVisionBlob)
                segue_cor()
            }
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 49
Acesse o menu ``||Input:Entrada||`` e adicione dois blocos 
``||Input:no botão A pressionado||`` à sua área de programação.
Altere um dos blocos de ``||Input:botão A||`` para ``||Input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
function segue_cor () {
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let x = 0
let largura = 0
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    let ligado = 0
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
            if (Camera.DetectedBlob(color_label_e.kColorRed, 1) || Camera.DetectedBlob(color_label_e.kColorGreen, 1)) {
                x = Camera.GetValue(sentry_obj_info_e.kXValue, 1, sengo_vision_e_1.kVisionBlob)
                largura = Camera.GetValue(sentry_obj_info_e.kWidthValue, 1, sengo_vision_e_1.kVisionBlob)
                segue_cor()
            }
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 50
Insira blocos ``||variables:definir (variável) para 0||`` dentro dos 
blocos ``||Input:no botão A pressionado||`` e 
``||Input:no botão B pressionado||``. Clique na seta desses blocos para selecionar
a variável ``||variables:ligado||`` e altere o valor dessa variável para **1**
dentro somente do bloco ``||Input:no botão A pressionado||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    ligado = 0
})
function segue_cor () {
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let x = 0
let largura = 0
let ligado = 0
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
            if (Camera.DetectedBlob(color_label_e.kColorRed, 1) || Camera.DetectedBlob(color_label_e.kColorGreen, 1)) {
                x = Camera.GetValue(sentry_obj_info_e.kXValue, 1, sengo_vision_e_1.kVisionBlob)
                largura = Camera.GetValue(sentry_obj_info_e.kWidthValue, 1, sengo_vision_e_1.kVisionBlob)
                segue_cor()
            }
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

## Passo 51
Transfira seu código para o micro:bit e pressione o botão A da placa para 
iniciar o seguidor de cor. Posicione balões das cores vermelho e verde à 
frente do campo de visão do FuzzyBoT para testar sua capacidade de segui-los.

```blocks
```

## Passo 52
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onButtonPressed(Button.A, function () {
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    ligado = 0
})
function segue_cor () {
    if (largura >= 80) {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    } else {
        if (x >= 40 && x <= 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        } else if (x < 40) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else if (x > 60) {
            fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade - 5)
            fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CCW, velocidade - 5)
            basic.pause(50)
            fuzzyBot.motorStop(fuzzyBot.Motors.All)
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    }
}
let x = 0
let largura = 0
let ligado = 0
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.SetParamNum(sengo_vision_e_2.kVisionBlob, 2)
Camera.SetBlobParam(5, 5, color_label_e.kColorRed, 1)
Camera.SetBlobParam(5, 5, color_label_e.kColorGreen, 2)
Camera.SetMaxBlobParam(5)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionBlob)
velocidade = 40
basic.pause(2000)
basic.forever(function () {
    if (ligado == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionBlob) > 0) {
            if (Camera.DetectedBlob(color_label_e.kColorRed, 1) || Camera.DetectedBlob(color_label_e.kColorGreen, 1)) {
                x = Camera.GetValue(sentry_obj_info_e.kXValue, 1, sengo_vision_e_1.kVisionBlob)
                largura = Camera.GetValue(sentry_obj_info_e.kWidthValue, 1, sengo_vision_e_1.kVisionBlob)
                segue_cor()
            }
        } else {
            fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.M1)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
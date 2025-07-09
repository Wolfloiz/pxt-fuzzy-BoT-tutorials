### @diffs true
# FuzzyBoT Joystick - Controle Remoto

## Passo 1
Neste tutorial, vamos programar a comunicação do Joystick com o FuzzyBoT. Ou seja,
vamos definir o que o Micro:bit do Joystick vai enviar através do rádio para o Micro:bit no robô.

## Passo 2
Para começar, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Vamos iniciar a programação configurando o grupo de rádio. Para isso, selecione o bloco ``||radio:definir grupo do rádio 1||``, na categoria 
``||radio:Rádio||``, e arraste para dentro do laço ``||basic:no iniciar||``. 

Altere o número do grupo de **1** para **255**, ou outro número próximo 
deste valor.

```blocks
radio.setGroup(255)
basic.forever(function () {
	
})
```

## Passo 4 

Esse bloco serve para garantir que todos os Micro:bits dentro desse mesmo grupo
de rádio estejam conectados uns com os outros. Portanto, certifique-se de que o grupo configurado no seu Micro:bit 
seja diferente do utilizado pelos outros grupos da sala de aula.

```blocks
radio.setGroup(255)
basic.forever(function () {
	
})
```

## Passo 5 

Agora, clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e clique em **Fazer uma função...**.
Crie uma função chamada ``||Functions:comando_joystick||``.
Um novo laço referente à função criada é adicionado automaticamente ao código.
Retorne ao menu de ``||Functions:Funções||`` e insira o comando ``||functions:Ligar comando_joystick||`` 
dentro do laço ``||basic:sempre||``.

```blocks
function comando_joystick () {
	
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
})
```

## Passo 6
Acesse a aba ``||Basic:Básico||`` e adicione o comando ``||Basic:pausa (ms) 100||``
dentro do laço ``||basic:sempre||``.

```blocks
function comando_joystick () {
	
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 7
Feito isso, prosseguiremos para a definição da função ``||Functions:comando_joystick||``.
Acesse o menu ``||radio:Rádio||`` e arraste o bloco ``||radio:rádio envia value "name" = 0||``
para dentro do laço da função. 

```blocks
function comando_joystick () {
    radio.sendValue("name", 0)
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 8
Altere o ``||radio:"name"||`` desse comando para a letra ``||radio:"E"||``, e o valor para o bloco
``||joystick:Valor da barra deslizante (E)||``, localizado no menu ``||joystick:Joystick||``.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 9
Vá ao menu ``||logic:Lógica||`` e adicione o laço ``||logic:se verdadeiro então ... senão||`` dentro do laço da 
função. Em seguida, clique no sinal de **+** na parte inferior desse bloco para transformá-lo em 
``||logic:se verdadeiro então ... senão se falso então ... senão||``.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (true) {
    	
    } else if (false) {
    	
    } else {
    	
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 10
Antes de avançar, clique no sinal de **-** à frente do ``||logic:senão||`` para transformar o bloco em
``||logic:se verdadeiro então ... senão se falso então||``. 

 **Atenção:** verifique se o seu bloco está exatamente como o estabelecido na lâmpada de dica antes de prosseguir.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (true) {
    	
    } else if (false) {
    	
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 11
Retorne à aba ``||logic:Lógica||`` e adicione um bloco comparador  ``||logic:0 < 0||`` dentro do campo 
``||logic:verdadeiro||`` e outro para o campo ``||logic:falso||``.  
**Atenção:** altere o sinal do segundo comparador de **<** para **>**.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (0 < 0) {
    	
    } else if (0 > 0) {
    	
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 12
Feito isso, acesse a aba ``||joystick:Joystick||`` e arraste dois blocos ``||joystick:Valor do eixo X da alavanca||``
para substituir o primeiro campo de ambos os comparadores.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 0) {
    	
    } else if (joystick.HorizontalStick() > 0) {
    	
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 13
Agora, substitua os valores do segundo campo de ambos comparadores por **300** e **600** respectivamente.
Assim, teremos ``||joystick:Valor do eixo X da alavanca||`` **< 300** e ``||joystick:Valor do eixo X da alavanca||`` **> 600**.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
    	
    } else if (joystick.HorizontalStick() > 600) {
    	
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 14
Em seguida, acesse o menu ``||radio:Rádio||`` e arraste o bloco ``||radio:rádio envia value "name" = 0||``
para dentro de ambos os laços ``||logic:então||``. Modifique o ``||radio:"name"||`` de ambos para ``||radio:"DIR"||``. 

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 0)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 0)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 15
Agora, altere os valores desses blocos ``||radio:rádio envia value "DIR" = 0||`` de **0** para
**1** no primeiro ``||logic:então||`` e para **2** no segundo ``||logic:então||``. 
Antes de prosseguir, confirme seu código clicando na lâmpada de dicas.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 16
Feito isso, duplique todo esse laço ``||logic:se verdadeiro então ... senão se falso então||`` clicando
com o botão direito do mouse ou copiando e colando o laço inteiro. Posicione o novo laço abaixo do anterior antes de seguir.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 17
Feito isso, altere ambos os blocos ``||joystick:Valor do eixo X da alavanca||`` pelo bloco
``||joystick:Valor do eixo Y da alavanca||`` também localizado no menu ``||joystick:Joystick||``.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 18
Modifique os valores desses blocos ``||radio:rádio envia value "DIR" = ||`` para
**3** no primeiro ``||logic:então||`` e para **4** no segundo ``||logic:então||``. 

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 19
Retorne ao menu ``||logic:Lógica||`` e adicione um laço ``||logic:se então||`` **abaixo** *(não dentro)*
dos anteriores. Volte à ``||logic:Lógica||`` e insira três operadores booleanos ``||logic: <> E <>||`` a frente desse ``||logic:se||``.
Eles devem ser posicionados um dentro do outro até que você tenha quatro espaços triangulares.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (false && (false && (false && false))) {
    	
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 20
Dentro de cada espaço desse, adicione um bloco comparador ``||logic:0 < 0||``, totalizando quatro comparadores.
Cuidado para não substituir os operadores ``||logic: <> E <>||`` nesse processo.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (0 < 0 && (0 < 0 && (0 < 0 && 0 < 0))) {
    	
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 21
Agora, vamos preencher os primeiros campos de cada ``||logic:comparador||``. Os dois primeiros comparadores serão referentes
ao ``||joystick:Valor do eixo X da alavanca||``, enquanto os dois últimos serão baseados no ``||joystick:Valor do eixo Y da alavanca||``.
Esses blocos estão localizados no menu ``||joystick:Joystick||``.  

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() < 0 && (joystick.HorizontalStick() < 0 && (joystick.VerticalStick() < 0 && joystick.VerticalStick() < 0))) {
    	
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 22
Feito isso, vamos modificar os valores dos segundos campos desses comparadores. O primeiro e terceiro devem ser **300**, enquanto o segundo e o quarto devem
ser **600**.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() < 300 && (joystick.HorizontalStick() < 600 && (joystick.VerticalStick() < 300 && joystick.VerticalStick() < 600))) {
    	
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 23
Modifique os sinais dos comparadores para **>=** no primeiro e terceiro, e **<=**
no segundo e quarto. Resumindo, devemos ter os seguintes comparadores:
- X >= 300 E
- X <= 600 E
- Y >= 300 E
- Y <= 600

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() >= 300 && (joystick.HorizontalStick() <= 600 && (joystick.VerticalStick() >= 300 && joystick.VerticalStick() <= 600))) {
    	
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 24
Dentro do ``||logic:então||`` desse laço, adicione o bloco ``||radio:rádio envia value "name" = 0||``, localizado no menu  ``||radio:Rádio||``.
Altere o ``||radio:"name"||`` para ``||radio:"DIR"||`` e o valor deve ser mantido como **0**.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() >= 300 && (joystick.HorizontalStick() <= 600 && (joystick.VerticalStick() >= 300 && joystick.VerticalStick() <= 600))) {
        radio.sendValue("DIR", 0)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 25
Feito isso, volte à aba ``||logic:Lógica||`` e adicione um laço ``||logic:se verdadeiro então ... senão||`` abaixo dos laços anteriores.
Cuidado para não posicionar dentro do laço anterior!  

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() >= 300 && (joystick.HorizontalStick() <= 600 && (joystick.VerticalStick() >= 300 && joystick.VerticalStick() <= 600))) {
        radio.sendValue("DIR", 0)
    }
    if (true) {
    	
    } else {
    	
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 26
Substitua o campo ``||logic:verdadeiro||`` por um comparador ``||logic:0 = 0||``. O primeiro campo desse comparador
deve ser alterado para o bloco ``||joystick:Botão D é pressionado||`` e o segundo valor deve ser modificado de **0** para **1**.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() >= 300 && (joystick.HorizontalStick() <= 600 && (joystick.VerticalStick() >= 300 && joystick.VerticalStick() <= 600))) {
        radio.sendValue("DIR", 0)
    }
    if (joystick.BlackUpButton() == 1) {
    	
    } else {
    	
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 27
Dentro do ``||logic:então||`` e do ``||logic:senão||`` desse laço, adicione blocos ``||radio:rádio envia value "name" = 0||``.
Altere ambos os campos ``||radio:"name"||`` para ``||radio:"D"||``. Já o campo de valor deve ser **1** para o ``||logic:então||`` e 
**0** para o ``||logic:senão||``.   

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() >= 300 && (joystick.HorizontalStick() <= 600 && (joystick.VerticalStick() >= 300 && joystick.VerticalStick() <= 600))) {
        radio.sendValue("DIR", 0)
    }
    if (joystick.BlackUpButton() == 1) {
        radio.sendValue("D", 1)
    } else {
        radio.sendValue("D", 0)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 28
Agora, devemos replicar essa lógica para os botões **C**, **B**, **A** e **eixo Z** da alavanca. Para isso,
duplique todo o laço anterior e posicione o novo abaixo do anterior.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() >= 300 && (joystick.HorizontalStick() <= 600 && (joystick.VerticalStick() >= 300 && joystick.VerticalStick() <= 600))) {
        radio.sendValue("DIR", 0)
    }
    if (joystick.BlackUpButton() == 1) {
        radio.sendValue("D", 1)
    } else {
        radio.sendValue("D", 0)
    }
    if (joystick.BlackUpButton() == 1) {
        radio.sendValue("D", 1)
    } else {
        radio.sendValue("D", 0)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 29
Altere o primeiro campo do comparador para ``||joystick:Botão C é pressionado||`` e o campo ``||radio:"name"||`` de ambos os blocos para ``||radio:"C"||``. 
  
```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() >= 300 && (joystick.HorizontalStick() <= 600 && (joystick.VerticalStick() >= 300 && joystick.VerticalStick() <= 600))) {
        radio.sendValue("DIR", 0)
    }
    if (joystick.BlackUpButton() == 1) {
        radio.sendValue("D", 1)
    } else {
        radio.sendValue("D", 0)
    }
    if (joystick.RedUpButton() == 1) {
        radio.sendValue("C", 1)
    } else {
        radio.sendValue("C", 0)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 30
Duplique o todo esse laço e faça as mesmas alterações para quando ``||joystick:Botão B é pressionado||``. 

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() >= 300 && (joystick.HorizontalStick() <= 600 && (joystick.VerticalStick() >= 300 && joystick.VerticalStick() <= 600))) {
        radio.sendValue("DIR", 0)
    }
    if (joystick.BlackUpButton() == 1) {
        radio.sendValue("D", 1)
    } else {
        radio.sendValue("D", 0)
    }
    if (joystick.RedUpButton() == 1) {
        radio.sendValue("C", 1)
    } else {
        radio.sendValue("C", 0)
    }
    if (joystick.RedFrontalButton() == 1) {
        radio.sendValue("B", 1)
    } else {
        radio.sendValue("B", 0)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 31
Repita o procedimento para o ``||joystick:Botão A é pressionado||``. 

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() >= 300 && (joystick.HorizontalStick() <= 600 && (joystick.VerticalStick() >= 300 && joystick.VerticalStick() <= 600))) {
        radio.sendValue("DIR", 0)
    }
    if (joystick.BlackUpButton() == 1) {
        radio.sendValue("D", 1)
    } else {
        radio.sendValue("D", 0)
    }
    if (joystick.RedUpButton() == 1) {
        radio.sendValue("C", 1)
    } else {
        radio.sendValue("C", 0)
    }
    if (joystick.RedFrontalButton() == 1) {
        radio.sendValue("B", 1)
    } else {
        radio.sendValue("B", 0)
    }
    if (joystick.BlackFrontalButton() == 1) {
        radio.sendValue("A", 1)
    } else {
        radio.sendValue("A", 0)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 32
O último caso deve ser feito considerando quando o ``||joystick:Botão alavanca é pressionado (Z)||``. Nessa situação,
o ``||radio:"name"||`` adotado será ``||radio:"Z"||``.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() >= 300 && (joystick.HorizontalStick() <= 600 && (joystick.VerticalStick() >= 300 && joystick.VerticalStick() <= 600))) {
        radio.sendValue("DIR", 0)
    }
    if (joystick.BlackUpButton() == 1) {
        radio.sendValue("D", 1)
    } else {
        radio.sendValue("D", 0)
    }
    if (joystick.RedUpButton() == 1) {
        radio.sendValue("C", 1)
    } else {
        radio.sendValue("C", 0)
    }
    if (joystick.RedFrontalButton() == 1) {
        radio.sendValue("B", 1)
    } else {
        radio.sendValue("B", 0)
    }
    if (joystick.BlackFrontalButton() == 1) {
        radio.sendValue("A", 1)
    } else {
        radio.sendValue("A", 0)
    }
    if (joystick.StickButton() == 1) {
        radio.sendValue("Z", 1)
    } else {
        radio.sendValue("Z", 0)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

## Passo 33
Agora seu código está pronto! Baixe-o para o micro:bit que será usado no Joystick, e 
prossiga para o tutorial de programação do micro:bit que será usado no FuzzyBoT. 

```blocks
```

## Passo 34
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
function comando_joystick () {
    radio.sendValue("E", joystick.SliderDimmer())
    if (joystick.HorizontalStick() < 300) {
        radio.sendValue("DIR", 1)
    } else if (joystick.HorizontalStick() > 600) {
        radio.sendValue("DIR", 2)
    }
    if (joystick.VerticalStick() < 300) {
        radio.sendValue("DIR", 3)
    } else if (joystick.VerticalStick() > 600) {
        radio.sendValue("DIR", 4)
    }
    if (joystick.HorizontalStick() >= 300 && (joystick.HorizontalStick() <= 600 && (joystick.VerticalStick() >= 300 && joystick.VerticalStick() <= 600))) {
        radio.sendValue("DIR", 0)
    }
    if (joystick.BlackUpButton() == 1) {
        radio.sendValue("D", 1)
    } else {
        radio.sendValue("D", 0)
    }
    if (joystick.RedUpButton() == 1) {
        radio.sendValue("C", 1)
    } else {
        radio.sendValue("C", 0)
    }
    if (joystick.RedFrontalButton() == 1) {
        radio.sendValue("B", 1)
    } else {
        radio.sendValue("B", 0)
    }
    if (joystick.BlackFrontalButton() == 1) {
        radio.sendValue("A", 1)
    } else {
        radio.sendValue("A", 0)
    }
    if (joystick.StickButton() == 1) {
        radio.sendValue("Z", 1)
    } else {
        radio.sendValue("Z", 0)
    }
}
radio.setGroup(255)
basic.forever(function () {
    comando_joystick()
    basic.pause(100)
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
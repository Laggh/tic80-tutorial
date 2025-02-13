Esse é um tutorial simples sobre o [TIC80](https://tic80.com), um computador de fantasia que te deixa criar jogos de maneira simples

## Oque você vai aprender:
- [Lua](https://www.lua.org/manual/5.1/pt/manual.html) Basico (Variaveis, funçoes, loops e condicionais)
- Usando o basico do tic80 (funçoes de terminal)
- callbacks do TIC80 (`TIC()`,`BOOT()`)
- funçoes de desenho (`cls()`, `print()`, `circ()`, `rect()`, `spr()`)
- funçoes de input (`btn()`, `btnp()`)
- funçoes de mapa (`map()`, `mget()`, `mset()`)

## Oque você vai precisar:
- [TIC80](https://tic80.com/create) (Inclue o editor e o emulador)
- Um celular ou computador

## Como abrir o tic80:
Existem varias maneiras de usar o TIC80, você pode usar o site ou o aplicativo, eu recomendo o aplicativo por ser mais facil de usar e ter suporte a CTRL+C e CTRL+V alem de manter os arquivos salvos no seu dispositivo

### Usando o site:
1. Abra o site do [TIC80](https://tic80.com/create)
2. Clique no botão `CLICK TO PLAY`
![Imagem do TIC80](imagem01.png)

### Usando o aplicativo:
1. Abra o site do [TIC80](https://tic80.com/create)
2. desça a pagina até achar a area de Downloads
3. Baixe o aplicativo para o seu dispositivo, Windows, Mac, Linux, Android (IOS não é suportado)
4. Se o arquivo estiver em um zip, extraia ele

## Usando o basico do TIC80:
Ao abrir o TIC80, você verá uma interface assim:
![Imagem do TIC80](imagem02.png)

Se você digitar `help` no terminal você verá algumas categorias para ajuda, como `version`, `api`, `buttons`, `keys`, etc...
para ver a ajuda de uma categoria, digite `help CATEGORIA` (ex: `help api`)

## Criando o seu primeiro cartucho:
Para cria um novo cartucho digite `new lua` no terminal, isso criará um novo cartucho com a lingua de programação lua, você receera a seguinte mensagem:
```
new cart has been created
```
Agora você pode começar a programar, digite `edit` ou aperte `[ESC]` para abrir o editor, você verá um codigo assim:
```lua 
(...)

t=0
x=96
y=24

function TIC()

	if btn(0) then y=y-1 end
	if btn(1) then y=y+1 end
	if btn(2) then x=x-1 end
	if btn(3) then x=x+1 end

	cls(13)
	spr(1+t%60//30*2,x,y,14,3,0,0,2,2)
	print("HELLO WORLD!",84,84)
	t=t+1
end
```

Aperte `[CTRL]+[R]` para rodar o codigo, você verá um personagem se movendo na tela, você pode usar as setas para mover o personagem
![Imagem do TIC80](imagem03.png)

Agora aperte `[ESC]` para abrir o menu, você verá varias opções como `RESUME GAME`, `RESET GAME`, `CLOSE GAME` e `OPTIONS`, você pode usar as setas para navegar e `[ENTER]` para selecionar
![Imagem do TIC80](imagem04.png)

## Introdução a Lua: sintaxe basica
Lua é uma linguagem de programação simples e poderosa, ela é usada em varios jogos e programas, ela é uma linguagem de script, oque significa que você não precisa compilar o codigo, você pode simplesmente escrever e rodar.
Porem agora vamos finalmente programar, abra o terminal e digite `new lua` para criar um novo cartucho, agora digite `edit` para abrir o editor, você verá o mesmo codigo de antes, apague tudo e escreva o seguinte codigo:
```lua
function TIC()
    cls(0) -- limpa a tela
    print("ola mundo") -- escreve "ola mundo" na tela
end
```
Aperte `[CTRL]+[R]` para rodar o codigo, você verá "ola mundo" na tela, dessa maneira:
![Imagem do TIC80](imagem05.png)

### Agora vamos explicar o codigo:
Todo programa do TIC80 PRECISA da função `TIC()`, essa funçao roda 60 vezes por segundo, ela é o coração do seu jogo, tudo que está entre ela e o `end` é executado 60 vezes por segundo.
- `cls(0)` limpa a tela, é oque faz o fundo preto atrás do texto
- `print("ola mundo")` escreve "ola mundo" na tela

Agora, tente editar os codigos, mude o texto para outra coisa como "ola amigos" ou "ola tic80", porem lembre se que qualquer texto deve estar entre aspas. Ou mude o numero da função `cls()` para mudar a cor do fundo, você pode usar qualquer numero de 0 a 15. 

## Aprendendo mais sobre as funçoes
Vamos aprender um pouco mais sobre as funçoes, vamos descobrir mais sobre a função `print()`, abra o terminal e digite `help print`, você verá a seguinte mensagem:
```	
print(text x=0 y=0 color=15 fixed=false 
scale=1 smallfont=false) -> width
(...)
```
Porem, oque isso siginifica? Esses são os **Parametros** da função `print()`, parametros são valores que você passa para a função, você já usou um desses parametros, o primeiro, chamado `text` ele é o texto que deve ser desenhado, os outros parametros são opcionais, porem dão mais controle sobre a função, vamos testar o parametro `x` e `y`, abra o editor e escreva o seguinte codigo:
```lua	 
function TIC()
	cls(0) -- limpa a tela
	print("ola mundo", 10, 10) -- escreve "ola mundo" na tela na posição 10, 10
end
```
Aperte `[CTRL]+[R]` para rodar o codigo, você verá "ola mundo" escrito em uma posição diferente, tente editar esses dois valores e veja oque acontece.

## Operadores matematicos
Lua tem varios operadores matematicos, os mais comuns são `+`, `-`, `*`, `/`, `^` e `%`, vamos aprender um pouco sobre eles, abra o editor e escreva o seguinte codigo:
```lua
function TIC()
	cls(0) -- limpa a tela
	print(1+1, 10, 10) -- escreve 2 na tela
	print(2-1, 10, 20) -- escreve 1 na tela
	print(2*2, 10, 30) -- escreve 4 na tela
	print(4/2, 10, 40) -- escreve 2 na tela
	print(2^3, 10, 50) -- escreve 8 na tela
	print(5%2, 10, 60) -- escreve 1 na tela
end
``` 
Ao rodar, você deve obter esse resultado:
![Imagem do TIC80](imagem06.png)

Não se preocupe, irei explicar oque está acontecendo:

1. Na linha 3, `print(1+1, 10, 10)` está somando **1 mais 1** e escrevendo o resultado na tela, o resultado é **2**, os outros parametros são a posição do texto na tela
2. Na linha 4, `print(2-1, 10, 20)` está subtraindo **2 menos 1** e escrevendo o resultado na tela, o resultado é **1**
3. Na linha 5, `print(2*2, 10, 30)` está multiplicando **2 vezes 2** e escrevendo o resultado na tela, o resultado é **4**
4. Na linha 6, `print(4/2, 10, 40)` está dividindo **4 dividido por 2** e escrevendo o resultado na tela, o resultado é **2**
5. Na linha 7, `print(2^3, 10, 50)` está elevando **2 a terceira potencia (2 ao cubo)** e escrevendo o resultado na tela, o resultado é **8**
6. Na linha 8, `print(5%2, 10, 60)` está pegando o **resto da divisão de 5 por 2** e escrevendo o resultado na tela, ele primeiro tenta dividir 5 por 2, o resultado é 2 com resto 1, então ele pega o resto e escreve na tela, que é **1**

### Desafio:
Agora que você entendeu os operadores matematicos, tente fazer algumas operações, descubra quanto é **127*61** apenas usando o tic 80, aqui está um codigo para te ajudar:
```lua
function TIC()
	cls(0) -- limpa a tela
	print(2+2, 10, 10) -- escreve o resultado de 127*61 na tela
end
```
<div id="acertou"> Digite uma resposta para ver se você acertou </div>
<input type="text" id="resposta" placeholder="Resposta">
<button onclick="
if(document.getElementById('resposta').value == 7747){
	document.getElementById('acertou').innerHTML = 'Parabens, você acertou!'
}else{
	document.getElementById('acertou').innerHTML = 'Tente novamente'
}
">Verificar</button>

## Variaveis
Variaveis são tipo "caixinhas" que guardam valores, você pode usar esses valores em qualquer lugar do seu codigo, vamos ver um exemplo para situações uteis dela:
```lua
function TIC()
	print("ola mundo", 10, 10)
	print("ola mundo", 10, 20)
	print("ola mundo", 10, 30)
	print("ola mundo", 10, 40) 
end
```
Vamos supor que você quer mudar o texto de todos os `print()`, você teria que mudar todos os textos, um por um, se já é chato mudar 4, imagina umas 100 linhas de codigo, é ai que as variaveis entram, você pode guardar o texto em uma variavel e usar ela em todos os `print()`, vamos ver um exemplo:
```lua
function TIC()
	texto = "ola mundo"
	print(texto, 10, 10)
	print(texto, 10, 20)
	print(texto, 10, 30)
	print(texto, 10, 40) 
end
```
Esse codigo faz a mesma coisa que o anterior, porem é mais facil de editar, você só precisa mudar o texto uma vez, tente mudar o texto da variavel `texto` e veja o resultado.

### Guardar valores
Os valores de variaveis são uteis não só para reutilizar em varios lugares, mas tambem para guardar valores que podem mudar, como a posição de um personagem, a vida de um inimigo, etc... Por enquanto, vamos fazer um exemplo simples, um contador que aumenta varias vezes por segundo
```lua
contador = 0
function TIC()
	cls(0) -- limpa a tela
	contador = contador + 1
	print(contador, 10, 10)
end
```
Primeiramente, antes de usar uma variavel, nós temos que **declarar** ela, basicamente estamos falando para o computador "Ei, eu vou usar uma variavel chamada `contador`, então se prepare", a declaração de variaveis é feita assim:
```lua
nome_da_variavel = valor
``` 

Depois disso, falamos para o computador criar a variavel antes de rodar a função `TIC()`, agora, a variavel `contador` é criada e tem o valor de `0`, na função `TIC()`, estamos falando para o computador calcular quanto é `contador + 1` e guardar o resultado na variavel `contador`, isso terá o efeito de aumentar o contador em 1 a cada vez que a função `TIC()` rodar, veja a tabela explicando
| Rodada | Valor de contador | Contador + 1 | Oque acontece |
|--|--|--|--|
| 1 | 0 | 0 + 1 = 1 | contador = 1 |
| 2 | 1 | 1 + 1 = 2 | contador = 2 |
| 3 | 2 | 2 + 1 = 3 | contador = 3 |
| 4 | 3 | 3 + 1 = 4 | contador = 4 |

E após isso, finalmente estamos escrevendo o valor de `contador` na tela, tente rodar o codigo e veja o contador aumentando, desta maneira:
![Imagem do TIC80](gif01.gif)

### Testes interessantes
Agora que você viu o contador funcionando, vamos fazer alguns testes e analizar o resultado, tente fazer esses testes:
1. Mude o valor de `contador` para `contador = contador + 2`, oque acontece?
2. Mude o valor de `contador` para `contador = contador - 1`, oque acontece?
3. Mude o valor de `contador` para `contador = contador * 2`, oque acontece?
4. Mude o valor de `contador` para `contador = contador / 2`, oque acontece?

Ou alguns testes sobre o proprio funcionamento do programa
1. Declare a variavel dentro da função `TIC()`, oque acontece?
2. Não declare a variavel, oque acontece?
3. Remova a linha `contador = contador + 1`, oque acontece?
4. Remova a linha `cls(0)`, oque acontece?

## Mais funções de desenho: `cls()`
Nós vimos a função `cls()` e `print()`, porem bem por cima, agora vamos se aprofundar mais nessas funçoes, vamos começar com a função `cls()`, veja a documentação dela digitando `help cls` no terminal:
```
---=== API ===---
cls(color=0)
```	
| Parametro | Descrição | Valor padrão |
|--|--|--|
| `color` | Cor do fundo para ser pintada | `0` |

Essa função limpa a tela, porem, ela tem um parametro, `color`. Nos exemplos anteriores, nós usamos `cls(0)`, porem você pode mudar o valor para mudar a cor do fundo, tente mudar o valor de `cls()` e veja o resultado, aqui está um exemplo:
```lua
function TIC()
	cls(1) -- limpa a tela com a cor 1
end
```
No TIC80, as cores são representadas por numeros, de 0 a 15, cada numero representa uma cor, aqui está uma tabela com as cores e seus numeros:
| Numero | Cor |
|--|--|
| `0` | Preto ou Transparente |
| `1` | Roxo |
| `2` | Vermelho |
| `3` | Laranja |
| `4` | Amarelo |
| `5` | Verde Claro |
| `6` | Verde |
| `7` | Verde Escuro |
| `8` | Azul Escuro |
| `9` | Azul |
| `10` | Azul Claro |
| `11` | Ciano |
| `12` | Branco |
| `13` | Cinza Claro |
| `14` | Cinza |
| `15` | Cinza Escuro |

Teste mudar o valor de `cls()` e veja o resultado, tente usar numeros de 0 a 15

### Testes interessantes
1. Agora tente colocar numeros maiore que 15, oque acontece?
2. Coloque numeros negativos, oque acontece?
3. Coloque numeros decimais, oque acontece?
4. Coloque letras, oque acontece?

### Desafio
Vamos fazer um desafio, tente fazer um codigo que muda a cor do fundo a cada segundo, lembre dessas coisas:
- A função `TIC()` roda 60 vezes por segundo
- A função `cls()` muda a cor do fundo
- Se você passar um numero decimal para a função `cls()`, ele vai arredondar para o numero inteiro mais proximo
- se você passar um numero mais que 15 ou menos que 0, ele vai ser convertido para 0 ou 15 respectivamente
- Você pode usar variaveis para guardar valores

Aqui está um codigo para te ajudar:
```lua
contador = 0 -- Cria a variavel contador
function TIC()
	contador = contador + 1 -- Aumenta o contador
	cls(contador/60) -- Muda a cor do fundo
end
```

## Mais funções de desenho: `print()`
Agora vamos falar sobre a função `print()`, essa função é usada para escrever texto na tela, veja a documentação dela digitando `help print` no terminal:
```
---=== API ===---
print(text x=0 y=0 color=15 fixed=false
scale=1 smallfont=false) -> width
```
| Parametro | Descrição | Valor padrão |
|-----------|-----------|--------------|
| `text`    | Texto a ser escrito | `""`  |
| `x`       | Posição X do texto | `0`   |
| `y`       | Posição Y do texto | `0`   |
| `color`   | Cor do texto | `15` (Cinza escuro)  |
| `fixed`   | Se o texto deve ser fixo | `false`  |
| `scale`   | Escala do texto | `1`  |
| `smallfont` | Se o texto deve ser pequeno | `false`  |

Antes, nós usamos apenas os parametros `text`, `x` e `y`, porem, agora, vamos usar o parametro `color`, para mudar a cor do texto, tente mudar o valor de `color` e veja o resultado, aqui está um exemplo:
```lua
cor = 1
function TIC()
	-- escreve "ola mundo" na posição 10, 10 com a cor 1 (Roxo)
	print("ola mundo", 10, 10, cor) 
end
```
Teste mudar o valor de `cor` e veja o resultado, tente usar numeros de 0 a 15

## Mais funções de desenho: `circ()`
Agora vamos finalmente ver uma função nova, a função `circ()`, essa função é usada para desenhar circulos, veja a documentação dela digitando `help circ` no terminal:
```
---=== API ===---
circ(x y radius color)
```
| Parametro | Descrição | Valor padrão |
|-----------|-----------|--------------|
| `x`       | Posição X do circulo | Nenhuma |
| `y`       | Posição Y do circulo | Nenhuma |
| `radius`  | Raio do circulo | Nenhuma |
| `color`   | Cor do circulo | Nenhuma |

Essa função desenha um circulo na tela, ela tem 4 parametros, `x` e `y` são a posição do circulo, `radius` é o raio (tamanho) do circulo e `color` é a cor do circulo, **todas esses parametros são obrigatorios** e devem ser passados na ordem certa, tente fazer um circulo na tela, aqui está um exemplo:
```lua
function TIC()
	cls(0) -- limpa a tela
	circ(64, 64, 32, 1) -- desenha um circulo na posição 64, 64 com raio 32 e cor 1 (Roxo)
end
```

### A função `circb`
A função `circb()` é parecida com a função `circ()`, porem, ela desenha apenas a borda do circulo, veja o exemplo:
```lua
function TIC()
	cls(0) -- limpa a tela
	circ(64, 64, 16, 1) -- desenha um circulo na posição 64, 64 com raio 32 e cor 1 (Roxo)
	circb(128, 64, 16, 2) -- desenha a borda do circulo na posição 64, 64 com raio 32 e cor 2 (Vermelho)
end
```
![Imagem do TIC80](imagem07.png)

## Mais funções de desenho: `rect()`
Agora vamos ver a função `rect()`, essa função é usada para desenhar retangulos, veja a documentação dela digitando `help rect` no terminal:
```
---=== API ===---
rect(x y w h color)
```
| Parametro | Descrição | Valor padrão |
|--|--|--|
| `x` | Posição X do retangulo | Nenhuma |
| `y` | Posição Y do retangulo | Nenhuma |
| `w` | Largura do retangulo | Nenhuma |
| `h` | Altura do retangulo | Nenhuma |
| `color` | Cor do retangulo | Nenhuma |

Essa função desenha um retangulo na tela, ela tem 5 parametros, `x` e `y` são a posição do retangulo, `w` é a largura do retangulo, `h` é a altura do retangulo e `color` é a cor do retangulo, **todas esses parametros são obrigatorios** e devem ser passados na ordem certa, tente fazer um retangulo na tela:
```lua
x = 32
y = 32
w = 64	
h = 32

function TIC()
	cls(0) -- limpa a tela
	rect(x, y, w, h, 1) -- desenha um retangulo na posição 32, 32 com largura 64, altura 32 e cor 1 (Roxo)
end
```

## condicionais
Condicionais, ou "ifs" são uma das bases da programação, eles são usados para fazer decisões, como "Se a vida do jogador for menor que 0, então ele morreu", ou "Se o jogador apertar o botão "A", ele pula", vamos ver um exemplo simples de um if:
```lua
vida = 100
function TIC()
	if vida > 0 then
		print("O jogador esta vivo", 10, 10)
	end
end
```
Antes de qualquer coisa, temos que analisar a sintaxe do if, ele é feito assim:
```lua
if CONDIÇÃO then
	-- codigo
end
```
O if começa com a palavra chave `if`, seguido de uma condição (como `vida > 0`), depois disso, temos a palavra chave `then`, que indica que o bloco de codigo do if começou, depois disso, temos os codigos que irão ser rodados se a condição for verdadeira, depois temos a palavra chave `end`, que indica que o bloco de codigo do if terminou, se a condição for falsa, o codigo dentro do if é ignorado.

Agora voltando para o codigo anterior, rode ele, vocé verá "O jogador está vivo" na tela, pois no if, verificamos se `vida` é maior que 0, e como `vida` é 100, a condição é verdadeira, então o codigo é rodado, agora tente mudar o valor de vida para outro valor, como 0 por exemplo, e veja o resultado.

### O uso do `else`
O `else` é usado para rodar um bloco de codigo se a condição do if for falsa, dessa maneira:
```lua
if CONDIÇÂO then
	-- codigo da condição verdadeira
else
	-- codigo da condição falsa
end
```
Agora vamos editar o codigo anterior para usar o `else`:
```lua
vida = 100
function TIC()
	if vida > 0 then
		print("O jogador esta vivo", 10, 10)
	else
		print("O jogador morreu", 10, 10)
	end
end
```
Agora, se a vida for maior que 0, ele escreve "O jogador está vivo", se não, ele escreve "O jogador morreu", tente mudar o valor de vida e veja o resultado.

## Operadores Logicos Matematicos
No ultimo codigo, nós utilizamos o operador `>` (maior que), porem ele não é o unico operador logico, existem varios outros, veja a tabela dos principais
| Operador | Descrição | Exemplo | Resultado |
|--|--|--|--|
| `>` | Maior que | `5 > 3` | Verdadeiro |
| `>=` | Maior ou igual a | `5 >= 5` | Verdadeiro |
| `<` | Menor que | `5 < 3` | Falso |
| `<=` | Menor ou igual a | `5 <= 3` | Falso |
| `==` | Igual a | `5 == 3` | Falso |
| `~=` | Diferente de | `5 ~= 3` | Verdadeiro |

vamos fazer um exemplo simple para testar esses operadores e variaves:
```lua
x = 5
y = 3
function TIC()
	cls(0) --não se esqueça de limpar a tela

	if x > y then --condição
		print("x e maior que y", 10, 10) --codigo se a condição for verdadeira
	end
	if x < y then --condição
		print("x e menor que y", 10, 20) --codigo se a condição for verdadeira
	end
	if x == y then --condição
		print("x e igual a y", 10, 30) --codigo se a condição for verdadeira
	end
	if x ~= y then --condição
		print("x e diferente de y", 10, 40) --codigo se a condição for verdadeira
	end

end
```
Tente mudar os valores de `x` e `y` e veja o resultado, tente usar elses tambem para testar o codigo

### Desafio
Agora que você entende condicionais e operadores logicos e funçoes de desenho, tente fazer um codigo que desenha um circulo, que vai para a direta, e quando ele chegar no final da tela, ele volta para o começo, lembre se dessas coisas:
1. A largura da tela é `240px`
2. A função `circ()` desenha um circulo e tem os parametros `(x, y, raio, cor)`
3. para somar um valor a uma variavel, você pode usar `variavel = variavel + valor`
4. para mover algo para a **direita** você aumenta o seu `x`, para mover para a **esquerda** você diminui o seu `x`
5. Se o circulo passar do final da tela, você pode usar um if para mudar a posição dele para o começo da tela
6. Lembre-se de definir as variaveis **FORA** da função `TIC()`

> [!WARNING]
> A seguir está uma solução para o desafio, tente fazer o desafio antes de ver a solução, a melhor maneira de aprender é tentando, porem sé precisar de ajuda, a solução está aqui

```lua
x = 0
LARGURA = 240
function TIC()
	cls(0)
	circ(x, 64, 16, 1)
	x = x + 1
	if x > LARGURA then
		x = 0
	end
end
```
O uso da **constante** `LARGURA` é para facilitar a edição do codigo, iremos aprender mais sobre constantes mais tarde.

## Nomes de variaveis e constantes
Nós já aprendemos sobre como usar variaveis, porem algo importante que devemos aprender é como nomear elas de uma maneira que evita erros e deixa o codigo mais facil de entender, aqui estão algumas regras e dicas para nomear variaveis:

#### 1. Não use palavras reservadas
Toda lingua de programação tem palavras reservadas, que são palavras que tem um significado especial para o computador, como o `if` e o `then` por exemplo, imagine o computador tentando entender esse codigo:
```lua
if = 10
then = 20

if if > then then
	--codigo
end
```
O computador não teria ideia doque fazer, pois o `if` e o `then` são palavras reservadas, então **não use palavras reservadas como nomes de variaveis**

#### 2. Não coloque espaços
Espaços são usados para separar palavras, então se você colocar um espaço no nome de uma variavel, o computador vai achar que a segunda palavra é outra variavel ou comando, veja esse exemplo:
```lua
variavel legal = 10
```
O computador vai ler a primeira palavra `variavel` perfeitamente, porem quando ele chegar no espaço, ele vai achar que a variavel acabou, então ele vai tentar ler a palavra `legal` como um comando, e vai dar erro, então **não use espaços no nome de variaveis**

#### 3. CamelCase
As vezes é necessario colocar mais de uma palavra em uma variavel, porem já vimos que isso é impossivel, para isso existe o `CamelCase`, que é uma convenção de nomear variaveis com mais de uma palavra, veja alguns exemplos
| Nome | CamelCase |
|--|--|
| Nome do jogador | `nomeDoJogador` |
| Vida do jogador | `vidaDoJogador` |
| Posição x | `posicaoX` |
| Posição y | `posicaoY` |

O camelCase consiste em juntar todas as palavras e colocar a primeira letra de cada palavra em maiusculo, menos a primeira

#### 4. Nomes curtos e descritivos
A maneira que você nomeia suas variaveis ajuda muito na hora de criar coisas novas, pois mesmo que o computador entenda o codigo, você não vai entender oque ele faz, vamos ver um exemplo de um codigo completamente funcional, porem que ninguem entende:
```lua
v1 = 10
v2 = 20
v3 = 12
v4 = 5
v5 = 240
function TIC()
	v1 = v1 + 1
	if v1 > v5 then
		v1 = 0
	end
	circ(v1, v2, v3, v4)
end
```
Esse codigo é completamente funcional, porem é dificil de entender, talvez você consiga deduzir oque ele faz pelo seu tamanho curto, porem imagina você tentar deduzir variaveis para um codigo com mais que 100 linhas, agora veja o mesmo codigo, porem com variaveis descritivas:
```lua
x = 10
y = 20
raio = 12
cor = 5
larguraTela = 240
function TIC()
	cls(0)
	x = x + 1
	if x > larguraTela then
		x = 0
	end
	circ(x, y, raio, cor)
end
```

Outra coisa para se analizar é o tamanho das variaveis, talvez você pense "Ah, mas eu posso usar `posicaoHorizontalDaBola`, porem imagina ter que escrever essa variavel toda vez que for usar ela, então tente achar um equilibrio entre o tamanho e a descrição da variavel, nesse exemplo, seria bom usar um nome como `x` ou se tiverem multiplas coisas que podem ter um "x" chamar de `bolaX`.

#### 5. Mais regras de nomeação
Existem outras regras de nomeação de variaveis, veja:

1. **Não use acentos ou caracteres especiais** - O computador pode não entender esses caracteres, ou achar que um asterisco, por exemplo, é um simbolo de multiplicação, então por isso não use caracteres especiais (`ç á é ã @ # $ % & *`)

2. **Não use numeros no começo** - O computador pode achar que você está tentando fazer uma operação matematica, então não use numeros no começo de uma variavel (`1vida`, `2nome`, `3x`)

#### 6. Constantes
Constantes são como variaveis, caixinhas que armazenam valores, porem elas são **constantes**, ou seja, ao contrario das variaveis, que são feitas para ter seu valor mudado varias vezes, as constantes são feitas para ter seu valor fixo, que é raramente ou nunca editado, para o computador variaveis e constantes são a mesma coisa, porem para o programador, elas tem um significado diferente, veja um exemplo de uma constante:
```lua
LARGURA_TELA = 240
function TIC()
	cls(0)
	print("A largura da tela e ", 10, 10)
	print(LARGURA_TELA, 10, 20)
end
```
Para facilitar o reconhecimento delas, as constantes são nomeadas completamente em maiusculo, usando Underline(`_`) para separar palavras, isso é uma convenção, não uma regra, porem é bom seguir ela, pois ajuda a diferenciar variaveis de constantes

Porem você deve estar pensando, quando é util usar constantes? Bem, constantes são uteis para valores que são usados varias vezes no codigo, como a largura da tela, a altura da tela, cores, etc... Porem, constantes são uteis para valores que são usados em varios lugares, pois se você precisar mudar o valor, você só precisa mudar em um lugar, e não em varios, veja um exemplo:
```lua
LARGURA_TELA = 240
ALTURA_TELA = 136
COR_FUNDO = 0
function TIC()
	cls(COR_FUNDO)
end
```
Se você precisar mudar a cor do fundo, você só precisa mudar o valor de `COR_FUNDO`, e não em todos os `cls()`, isso é util para evitar erros e facilitar a edição do codigo

Outro lugar que é util para constantes, neste caso especificamente para o TIC80 são as cores, pois as cores são representadas por numeros, e é dificil lembrar o numero de cada cor, então é bom usar constantes para isso, veja um exemplo:
```lua
PRETO = 0
ROXO = 1
VERMELHO = 2
LARANJA = 3
AMARELO = 4
VERDE_CLARO = 5
(...)

function TIC()
	cls(PRETO)
	rect(10, 10, 40, 30, AMARELO)
end
```
Dessa maneira, você pode usar o nome da cor ao inves do numero, oque deixa o codigo mais facil de entender, porem, você pode usar numeros se quiser, porem é bom usar constantes para facilitar a leitura do codigo

## Interação do jogador
Você provavelmente deve estar se perguntando "ok, eu sei como desenhar coisas, sei como verificar condições, porem como que eu faço meu jogo ser um jogo?", A resposta é interação do jogador, no TIC80 você tem 3 metodos de interação:

1. **Botões** - O TIC80 tem 8 botões, `cima`,`baixo`,`esquerda`,`direita`,`A`,`B`,`X` e `Y`, no celular, esses botões aparecem na tela, no computador você pode usar seu teclado para simular eles.

2. **Teclado** - Você pode usar teclado para interagir com o TIC80, tendo suporte para 94 teclas

3. **Mouse** - Você pode usar o mouse para interagir tambem, no celular você usa o mouse clicando na tela

Agora vamos ver com mais detalhe como usar essas interações

## Botões









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

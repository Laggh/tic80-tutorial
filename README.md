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


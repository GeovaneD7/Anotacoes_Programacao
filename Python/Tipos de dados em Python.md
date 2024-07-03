O Python faz a inferência do tipo de dado quando ele recebe uma atribuição de variável. Muitas das vezes não é necessário imprimir qual o tipo de dado que será usado, mas se for necessário o python também é capaz de definir o tipo de dado quando este for expressado.

Ao ser definido um dado o interpretador analisa aquele dado para saber qual tipo de dado ele se encaixa, e guarda na memória (em bytes) qual o tipo daquele dado ( `type(<objeto>)` ), o seu valor em binário ( `bin(<objeto>)` ) e qual atribuição (variável ou constante) foi dada à aquele dado. Tudo isso é também gravado em um bloco na memória( `id(<objeto>)` ).

Em python tudo que começa com `0b` é um numero binário.

classe, categoria e tipo são as mesmas coisas

---
### Dados primários / Scalar 
Representam um único valor associado a um objeto.
`dir(<type>)`
	 Mostra todos os métodos que podem ser usado com aquele tipo. Onde os métodos que não possuírem dunder(`__`) são métodos que "podem" ser chamado diretamente com o objeto.
		ex: `int.bit_lengt()` 


##### int
números inteiros
##### float
decimais
##### bool
Em Python o booleano deve ser escrito iniciando em letra maiúscula, como em `True` e `False`.
Além disso um texto vazio também é considerado um booleano negativo. Ex: `"" == False`.
Qualquer número inteiro é considerado True e todo 0  é considerado False.
##### NoneType
Também chamado de Valor Nulo. Usado para definir um valor que não foi estabelecido ainda para um objeto (semelhante ao `NULL` em linguagem SQL).
É um objeto de característica *singleton*, que quer dizer que somente um único objeto NoneType é criado na memória independentemente de quantos objetos fazerem uso dele, todos terão o mesmo id na memória.

```
nulo = None
type(nulo)
NoneType
```

---
### Dados compostos

##### Tuple / tupla
Lista de objetos ==IMUTÁVEIS== organizados entre parênteses separados por vírgula
Ex
```python
dados = "Eu", 25, True, None, 3.25
('Eu', 25, True, None, 3.25)
```

Todos os métodos de  [[Cortar textos(string)]] funcionam normalmente e da mesma forma para tuplas. 

Para desempacotar tuplas é necessário criar novas variáveis, normalmente associando o conteúdo de cada índice a um nome que representa aquele conteúdo.

Ex:
```:n
coordenada = (5, 3, 1)
x = coordenada[0]
y = coordenada[1]
z = coordenada[2]
```

Alternadamente pode ser usado a seguinte sintaxe para automatizar esse processo, a quantidade de objetos devem ser iguais
	`x, y, z = coordenada`

Além disso pode ser usado um asterisco `*` para associar todos os outros objetos a uma única variável.
```
pontos = x, y, z
x, *_ = pontos
```
_Por convenção, todo objeto em uma underline é considerado descartável para aquele programa_

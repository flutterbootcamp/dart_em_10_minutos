# **Introdução**

Com este guia você aprenderá **tudo** o que é necessário sobre o Dart, para começar sua jornada com o Flutter.

> Dart é a [**melhor**](https://www.youtube.com/watch?v=J5DQRPRBiFI) linguagem de programação já feita pelo Google.


---

## **Sumário**
  - [**Por que o Flutter usa Dart?**](#por-que-o-flutter-usa-dart)
  - [**Conceitos fundamentais**](#conceitos-fundamentais)
  - [**`main()`**](#main)
  - [**Tipos de dados**](#tipos-de-dados)
  - [**Variáveis**](#variáveis)
  - [**Inferência**](#inferência)
  - [**`var / const / final`**](#var--const--final)
  - [**Null Safety**](#null-safety)
  - [**Operadores**](#operadores)
  - [**```if```**](#if)
  - [**```switch```**](#switch)
  - [**```while```**](#while)
  - [**```for```**](#for)
  - [**Funções**](#funções)
  - [**Classes**](#classes)
  - [**Herança**](#herança)
  - [**Coleções**](#coleções)
  - [**```try / catch / finally```**](#try--catch--finally)
  - [**`Future`**](#future)
  - [**`async / await`**](#async--await)
  - [**E agora?**](#e-agora)
  - [**Referências**](#referências)

---

## **Por que o Flutter usa Dart ?**

Dart oferece 2 modos de execução distintos:

1. **Interpretado (JIT - Just-In-Time):**
   - Utilizado durante o desenvolvimento
   - Permite hot-reload para atualizações rápidas
   - Código interpretado em tempo real pela Dart VM

2. **Compilado (AOT - Ahead-Of-Time):**
   - Utilizado para a publicação dos aplicativos
   - Código pré-compilado para código de máquina nativo
   - Oferece inicialização rápida e alto desempenho

Assim, proporciona equilíbrio entre produtividade (do desenvolvedor) e desempenho (do aplicativo): 

> #### **Interpretado** (JIT = **j**ust-**i**n-**t**ime): O código é interpretado e executado em tempo real pela Dart VM (*virtual machine*), semelhante a linguagens como Python ou Javascript. Essa abordagem é particularmente benéfica durante o desenvolvimento, possibilitando o hot-reload. Isso significa que as alterações no código são injetadas em um aplicativo em execução sem a necessidade de reinicialização. Este modo é utilizado para o desenvolvimento dos aplicativos.

---
 
> #### **Compilado** (AOT = **a**head **o**f **t**ime): O código é pré-compilado em código de máquina nativo, semelhante a linguagens como Java ou Swift. Esta abordagem aumenta significativamente a velocidade de inicialização e o desempenho geral. Este modo é utilizado para a publicação dos aplicativos.

### **E qual a vantagem?** 

Ao oferecer os modos JIT e AOT, o Dart fornece um equilíbrio único entre produtividade do desenvolvedor e desempenho do aplicativo.

*Para desenvolvedores:* Uma experiência incrível, pois o código é interpretado e as alterações são refletidas em menos de 2 segundos.

*Para os usuários:* Um aplicativo altamente performático, já que o código foi compilado para a plataforma nativa na qual está sendo executado.

Esta versatilidade é uma razão chave pela qual o Flutter utiliza o Dart.

|                 | Interpretado (JIT)                            | Compilado (AOT)                             |
|-----------------|-----------------------------------------------|---------------------------------------------|
| **Código**      | Interpretado e executado em tempo real        | Pré-compilado em código de nativo           |
| **Semelhança**  | Python, JavaScript                            | Java, Swift                                 |
| **Uso**         | Desenvolvimento                               | Produção                                    |
| **Vantagem**    | Hot-reload                                    | Performance                                 |
| **Execução**    | Lenta                                         | Rápida                                      |

Caso queira se aprofundar, recomendo os materiais abaixo:

[Primeiro artigo sobre este assunto](https://hackernoon.com/why-flutter-uses-dart-dd635a054ebf)

[Documentação oficial do Flutter](https://flutter.dev/docs/resources/faq#why-did-flutter-choose-to-use-dart)

[Vídeo no canal do Flutter](https://www.youtube.com/watch?v=5F-6n_2XWR8&ab_channel=Flutter)

---

## **Conceitos fundamentais**

- É uma linguagem **tipada**, porém a declaração de tipos é opcional.
- Tudo em Dart é um objeto (instância de `Object`), exceto `null`.
- Null safety: variáveis não aceitam `null` por padrão (é necessário declarar **explicitamente** esta possibilidade). 

--- 

## **`main()`**
Todo programa Dart (e aplicativos em Flutter, são programas Dart), iniciam na função `main()`:

```dart
void main() {
  print('Flutter Bootcamp');
}
```
## **Tipos de dados**

Básicos:

- Numérico: `int` e `double`
- Literal: `String`
- Booleano: `true` e `false`
- Coleções: `List`,`Sets` e `Maps`
- `null`

Especiais:
- `Object`: A **super classe** do Dart. Todos os objetos são herdados dela, com exceção do tipo `Null`.
- `Future` e `Stream`: Utilizadas para operações assíncronas.
- `dynamic`: Desabilita a tipagem do Dart e permite que qualquer tipo de dados seja utilizado.
- `void`: Utilizado como retorno (geralmente). Indica que este valor nunca é usado.


## **Variáveis**

Variáveis armezenam referências. E em Dart, podemos declarar variáveis informando o seu tipo ou não (*a tipagem é opcional*):

```dart
String bootcamp = 'Flutter Bootcamp';
// bootcamp é uma variável do tipo String
```

E esta sintaxe se aplica para todos os outros tipos de dados:

```dart
int lancamento = 2024;
double versao = 2.0;
List<String> aplicativos = ['Tempus', 'Menuo', 'Libria', 'Civitas'];
Map<String, Object> informacoes = {
  'tags': ['flutter','dart'],
  'descricao': 'Treinamento completo em Flutter',
  'aplicativos': 6
};

```

## **Inferência**

A declaração de tipos em Dart é opcional, ou seja, ambas declarações abaixo são válidas:

```dart
//tipo String declarado
String bootcampTipado = 'Flutter Bootcamp';

// tipo não declarado
var bootcampSemTipo = 'Flutter Bootcamp';
```

Por **inferência**, o Dart consegue identificar que `bootcampSemTipo` é do tipo `String` devido ao valor atribuido.

E o mesmo se aplica para todos os outros tipos de dados. 

```dart
// int
var lancamento = 2024;

// double
var versao = 1.0;

// List<String>
var aplicativos = ['Tempus', 'Menuo', 'Libria', 'Civitas'];

// Map<String, Object>
var informacoes = {
  'tags': ['flutter','dart'],
  'descricao': 'Treinamento completo em Flutter',
  'aplicativos': 6
};
```

## **`var / const / final`**

Estes são os modificadores possíveis ao declarar variáveis:

- **var:** Permite que o valor seja alterado.

- **final:** O valor não pode ser alterado e **não** é conhecido em tempo de execução.

- **const:** O valor não pode ser alterado e ja é conhecido em tempo de execução.

> Sempre que possível, utilize `const`.

## **Null Safety**

Por padrão, o Dart não aceita variáveis com valor `null`. Sendo mandatório iniciar a variável com um valor.

Para que uma variável aceite valor `null`, devemos declarar explicitamente, caso contrário, o compilador indicará um erro:

```dart
int idade;
print(idade);

❌ The non-nullable local variable 'idade' must be assigned before it can be used.
```

Este erro ocorre pois estamos acessando `idade` antes de atribuir um valor à ela. 

Ao utilizar o operador `?`, indicamos ao compilador que a variável pode ter valor `null`.

```dart
int? idade;
print(idade);

✅ será imprimido o valor null
```

## **Operadores**

Dart possui todos os tipos de operadores tradicionais: `==`, `!=`, `&&`, `||`, `>`, `>=`, `+=`, `!`,  e muitos outros.

Porém, precisamos destacar 3 que são amplamente utilizados:

 - `?` - Indica que uma variável pode ter valor `null`.
 - `??` - Retorna o valor da 1a expressão **não** seja `null`. Se for `null`, retorna a 2a expressão.
  - `:` - Se a condição for `true`, retorna o valor da 1a expressão. Caso **não** seja `null`, retorna a 2a expressão.

	```dart 
	// O valor null não pode ser atribuído à variavel mes
	int mes = null; 

	// Em ambas declarações, o valor de mes é null.
	int? mes = null;
	int? mes;
	
	// anoAtual possui valor de 2024, pois ano é null
	int? ano;
	var anoAtual = ano ?? 2024;
	
	// maiorIdade possui valor true, pois (idade é maior que 18) 
	var idade = 34;
	var maiorIdade = idade > 18 ? true : false;
	```

## **```if```**

```dart
if (condicao) {

} else if (outraCondicao){

} else {

}
```

## **```switch```**
```dart
switch (variavel) {
  case valor1: 
	break;
  case valor2:
	break;
  default; // opcional, acionado caso variavel não seja valor1 ou valor2		
}
```

## **```while```**


```dart

var mes = 1;
while (mes < 13) {
  mes++;
}

var ano = 2024;
do {
  ano++;
} while (ano < 2050);
```

## **```for```**

```dart
for (var i = 0; i < 5; i++) {

}

for (var item in minhaLista) {

}
```


## **Funções**

São instruções de código executadas em sequência.

No Dart, são objetos do tipo `Function`, ou seja, podem ser atribuídas a variáveis ou passadas como parâmetros.

```dart
bool isMaiorDeIdade(int idade) {
  return idade >= 18;
}

// se a função possui apenas 1 instrução, pode ser declarada com =>
bool isMaiorIdade(int idade) => idade > 18;
```

## **Classes**

Fornecem uma estrutura para a criação de **objetos**.

```dart
class FlutterBootcamp {

  // atributos
  int? aplicativos;
  String? descricao;
  List<String>? tags;

  // construtor default(opcional, não é necessário declarar)
  FlutterBootcamp();

  // construtor com parâmetros
  FlutterBootcamp(this.aplicativos, this.descricao, this.tags);

  // funções
  void exibirConteudo(){
    print('Construa $aplicativos aplicativos com Flutter!');
  }

}
```

Há também os `named constructors`, que permitem criar a instância do objeto com valores específicos.

```dart
class Carro{
  String? marca;
  int? ano;
  double? motor;

  Carro.popular(){
    motor = 1.0;
  }

  Carro.novo():
    ano = 2024;

  Carro.tesla(this.ano, this.motor):
    marca = 'Tesla';
}

// gol possui motor=1.0
var gol = Carro.popular();

// corollaCross possui ano=2024
var corollaCross = Carro.novo();

// modelS possui marca='Tesla', ano=2020, motor=2.0
var modelS = Carro.tesla(2020, 2.0);
```
## **Herança**

É um padrão da orientação à objetos que permite a criação de **subclasses**.

No Dart, utilizamos a palavra-chave `extends` para indicar que uma classe é *filha* de outra.

```dart
class Bootcamp {
  String? linguagem;
  Bootcamp(this.linguagem);
  void basico() {
    print('Conceitos Básicos OO');
    conteudo();
  }

  void conteudo() {
    print('Objetos, Herança, Encapsulamento');
  }
}

class FlutterBootcamp extends Bootcamp {
  FlutterBootcamp(super.linguagem);
  aprenderDart() {
    super.basico();
    super.linguagem = 'Dart';
  }

  @override
  void conteudo() {
    print('Tipos de dados e construtores');
  }
}
```

## **Coleções**

```dart
// list
var aplicativos = ['libria', 'menuo', 'civitas'];

// set
var aplicativos = {'libria', 'menuo', 'civitas'};

// map
var aplicativos = {
  1 : 'libria', 
  2 : 'menuo', 
  3 : 'civitas'
 };
```
## **```try / catch / finally```**

```dart
try {
  // código que pode gerar erro
} catch (e) {
  // executado caso ocorra erro
} finally { // opcional
  // executado independente de ter ocorrido erro ou não
}
```

## **Future**

São objetos utilizados para tratar operações assíncronas (sem sincronia), como:

- Consumir uma API; 
- Operações em banco de dados;
- Ler / gravar em um arquivo.

> Qualquer operação que não seja concluída **imediatamente** é uma operação *assíncrona*.

Future é um objeto que representa uma operação assíncrona. Assim que a operação for concluída, o valor está pronto para ser usado.

```dart
Future<int?> buscarApi() async {
  // Future.delayed: simula uma operação assíncrona
  return Future.delayed(Duration(seconds: 2), () => 2);
}

void consultarTotalCommits() {
  Future<int?> totalCommits = buscarApi();
  totalCommits.then((total) => print(total));
}

void main() => consultarTotalCommits();
```

O compilador **não** irá esperar o retorno da API continuar o processamento.

## **`async / await`**

As palavras-chave `async` e `await`, permitem escrever código com operações assíncronas similar à **operações síncronas**.

O código anterior, com `async` e `await`, poderia ser escrito da seguinte forma:

```dart
// deve-se usar async para indicar o uso do await dentro de uma função
void consultarTotalCommits() async {
  // usando o await, fará o compilador esperar até que buscarApi() conclua seu processamento
  int totalCommits = await buscarApi();
  tratarRetorno(total);
}
```

O compilador **irá** esperar o retorno da API para continuar o processamento.

## **E agora ?**

### Parabéns! 👏 

Tudo sobre linguagem Dart necessário para começar com Flutter já foi apresentado. 

A documentação oficial do Dart é uma ótima fonte de conhecimento:

- [Introduction to Dart](https://dart.dev/samples)
- [Effective Dart](https://dart.dev/guides/language/effective-dart)
- [Dart Tutorials](https://dart.dev/tutorials)

#### Bons estudos 📖
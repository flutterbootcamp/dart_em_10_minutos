# **Introdução**

Com este guia você aprenderá **tudo** o que é necessário sobre o Dart, para começar sua jornada com o Flutter.

> Dart é a [**melhor**](https://www.youtube.com/watch?v=J5DQRPRBiFI) linguagem de programação já feita pelo Google.


---

## **Sumário**
  - [**Por que o Flutter usa Dart?**](#por-que-o-flutter-usa-dart)
  - [**Conceitos importantes**](#conceitos-importantes)
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

Dart é uma linguagem de programação versátil que oferece 2 modos de execução distintos:

> #### **Interpretado** (JIT = **j**ust-**i**n-**t**ime): O código é interpretado e executado em tempo real pela Dart VM (*virtual machine*), semelhante a linguagens como Python ou Javascript. Essa abordagem é particularmente benéfica durante o desenvolvimento, possibilitando o hot-reload. Isso significa que as alterações no código são injetadas em um aplicativo em execução sem a necessidade de reinicialização. Este modo é utilizado para o desenvolvimento dos aplicativos.

---
 
> #### **Compilado** (AOT = **a**head **o**f **t**ime): O código é pré-compilado em código de máquina nativo, semelhante a linguagens como Java ou Swift.Esta abordagem aumenta significativamente a velocidade de inicialização e o desempenho geral. Este modo é utilizado para a publicação dos aplicativos.  

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

## **Conceitos importantes**

- É uma linguagem **tipada**, porém a declaração de tipos é opcional.
- Tudo em Dart é uma instância de `Object`. Qualquer coisa que possa ser armazenada em uma variável. Com exceção de `null`.
- Variáveis não podem ser declaradas com valores `null`. Para que elas aceitem, precisa-se declarar **explicitamente** esta possibilidade. 

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

Existem ainda os tipos `Symbols` e `Runes` mas provavelmente não utilizará nenhum deles.

Especiais:
- `Object`: A **super classe** do Dart. Todos os objetos são herdados dela, com exceção do tipo `Null`.
- `Future` e `Stream`: Utilizadas para operações assíncronas.
- `dynamic`: Desabilita a tipagem do Dart e permite que qualquer tipo de dados seja utilizado.
- `void`: Utilizado como retorno (geralmente). Indica que este valor nunca é usado.


## **Variáveis**

Variáveis armezenam referências. E em Dart, podemos declarar variáveis informando o seu tipo ou não (*a tipagem é opcional*):

```dart
String bootcamp = 'Flutter Bootcamp';
```

Neste caso, `bootcamp` armazena a referência para um objeto do tipo `String` com o valor de "Flutter Bootcamp".

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

**var:** Permite que o valor atribuído seja alterado.

**final:** O valor não pode ser alterado e **não** é conhecido em tempo de execução.

**const:** O valor não pode ser alterado e ja é conhecido em tempo de execução.

> Sempre que possível, utilize `const`.

## **Null Safety**

Desde a versão [2.12](https://medium.com/dartlang/announcing-dart-2-12-499a6e689c87) (liberada em março de 2021), Dart suporta o modo `null safety` por padrão.

Isso significa que devemos declarar explicitamente que uma variável pode ter valor `null`. Caso contrário, o compilador indicará um erro:.

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

Dart é uma linguagem moderna e possui todos os tipos de operadores tradicionais:

`==`, `!=`, `&&`, `||`, `>`, `>=`, `+=`, `!`,  e muitos outros.

Porém, precisamos destacar 3 que são amplamento utilizados:

 - `?` - Indica que uma variável pode ter valor `null`:

	```dart 
	// O valor null não pode ser atribuído à variavel ano
	int ano = null; 

	// Em ambas declarações, o valor de ano é null.
	int? ano = null;
	int? ano;
	```
 - `??` - Retorna o valor da 1a expressão **não** seja `null`. Se for `null`, retorna a 2a expressão:
 	```dart 
	// anoAtual possui valor de 2024, pois ano é null
	int? ano;
	var anoAtual = ano ?? 2024;
	```

 - `:` - Se a condição for `true`, retorna o valor da 1a expressão. Caso **não** seja `null`, retorna a 2a expressão:
 	```dart 
	// maiorIdade possui valor true, pois (idade é maior que 18) 
	var idade = 34;
	var maiorIdade = idade > 18 ? true : false;
	```

## **```if```**

```dart
if (condicao) {

}
```

```dart
if (condicao) {

} else {

}
```

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
var ano = 2024;
while (ano < 2050) {
  ano++;
}
```

```dart
var ano = 2024;
do {
  ano++;
} while (ano < 2050);
```


## **```for```**

```dart
for (var i = 0; i < 5; i++) {

}
```

```dart
for (var item in minhaLista) {

}
```


## **Funções**

São instruções de código que executadas em sequência.

Em Dart funções são objetos e do tipo `Function`, ou seja, podem ser atribuídas às variáveis ou passadas como parâmetros.

```dart
bool isMaiorDeIdade(int idade) {
  return idade >= 18;
}
```

Funções que executam apenas 1 instruçãos, podem ser declaradas usando a sintáxe `=>` :

```dart
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

  // construtor default(opcional)
  FlutterBootcamp();
  FlutterBootcamp(int aplicativos, String descricao, List<String> tags ){
    this.aplicativos = aplicativos;
    this.descricao = descricao;
    this.tags = tags;
  };
  FlutterBootcamp(this.aplicativos, this.descricao, this.tags);
  /*
    Todas as declarações acima são válidas como construtor default da classe. 
    Porém, só é possível utilizar 1 delas.
    Lembre-se: declarar o construtor default é opcional 
  */

  // funções
  void exibirConteudo(){

  }

}
```

No Flutter, outra funcionalidade muito utilizada da linguagem Dart são os `named constructors`:

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
```

Agora, pode-se criar uma  instância do objeto `Carro` da seguinte forma:

```dart
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

class ReactBootcamp extends Bootcamp {
  bool isNative = true;
  ReactBootcamp(super.linguagem, this.isNative);
  aprenderJavascript() {
    super.basico();
    super.linguagem = 'Javascript';
  }

  void conteudoReact(String extra) {
    super.conteudo();
    print(extra);
  }
}

```

## **Coleções**

```dart
// List (os itens podem ser duplicados)
var aplicativos = ['libria', 'menuo', 'civitas'];

// Por inferência, aplicativos é um List<String>
```

```dart
// Set (os itens são únicos)
var aplicativos = {'libria', 'menuo', 'civitas'};

// Por inferência, aplicativos é um Set<String>
```

```dart
// Map 
var aplicativos = {
  1 : 'libria', 
  2 : 'menuo', 
  3 : 'civitas'
 };

 // Por inferência, aplicativos é um Map<int, String>
```
## **```try / catch / finally```**

```dart
try {
  
} catch (e) {

} finally { // opcional
  
}
```

## **Future**

São objetos utilizados para tratar operações assíncronas (sem sincronia).

Alguns exemplos:

- Consumir uma API via rede; 
- Operações em banco de dados;
- Ler / gravar em um arquivo.

> Qualquer operação que não seja concluída **imediatamente** é uma operação *assíncrona*.

Future é um objeto que representa uma operação assíncrona. Assim que a operação for concluída, o valor está pronto para ser usado.

```dart
Future<int?> buscarApi() async {
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

Porém, ainda existem muitos recursos para serem explorados.

Para continuar os estudos e se aprofundar, acesse o guia:

[A tour of the Dart language](https://dart.dev/guides/language/language-tour)

E também os cursos do [Google Codelabs](https://dart.dev/codelabs).

Com [DartPad](https://dartpad.dev/?null_safety=true), é possível experimentar a linguagem diretamente no browser.

#### Bons estudos 📖


## **Referências**

[A tour of the Dart language](https://dart.dev/guides/language/language-tour)

[Language samples](https://dart.dev/samples)

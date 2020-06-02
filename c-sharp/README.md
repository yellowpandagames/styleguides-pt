## Índice

- [Nomenclatura](#nomenclatura)

    - [Namespaces](#Namespaces)

    - [Tipos](#Tipos)

    - [Métodos](#Métodos)

    - [Campos](#Campos)

    - [Propriedades](#Propriedades)

    - [Parâmetros](#Parâmetros)

    - [Teste Unitário (Unit Testing)](#TesteUnitário)

    - [Outros](#Outros)

- [Declarações](#declaracoes)

    - [Disposição](#declaracoes-disposicao)

    - [Tipos](#declaracoes-tipos)

    - [Modificadores de acesso](#declaracoes-modificadores-de-acesso)

    - [Tipos implícitos](#declaracoes-tipos-implicitos)

- [Espaçamento](#espacamento)

    - [Comprimento de Linha](#espacamento-comprimento-de-linha)

    - [Indentação](#espacamento-identacao)

    - [Espaçamento Vertical](#espacamento-vertical)

- [Estilo de Corpo { }](#estilo-de-corpo)

- [Instruções Switch](#switchs)

- [Ordem de Membros](#ordem)

- [Língua](#lingua)

- [Direitos Autorais](#direitos-autorais)

- [Referências e Inspirações](#referencias)

## Nomenclatura <a id="nomenclatura"></a>

Quando se trata de nomenclatura, em geral, devem ser seguidos as convenções da
linguagem C# porém algumas exceções se aplicam. Segue uma tabela a qual resume o
estilo das nomenclaturas utilizadas:

| **Nome do Objeto** | **Notações** | **Plural** | **Prefixo** | **Sufixo** | **Abreviação** |
| ------------------ | ------------ | :--------: | :---------: | :--------: | :------------: |
| Classes            | PascalCase   |     ✖️    |      ❌     |     ✔️     |      ❌       |
| Construtores       | PascalCase   |     ❌    |      ❌     |     ✔️     |      ❌       |
| Métodos            | PascalCase   |     ✔️    |      ❌     |     ✖️     |      ❌       |
| Parâmetros         | camelCase    |     ✔️    |      ❌     |     ❌     |      ✔️       |
| Variáveis Locais   | camelCase    |     ✔️    |      ❌     |     ❌     |      ✔️       |
| Constantes         | MACRO\_CASE  |     ❌    |      ❌     |     ❌     |      ❌       |
| Campos             | `-` \_camelCase<br>`#` camelCase<br>`+` PascalCase | ✔️ | ✖️ | ❌ | ❌ |
| Propriedades       | PascalCase   |     ✔️    |      ❌     |     ❌     |      ❌       |
| Delegados          | PascalCase   |     ❌    |      ❌     |     ✔️     |      ❌       |
| Enums              | PascalCase   |     ✖️    |      ❌     |     ❌     |      ❌       |

✔️ Pode ser utilizado

❌ Não deve ser utilizado

✖️ Não deve ser utilizado, porém existem exceções

`-` Membros privados

`#` Membros protegidos

`+` Membros públicos

### Namespaces <a id="nomeclatura-namespaces"></a>

Utilizar **PascalCase** , sendo a única exceção acrônimos, como UI ou HUD, os quais
podem ser em caixa alta.

EVITE:

```csharp
namespace yellowpanda.mazegame.hud.healthbar
```

PREFIRA:

```csharp
namespace YellowPanda.MazeGame.HUD.Healthbar
```

### Tipos <a id="nomeclatura-tipos"></a>

Todos os tipos são escritos em alguma variação de **PascalCase**.

#### Classes e Structs

Escritos em **PascalCase** utilizando substantivos ou frases nominais:

```csharp
class Player {}
class RadialSlider {}
class GameManager {}
```

#### Interfaces

Escritos em **PascalCase** com o prefixo **I** , utilizando principalmente adjetivos
e ocasionalmente frases nominais ou substantivos:

```csharp
interface IBreakable {}
interface ISearcher {}
interface IPrintable {}
```

💡 Ao nomear uma interface com substantivos ou frases nominais pode ser um indicativo
que esta poderia ser melhor representada por uma classe abstrata.

#### Eventos

   // Work In Progress

~~Escritos em **PascalCase**~~

#### Enumerações (enum)

Escritos em **PascalCase** com nomes no singular. Enums são somente nomeados no plural
quando seus valores são sinalizadores (Flags). **Não** utilize sufixos e prefixos
como &quot;Enum&quot; ou &quot;Flags&quot; ao nomear enumerações.

EVITE:

```csharp
enum SwitchStates {}

[System.Flags]
enum Layer {}
```

PREFIRA:

```csharp
enum SwitchState {}

[System.Flags]
enum Layers {}
```

#### Delegados

Escritos em **PascalCase** + sufixo de acordo com seus usos:

Em Eventos 🠊 Sufixo &quot;**EventHandler**&quot;

Outros casos 🠊 Sufixo &quot;**Callback**&quot;

EVITE:

```csharp
delegate void PlayerSpawned();
delegate void TaskCompleted();
delegate void TaskFailedDelegate();
```

PREFIRA:

```csharp
delegate void PlayerSpawnedEventHandler();
delegate void TaskCompletedCallback();
delegate void TaskFailedCallback();
```

#### Outros tipos comuns

| **Tipo da Base** | **Nomenclatura<br>da Derivação** | **Exemplo** |
| ---------------- | -------------------------------- | ---------------------- |
| System.Attribute | Sufixo &quot;**Attribute**&quot; | ReadOnlyAttribute      |
| System.EventArgs | Sufixo &quot;**EventArgs**&quot; | PlayerDiedEventArgs    |
| IDictionary<br>IDictionary\<TKey,TValue> | Sufixo &quot;**Dictionary**&quot; | ProvincesByCountryDictionary |
| IEnumerable<br>ICollection<br>IList<br>IEnumerable\<T><br>ICollection\<T><br>IList\<T> | Sufixo &quot;**Collection**&quot; | DinosaurNamesCollection |
| System.Exception | Sufixo &quot;**Exception**&quot; | DataCorruptedException |

### Métodos <a id="nomeclatura-metodos"></a>

Escritos em **PascalCase** utilizando frases verbais:

```csharp
void DoSomething() {}
void DamagePlayer() {}
```

### Campos <a id="nomeclatura-campos"></a>

Escritos diferentemente dependendo de seus modificadores de acesso:

private 🠊 **\_camelCase**

protected 🠊 **camelCase**

internal 🠊 **PascalCase**

public 🠊 **PascalCase**

private protected 🠊 **pascalCase**

protected internal 🠊 **PascalCase**

EXEMPLO:

```csharp
public class FooBar
{
    public int PublicField;
    internal int InternalField;
    protected int protectedField;
    private int _privateField;
}
```
EVITE:

```csharp
public int myPublicVariable;
private int myPrivateVariable;
```

PREFIRA:

```csharp
public int MyPublicVariable;
private int _myPrivateVariable;
```

#### Coleções

Campos de coleções são escritos no plural:

```csharp
int[] randomNumbers;
string[] fruitNames;
List<Player> players;
EnemyCollection enemies;
```

### Propriedades <a id="nomeclatura-propriedades"></a>

Todas as propriedades são escritas em **PascalCase** , independentemente do seu
modificador de acesso:

```csharp
public int TotalPageCount { get; }
private int PageIndex { get; set; }
```

### Parâmetros <a id="nomeclatura-parametros"></a>

Escritos em **camelCase** :

EVITE:

```csharp
void DisplayPopUp(Vector3 DisplayLocation, string DisplayText)
```

PREFIRA:

```csharp
void DisplayPopUp(Vector3 displayLocation, string displayText)
```

Nomes com 1 caractere são evitados a não ser que sejam utilizados em loops ou em 
contexto matemático, com suas devidas convenções, como a fórmula de bhaskara ou o 
construtor de algum vetor por exemplo:

```csharp
void Bhaskara(float a, float b, float c)
Vector2(float x, float y)
```

### Teste Unitário (Unit Testing) <a id="nomeclatura-testes"></a>

#### Classes

Escritas em **PascalCase** + sufixo **Tests** :

```csharp
class CarTests {}
class PlayerMovementTests {}
```

#### Métodos

Escritos em **PascalCase** + prefixo **Should\_** + infixo **\_When\_** (pode ser 
substituído por outras palavras como &quot;After&quot; ou &quot;Before&quot;):

**Should\_** ComportamentoEsperado **\_When\_** EstadoEmTeste

EXEMPLO:

```csharp
void Should_DisplayVictoryText_When_PlayerWinsGame();
void Should_LoseHealth_When_HitByPlayer();
void Should_DestroyProjectile_When_MaximumDistanceReached();
void Should_LeaveBuilding_Before_BuildingExplodes();
```

O nome de um teste deve ser baseado na _feature_ a ser testada. O prefixo **Should\_** 
é importante já que reforça a forma como os testes unitários devem ser escritos. 
Já o infixo **\_When\_** separa o comportamento, do estado em teste.

### Outros <a id="nomeclatura-outros"></a>

#### Abreviações

Para abreviações com 3 caracteres ou mais deve se utilizar **PascalCasing**
(para 2 caracteres podem ser escritos em caixa alta):

```csharp
HttpRequest httpRequest;
TextUI textUI;
int userID;
```

Evite utilizar abreviações (principalmente em membros públicos e internos), 
a não ser que estas sejam abreviações comumente utilizadas como nomes por exemplo:
gui, UI, ftp, xml, ID, max, min.

EVITE:

```csharp
Button openDoorBttn;
UserGroup usrGrp;
Assignment empAssignment;
```

PREFIRA:

```csharp
Button openDoorButton;
UserGroup userGroup;
Assignment employeeAssignment;
```

EXCEÇÃO:

```csharp
CustomerId customerID;
XmlDocument xmlDocument;
UrlHelper UrlHelper;
```

#### Claridade

Utilize o máximo de palavras possíveis até que o propósito de um membro esteja
claro (porém devem ser evitados pleonasmos ou redundâncias):

EVITE:

```csharp
// Propósito não claro
string[] fruits;
int svToken;
void ResetPos();

// Redundância
void FunctionToKillThePlayer(Player player);
```

PREFIRA:

```csharp
string[] fruitNames;
int serverAuthToken;
void ResetPosition();
void KillPlayer(Player player);
```

#### Números

Uma boa prática para nomear números é utilizar adjetivos como &quot;Maximum&quot; (max),
&quot;Minimum&quot; (min), &quot;Total&quot;. Trocar a palavra &quot;Number&quot; 
por &quot;Count&quot; também aumenta a claridade. Em algumas situações a palavra 
&quot;Limit&quot; pode ser melhor substituída pelas palavras
&quot;Maximum&quot; / &quot;Minimum&quot;:

EVITE:

```csharp
int numberOfPages;
int secretPages;
```

PREFIRA:

```csharp
int totalPageCount;
int secretPagesCount;
```

#### Ambiguidade

No exemplo a seguir &quot;secretPages&quot; pode ser interpretado pelo leitor
tanto como a quantidade de páginas secretas quanto uma coleção de páginas secretas.
Somente lendo seu nome, essa variável é facilmente interpretada como uma coleção
(pois segue a convenção de nomenclatura de coleções), porém ao saber que a variável 
é do tipo integral (int) fica claro que se trata de alguma quantidade:

EVITE:

```csharp
//Ambiguidade entre coleções e números
int players;
int specialPages;
```

PREFIRA:

```csharp
//Coleções
Player[] players;
Page[] specialPages;

//Números
int SpecialPagesCount;
int PlayerCount { get { return players.Length; } }
```

## Declarações <a id="declaracoes-disposicao"></a>

### Disposição

Prefira uma declaração por linha.

EVITE:

```csharp
string username, password;
```

PREFIRA:

```csharp
string username;
string password;
```

### Tipos <a id="declaracoes-tipos"></a>

Um tipo por arquivo (salvo o uso de tipos aninhados).

### Modificadores de acesso <a id="declaracoes-modificadores-de-acesso"></a>

Modificadores de acesso são explícitos para tipos, métodos e variáveis de membro.

EVITE:

```csharp
class Player
{
    int _playerHealth;
    int _playerDamage;

    void Start()
    {
        //...
    }
}
```

PREFIRA:

```csharp
internal class Player
{
    private int _playerHealth;
    private int _playerDamage;
    
    private void Start()
    {
        //...
    }
}
```

### Tipos implícitos <a id="declaracoes-tipos-implicitos"></a>

var

## Espaçamento <a id="espacamento"></a>

### Comprimento de Linha <a id="espacamento-comprimento-de-linha"></a>

O número máximo de caracteres por linha é de **85 caracteres**.

💡 Utilize ferramentas ou plugins do seu editor de texto de escolha para 
auxiliar na detecção de linhas longas, como réguas verticais ou quebras
de linha automáticas ([VSCode](https://stackoverflow.com/a/29972073/8140034),
[VS](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)).

### Indentação <a id="espacamento-identacao"></a>

A indentação é feita através de **espaços**.

💡 Configure o espaçamento de seu Tab no seu editor de escolha,
caso seja necessário ([VSCode](https://stackoverflow.com/a/29972553/8140034),
[VS](https://stackoverflow.com/a/14167067/8140034)).

#### Blocos

Indentação em blocos são de **4 espaços** :

```csharp
if (true)
{
    print("Hello World");
}
```

#### Alinhamento

Quando necessário, argumentos devem ser alinhados um por linha, sendo o primeiro
argumento na mesma linha da invocação ou declaração:

```csharp
SomeObjectReference.SomeMethodCall(defaultPlayerHealth,                             // limite
                                   defaultPlayerDamage,                             // de
                                   defaultPlayerMovementSpeed);                     // caracteres
                                                                                    // (85)
float[,] GenerateNoiseMap(int mapWidth,                                             //
                          int mapHeight,                                            //
                          float scale,                                              //
                          int octaves,                                              //
                          float lacunarity);                                        //
```

#### Quebras de Linha

Indentação em quebras de linha são de **4 espaços** :

```csharp
CoolUiWidget widget =                                                               //
    someIncrediblyLongExpression(ThatReallyWouldNotFitOnASingleLine);               //
```

✔️ Alinhe argumentos de invocações ou declarações com **2 ou mais argumentos** 
que ultrapassem o [limite de caracteres](#_es9k0sy4vg8h) (85).

```csharp
// 97 caracteres                                                                    //
Player player = new Player(defaultPlayerHealth,                                     //
                           defaultPlayerDamage,                                     //
                           defaultPlayerMovementSpeed);                             //
                                                                                    //
// 62 caracteres                                                                    //
Vector4 fourNumbersVector = new Vector4(100, 200, 300, 400);                        //
```

✔️ Utilize uma quebra de linha **antes** de uma invocação cujo primeiro 
argumento ultrapasse o limite de caracteres por linha.

```csharp
// 90 caracteres                                                                    //
Robot shinyNewClonedRobot =                                                         //
    CloneRobot(robotToClone, aVeryLongVariableNameJustForExample);                  //
```

✔️ Utilize uma quebra de linha **depois** de [operadores](https://docs.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/)
de atribuição (=), atribuição composta (+=, -=, \*= ...), ou declaradores
de expressões lambda (=\&gt;) cujas expressões a sua direita ultrapassem
o limite de caracteres:

```csharp
// 104 caracteres                                                                   //
Enemy closestEnemy =                                                                //
    allEnemies.OrderBy(t => (t.position - referencePos).sqrMagnitude)               //
              .FirstOrDefault();                                                    //
```

✔️ Utilize uma quebra de linha **antes** de quaisquer outros [operadores](https://docs.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/)
cujas expressões a sua direita ultrapassem o limite de caracteres:

```csharp
// 103 caracteres                                                                   //
int randomAritmetic = (GetSomeValueFromObject(obj) * GetSomeOtherValue())           //
    * UnityEngine.Random.Range();                                                   //
```

✔️ Utilize variáveis locais para manter fácil a leitura de expressões longas.

❌ EVITE quebras de linha consecutivas com diversos alinhamentos:

```csharp
if (JumpPressed 
    && ((GodModeOn && SomeOtherLongCondition)
        || (PlayerIsGrounded && JumpCooldownIsOver))
{
    Jump();
}
```

PREFIRA:

```csharp
bool canJump = (GodModeOn && SomeOtherLongCondition)
               || (PlayerIsGrounded && JumpCooldownIsOver);
if (JumpPressed && canJump)
{
    Jump();
}
```

### Espaçamento Vertical <a id="espacamento-vertical"></a>

✔️ Utilize somente **uma** linha em branco separando métodos.

✔️ Utilize linhas em branco dentro de métodos para separar funcionalidade e contexto.

💡 Um método com muitas seções talvez signifique que este deva ser refatorado em
múltiplos métodos.

## Estilo de Corpo { } <a id="estilo-de-corpo"></a>

Cada chave possui sua própria linha, uma convenção da língua C#:

EVITE:

```csharp
class MyClass {
    void DoSomething() {
        if (someTest) {
            // ...
        } else {
            // ...
        }
    }
}
```

PREFIRA:

```csharp
class MyClass
{
    void DoSomething()
    {
        if (someTest)
        {
            // ...
        }
        else
        {
            // ...
        }
    }
}
```

Instruções condicionais (if-else) devem sempre possuir corpo, não importando o número
de linhas.

EVITE:

```csharp
if (someTest)
    doSomething();

if (someTest) doSomethingElse();
```

PREFIRA:

```csharp
if (someTest)
{
    DoSomething();
}
```

## Instruções Switch <a id="switchs"></a>

Switch()

## Ordem de Membros <a id="ordem"></a>

Dentro de uma classe, estrutura ou interface:

1. Constantes
2. Campos serializados no inspector da UnityEngine
3. Campos
4. Construtores
5. Finalizadores
6. Delegados
7. Eventos
8. Enumerações
9. Interfaces (implementações)
10. Propriedades
11. Indexadores
12. Métodos mensagens da UnityEngine
13. Métodos callbacks de eventos
14. Métodos
15. Estruturas (structs)
16. Classes

Para cada um desses grupos ordene por acesso:

1. public
2. internal
3. protected internal
4. protected
5. private

Para cada um desses grupos ordene por estáticos e não-estáticos:

1. static
2. non-static

Para cada um desses grupos estáticos e não estáticos ordene por somente leitura e
leitura/escrita:

1. readonly
2. non-readonly

A ordem completa para métodos é a seguinte:

1. public static
2. public
3. internal static
4. internal
5. protected internal static
6. protected internal
7. protected static
8. protected
9. private static
10. private
1. aaaaa

## Língua <a id="lingua"></a>

Utilize **inglês** (en-US/en-UK) para escrever código. Comentários podem ser escritos
tanto em **inglês** (en-US/en-UK) quanto em **português** (pt-BR).

## Direitos Autorais <a id="direitos-autorais"></a>

Coloque o seguinte trecho no início de cada arquivo escrito pela Yellow Panda Games:

```csharp
/// <copyright>
/// Não copie, somente um exemplo.
/// </copyright>
```

## Referências e Inspirações <a id="referencias"></a>

Este guia foi baseado em convenções de C#, Unity e também em diversos outros guias de estilos:

- [Raywenderlich Style Guide](https://github.com/raywenderlich/c-sharp-style-guide/blob/master/README.markdown)
- [DoFactory - C# Coding Standards and Naming Conventions](https://www.dofactory.com/reference/csharp-coding-standards)
- [.NET Framework Design Guidelines](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines)
- [Ktaranov&#39;s naming convention templates](https://github.com/ktaranov/naming-convention)
- [7 Popular Unit Test Naming Conventions](https://dzone.com/articles/7-popular-unit-test-naming)
- [StyleCop - Ordering Rules](https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/documentation/SA1201.md)
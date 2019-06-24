# manual-bigdata

### 스파크 역사
```
UC버클리의 RAD 연구실의 연구프로젝트로 2009년 시작
2010년 3월 오픈소스화
2013년 6월 아파치 
```

### 스파크 관련사이트
```
스파크의 사용자 목록페이지
https://cwiki.apache.org/confluence/display/SPARK/Powered+By+Spark#app-switcher

스파크 밋업
http://www.meetup.com/spark-users

스파크 서미트
http://spark-summit.org

스파크 튜토리얼
http://spark.apache.org/docs/latest/quick-start.html
```

### 윈도우 스파크 실습환경
```
실습환경
1. OS
    Window 10
2. Other
    java 1.8.0_201
    spark-2.4.6
    hadoop 2.6

환경변수
    SPARK_HOME (C:\\spark-2.4\\bin)
    SCALA_HOME (C:\\scala\\bin)
    JAVA_HOME  (C:\\Progra~1\\java\\jdk1.8.0_144)
    HADOOP_HOME (C:\\hadoop)
    JAVA_OPTIONS (-Xmx512M -Xmx512M)

실습과정 (WordCountScalaHDFSScript.scala는 c:\spark-2.4\bin에 집어넣는다)
    Window PowerShell 실행 (C:\\spark-2.4\\bin 경로 이동)
    .\\spark-shell -i WordCountScalaHDFSScript.scala 2>&1 | Tee-Object -file c:\\output_조길상_201103277.txt
    txt파일 UTF-8 형식 변환
    tree /F >> c:\\output_조길상_201103277.txt
```

### 윈도우 스파크 설정
```
C:\spark-2.4\conf\log4j.properties.template
log4j.rootCategory=WARN, console
```


### 윈도우 스파크, 스칼라, 자바 세팅 window spark, scala,java 설치
```
1. java 설치
   1.8 이상 버전 JDK 설치 (왜냐하면 람다식을 지원해야된다. 그래서 무조건 1.8이상)
   (https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

2. Scala 설치
   c:\scala 로 경로설정해서 설치하기 (중간에 경로 띄어쓰기 있으면 에러남)
   (https://www.scala-lang.org/download/)

3. Spark 설치
   3.1. hadoop 2.6에 맞춰서 download
   (http://spark.apache.org/downloads.html)
   3.2. c:\spark-2.4 (중간에 경로 띄어쓰기 있으면 에러남)

4. Hadoop (하둡을 사용안하기때문에, 이 작업이 필요함)
   4.1. 해당 사이트를 방문 (https://github.com/steveloughran/winutils)
   4.2. 원하는폴더(예 : 다운로드)에 가서 git clone https://github.com/steveloughran/winutils.git
        *** git 설치가 안되있으면 수동으로 사이트에서 압축파일 다운 후 해제 ***
   4.3. 다운받거나 압축해제 후 winutils\hadoop-2.6.4\bin 폴더에 있는 winutils.exe 복사하기
   4.4. C:\hadoop\bin 폴더만들고, 위에 복사한 winutils.exe 붙여넣기 

5. 환경변수 설정 (시스템 변수 클릭 후 추가)
   SPARK_HOME C:\spark-2.4\bin
   SCALA_HOME C:\scala\bin
   JAVA_HOME  C:\Progra~1\java\jdk1.8.0_144 (스파크는 중간에 띄어쓰기경로 있으면 에러남, 본인 버전에 맞게)
   HADOOP_HOME C:\hadoop
   JAVA_OPTIONS -Xmx512M -Xmx512M

6. spark-shell 
   6.1 cmd(명령프롬프트)창을 연다
   6.2 c:\로 이동한뒤, spark-2.4\bin\spark-shell 기입후 Enter
       (또는 c:\spark-2.4\bin\로 이동한뒤, spark-shell 기입후 Enter)

   (에러 발생시 100% 경로문제)
   4.5으로 돌아가서 SPARK_HOME, SCALA_HOME 경로에 bin을 제거 혹은 추가(C:\scala, C:\spark-2.4 변경)
   기존 자바 사용자는 시스템 변수가 아닌 사용자 변수에 등록된 path 경로 확인후 bin 추가 혹은 제거
   (예 : C:\Progra~1\java\jdk1.8.0_144, C:\Progra~1\java\jdk1.8.0_144\bin)       

출처 : https://jjangjjong.tistory.com/24      
```

### 윈도우 스칼라 WordCount 과제
1. 코드  
```
val text = sc.textFile("C:\\input\\2006.csv")
val counts = text.flatMap(line => line.split(",")).map(word => (word, 1)).reduceByKey(_+_)
counts.saveAsTextFile("C:\\output")
System.out.println("Spark WordCount Completes!!")
```
2. 커맨드  
C:\spark-2.4\bin에 WordCountScalaHDFSScript.scala 집어넣기(Path되있기때문)  
```
    Window PowerShell 실행 (C:\\spark-2.4\\bin 경로 이동)
    .\\spark-shell -i WordCountScalaHDFSScript.scala 2>&1 | Tee-Object -file c:\\output_조길상_201103277.txt
    txt파일 UTF-8 형식 변환
    tree /F >> c:\\output_조길상_201103277.txt
```

### 스칼라 Hello World!
```
object HelloWorld {
    def main(args: Array[String]) {
        println("Hello, world!")
    }
}

HelloWorld.main(null)
```

### 스칼라 예제
```
https://www.programcreek.com/scala/org.apache.spark.sql.expressions.Window
```
### 스칼라 튜토리얼 사이즈
```
url :
https://www.scala-exercises.org/scala_tutorial
```

### 스칼라 튜토리얼 1 : terms_and_types
```
contents :

scala> 1
res0: Int = 1

scala> true
res1: Boolean = true

scala> "hello, scala"
res2: String = hello, scala

scala> 1+2
res3: Int = 3

scala> "Hello, " + "Scala!"
res4: String = Hello, Scala!

scala> "Hello, " ++ "Scala!"
res5: String = Hello, Scala!

scala> (1+2)+3
res6: Int = 6

scala> (3*3)
res7: Int = 9

scala> "hello, scala".size
res8: Int = 12

scala> "hello, scala".toUpperCase
res15: String = HELLO, SCALA

scala> "hello, scala".toLowerCase
res16: String = hello, scala

scala> 3 + 2 == 3.+(2)
res17: Boolean = true

scala> 16.toHexString
res20: String = 10

scala> 4.toHexString
res21: String = 4

scala> (0 to 10).contains
contains   containsSlice

scala> (0 to 10).contains(10)
res23: Boolean = true

scala> (0 until 10).contains(10)
res24: Boolean = false

scala> 0 until 10
res26: scala.collection.immutable.Range = Range(0, 1, 2, 3, 4, 5, 6, 7, 8, 9)

scala> 0 to 10
res27: scala.collection.immutable.Range.Inclusive = Range(0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

scala> "abc".drop(1)
res31: String = bc

scala> "abc".drop(2)
res32: String = c

scala> "abc".drop(3)
res33: String = ""

scala> "abc".drop(4)
res34: String = ""

scala> "abc".take(1)
res35: String = a

scala> "abc".take(2)
res36: String = ab

scala> "abc".take(3)
res37: String = abc

scala> "abc".take(4)
res38: String = abc

```

### 스칼라 튜토리얼 2 : DEFINITIONS AND EVALUATION
```
scala> val radius = 10
radius: Int = 10

scala> var pi = 3.14159
pi: Double = 3.14159

scala> def square(x: Double) = x * x
square: (x: Double)Double

scala> def area(radius: Double): Double = 3.14159 * square(radius)
area: (radius: Double)Double

scala> def power(x: Double, y: Int) : Double = x + y
power: (x: Double, y: Int)Double

scala> loop
java.lang.StackOverflowError
at loop(<console>:23)
```

### 스칼라 튜토리얼 3 : Functional Loops
```
scala> def abs(x: Double):Double = if (x>=0) x else -x
abs: (x: Double)Double

scala> abs(5)
res24: Double = 5.0

scala> abs(0)
res25: Double = 0.0

scala> abs(-3)
res26: Double = 3.0
```

### 스칼라 튜토리얼 4 : Lexical Scopes
```
scala> object Foo {
     |   val x = 1
     | }
defined object Foo

scala> object Bar {
     |   val x = 2
     | }
defined object Bar

scala> object Baz {
     |   import Bar.x
     |   val y = x + Foo.x
     | }
defined object Baz

scala> Baz.y
res33: Int = 3

scala> Bar.x
res34: Int = 2

scala> Foo.x
res35: Int = 1

scala> {
     | val x = f(3)
     | x*x
     | }

```

### 스칼라 튜토리얼 5 : Tail Recursion
```
scala> def factorial(n:Int): Int =
     | if(n==0) 1 else n*factorial(n-1)
factorial: (n: Int)Int

scala> factorial(4)
res38: Int = 24

@tailrec ???
```

### 스칼라 튜토리얼 6 : Structuring Information
```

case class Note(
  name: String,
  duration: String,
  octave: Int
)

val c3 = Note("C", "Quarter", 3)

sealed trait Symbol
case class Note(name: String, duration: String, octave: Int) extends Symbol
case class Rest(duration: String) extends Symbol

--------------------------------------------------------------------------------

scala> sealed trait Duration
defined trait Duration

scala> case object Whole extends Duration
defined object Whole

scala> case object Half extends Duration
defined object Half

scala> case object Quarter extends Duration
defined object Quarter

scala> def fractionOfWhole(duration: Duration): Double =
     |   duration match {
     | case Whole => 1.0
     | case Half => 2.0
     | case Quarter => 3.0
     | }
fractionOfWhole: (duration: Duration)Double

scala> fractionOfWhole(Whole)
res44: Double = 1.0

```

### 스칼라 튜토리얼 7 :Higher Order Functions
```
def sumInts(a: Int, b: Int): Int =
  if (a > b) 0 else a + sumInts(a + 1, b)

def cube(x: Int): Int = x * x * x

def sumCubes(a: Int, b: Int): Int =
  if (a > b) 0 else cube(a) + sumCubes(a + 1, b)

def sumFactorials(a: Int, b: Int): Int =
  if (a > b) 0 else factorial(a) + sumFactorials(a + 1, b)

-------------------------------------------------------

def id(x: Int): Int = x
def sumInts(a: Int, b: Int) = sum(id, a, b)
def sumCubes(a: Int, b: Int) = sum(cube, a, b)
def sumFactorials(a: Int, b: Int) = sum(factorial, a, b)
--------------------------------------------------------

def sumInts(a: Int, b: Int) = sum(x => x, a, b)
def sumCubes(a: Int, b: Int) = sum(x => x * x * x, a, b)
```

### 스칼라 튜토리얼 8 : Standard Library
```
val fruit = List("apples", "oranges", "pears")
val nums = List(1, 2, 3, 4)
val empty = List()

val nums = 1 :: 2 :: 3 :: 4 :: Nil
val nums = Nil.::(4).::(3).::(2).::(1)

val nums = List(1)
val nums = List()

nums match {
  // 리스트가 1이나 2로 시작한다
  case 1 :: 2 :: xs =>
  println("리스트가 1이나 2로 시작한다")

  // 리스트의 길이(Lenth)가 1이다.
  case x :: Nil =>
  println("리스트의 길이(Lenth)가 1이다.")

  // 리스트의 길이(Lenth)가 1이다.
  case List(x) =>
  println("리스트의 길이(Lenth)가 1이다.") 

  // 리스트가 비어있다. Nil
  case List() =>
  println("리스트가 비어있다. Nil") 

}

// 리스트를 받아서 match 시키는 함수의 예
def insertionSort(xs: List[Int]): List[Int] = xs match {
  case List() => List()
  case y :: ys => insert(y, insertionSort(ys))
}

// 리스트에 있는 값들 하나씩 증가시키는 경우
List(1, 2, 3).map(x => x + 1) == List(2, 3, 4)
res7: Boolean = true

// 리스트에서 2의 배수만 필터링하기
List(1, 2, 3).filter(x => x % 2 == 0) == List(2)
res8: Boolean = true

// 리스트의 요소별로 새로운 리스트를 만들기???
val xs =
  List(1, 2, 3).flatMap { x =>
    List(x, x+1, x+2)
  }
xs == List(1, 2, 3, 3, 4, 5, 4, 5, 6)


// option을 줘서 할수있는거같은데, 잘모르겠다. 다른 예시가 필요할듯
def sqrt(x: Double): Option[Double] =
  if (x < 0) None else Some(…)

// Success와 fail에 대해서
def sqrt(x: Double): Try[Double] =
  if (x < 0) Failure(new IllegalArgumentException("x must be positive"))
  else Success(…)
  
  // Either ? left ? Right? 모르겠다
  
```

### 스칼라 튜토리얼 9 : Syntactic Conveniences
```
// 숫자랑 문자열을 넣어서 Tuple 형식으로 받기
def getTuple(i:Int, s:String): (Int,String) = (i,s)

scala> getTuple(930126,"gilsang")
res17: (Int, String) = (930126,GILSANG)

// 튜플 하나 만들기
val is: (Int, String) = (930126, "gilsang")

scala> is._1
res22: Int = 930126

scala> is._2
res23: String = gilsang

is match {
  case (i, s) =>
    (i,s)
}

is match {
  case (i, s) =>
    i
}
```

### 스칼라 튜토리얼 10 : Object Oriented Programming
```

abstract class profile {
 // OVERRIDING
  def nationality : String = "kr"
  
  // IMPLEMENTATION
  def name : String
  def birth : Int
  def age : Int
  
  def getName(): String
  def getBirth() : Int 
  def getAge() : Int
}

class User(x: String, y: Int, z:Int, gender:String) extends profile{

   // REQUIRE (Check Parameter and Alarm Error)
   require(y > 0, "birth must be positive") // java.lang.IllegalArgumentException
   require(z > 0, "age must be positive")   // java.lang.IllegalArgumentException

   // OVERRIDING
  override def nationality : String = "en" 
  override def toString = this.name + "/" + this.birth + "/" + this.age + "/" + this.sex
  
  // IMPLEMENTATION
  def name : String = x // abstract class 를 구현하는경우, private 사용불가
  def birth : Int = y // abstract class 를 구현하는경우, private 사용불가
  def age : Int= z // abstract class 를 구현하는경우, private 사용불가
  
  def getName(): String = this.name
  def getBirth() : Int = this.birth
  def getAge() : Int = this.age
  
  // NONE
  private def sex : String = gender
  
}

val user = new User("jogilsang", 930126,27,"man")


// implement는 trait로 만들어서 with로 쓰나보네
// overide는 위에처럼 사용하고...
trait Planar {
  def height: Int
  def width: Int
  def surface = height * width
}

class Square extends Shape with Planar with Movable …
```

### 스칼라 튜토리얼 11 : Imperative Programming
```

class BankAccount {
  private var balance = 0
  def deposit(amount: Int): Int = {
    if (amount > 0) balance = balance + amount
    balance
  }
  def withdraw(amount: Int): Int =
    if (0 < amount && amount <= balance) {
      balance = balance - amount
      balance
    } else throw new Error("insufficient funds")
}

scala> val account = new BankAccount
account: BankAccount = BankAccount@7cf166db

scala> account.deposit(50)
res0: Int = 50

scala> account deposit 50
res1: Int = 100

scala> account withdraw 20
res2: Int = 80

scala> account withdraw 20
res3: Int = 60

scala> val x = new BankAccount
x: BankAccount = BankAccount@302692b1

scala> val c = x
c: BankAccount = BankAccount@302692b1


scala> for (i <- 1 until 3) { System.out.print(i + " ") }
1 2
scala> for (i <- 1 until 3; j <- "abc") println(s"$i $j")
1 a
1 b
1 c
2 a
2 b
2 c
```
### 스칼라 튜토리얼 12 : Classes Vs Case Classes
```


val c3 = Note("C", "Quarter", 3)
scala> val cThree = Note("C", "Quarter", 3)

scala> c3 == cThree
res12: Boolean = true

scala> val aliceAccount = new BankAccount
aliceAccount: BankAccount = BankAccount@7ccf6785

scala> val bobAccount = new BankAccount
bobAccount: BankAccount = BankAccount@4430d9be

scala> aliceAccount == bobAccount
res13: Boolean = false

c3 match {
  case Note(name, duration, octave) => s"The duration of c3 is $duration"
}

scala> c3 match {
     |   case Note(name, duration, octave) => s"The duration of c3 is $duration"
     | }
res15: String = The duration of c3 is Quarter

```


### 스칼라 스터디(한글)
```
https://twitter.github.io/scala_school/ko/index.html
```




### 스칼라 에러
Spark context available as 'sc' (master = local[*], app id = local-1560057371716).  
Spark session available as 'spark'.
```
spark.stop() 
sc.stop()
```

### 페이지 랭크 알고리즘
```
레리 페이지가 만든것으로, 많은 조인을 수행하는 반복 알고리즘
RDD 파티셔닝의 좋은 예로 두 종류의 데이터세트를 관리한다
하나는 pageId, linklist의 형태로 각 페이지와 그 이웃 페이지들을 가지고있으며
pageID, rank 형태로 각 페이지의 현재 랭크를 관리한다

1. 각 페이지의 랭크를 1.0으로 초기화한다
2. 매번 반복주기마다 페이지 p는 공헌치 "랭크(p)/이웃숫자(p)를 이웃들(자신을 링크하고있는
페이지)에게 보낸다
3. 각 페이지의 랭크를 0.15+0.85*(받은공헌치)로 갱신한다.
```

### Learning Spark O'REILLY
```
스파크란? 클러스터용 연산플랫폼이다
맵리듀스 모델을 대화형 명령어 쿼리와 스트리밍 처리 등이 가능하도록 확장한것이다
연산은 메모리에서 수행하기떄문에, 속도가 빠르다
하둡 클러스터 위에서도 실행가능하며, 
카산드라를 포함한 어떤 하둡데이터 소스에도 접근이가능하다.

스파크는 여러개의 컴포넌트로 구성되어있다
스파크SQL, 스파크 스트리밍(실시간), MLib(머신러닝), 그래프x(그래프처리)
단독 스케줄러, 얀, 메소스

RDD(탄력적인 분산 데이터 세트)

스파크로 할 수 있는것?
데이터 과학
SQL, 통계, 예측 모델링(머신 러닝), 파이썬, 매틀랩, R프로그래밍

데이터 어플리케이션 ???

로컬모드는 즉 비분산모드
메소스,얀,스파크 배포판에 포함된 단독스케줄러 등에서 동작이가능함

---------------------------

병렬연산을 수행하는 드라이버 프로그램 // spark shell
SparkContext : 연산 클러스터에 대한 연결

--------------------------
스파크와 연동하는 방법은 스칼라의 경우 메이븐 의존성 필드에 spark-core 아티팩트를 써준다

---------------------------------
val lines = sc.textFile("C:\\spark-2.4\\README.md")
lines.count()
lines.first()

val lines = sc.textFile("C:\\spark-2.4\\README.md")
val counts = lines.filter(line => line.contains("Spark"))
counts.count()
counts.first()

val inputRDD = sc.textFile("C:\\spark-2.4\\README.md")
val countsSparkRDD = lines.filter(line => line.contains("Spark"))
val countsApacheRDD = lines.filter(line => line.contains("Apache"))
val unionRDD = countsSparkRDD.union(countsApacheRDD)
scala> unionRDD.count
res70: Long = 22
scala> countsSparkRDD.count
res71: Long = 20
scala> countsApacheRDD.count
res72: Long = 2


println("Here are 10 examples: ")
countsSparkRDD.take(10).foreach(println)

scala> countsSparkRDD.take(3).foreach(println)
# Apache Spark
Spark is a fast and general cluster computing system for Big Data. It provides
rich set of higher-level tools including Spark SQL for SQL and DataFrames,



val input = sc.textFile("C:\\spark-2.4\\README.md")
// 단어별로 나눈다
 val words = input.flatMap(line => line.split(" "))
// 단어, 숫자 쌍으로 변환하고 개수를 센다
val counts = words.map(word => (word,1)).reduceByKey{case (x,y) => x+y}
// 단어 개수르 다시 텍스트 파일로 저장한다
counts.saveAsTextFile("C:\\output")



-----------------------------------------------

RDD(탄력적인 분산 데이터 세트)
: 변경 불가능한 객체모음, 여러개의 파티션으로 나눠질수있음
RDD는 두가지 연산타입을 제공해주는대
트랜스포메이션과 액션이다
트랜스포메이션은 기존 RDD로부터 새로운 RDD를 생성해낸다. 예를들어 Python단어를 포함한 문자열만을 갖는 RDD 만드는 필터
액션은 RDD를 기초로 결과 값을 계산하여, 그 값을 되돌려주거나 저장
예를들어 first()함수로 첫번쨰줄이 shell에 표현됨

lazy evaluation(여유로운 방식)

RDD의 동작방식?
RDD를 만들게되고, 트랜스포메이션 등으로 새로운 RDD를 정의한다
RDD를 재사용한다면 persist()를 요청한다
연산수행을 위해 action을 시작한다.

-----------------------------------------------------------------------------------
키/값 페어로 작업
ETL : 기업용 시스템 간에 대량 데이터를 추출해 다른 시스템에 적재하는 작업
키/값 쌍을 가지고 있는 RDD에 대해 특수한 연산 제공
페어 RDD

첫번째 단어를 키로 사용한 페어 RDD 생성
val pairs = input.map(x => (x.split(" ")(0), x))

페어RDD의 트랜스포메이션의 다양한 예시 reduceByKey(func)

// 워드카운트
val input = sc.textFile("C:\\spark-2.4\\README.md")
val words = input.flatMap(x => x.split(" "))
val result = words.map(x => (x,1)).reduceByKey((x,y) => x+y)

// 키별로 평균구하기
val result2 = result.mapValues(x => (x,1)).reduceByKey((x,y) => (x._1 + y._1, x._2 + y._2))

// 스칼라 병렬화 직접 지정을 사용한 reduceByKey
val data = Seq(("a",3), ("b",4), ("a",1))
sc.parallelize(data).reducyByKey((x,y) => x+y)
sc.parallelize(data).reducyByKey((x,y) => x+y, 10) // 병렬화 수준 지정

storeAddress = {
  (Store("Ritual"), "1026 Valencia St")
}
```

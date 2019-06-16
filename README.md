# manual-bigdata
-환경변수 백업이 가능한가?

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


### 윈도우 스파크, 스칼라, 자바 세팅 window spark, scala,java 설치
```
1. java 
   1.8 설치 및 환경변수 설정 (람다지원해야됨. 무조건 1.8이상)
2. Scala 설치
   c:\scala 로 경로설정해서 설치하기 (중간에 경로 띄어쓰기 있으면 에러남)
   (https://www.scala-lang.org/download/)
3. Spark
   1. hadoop 2.6에 맞춰서 download
   (http://spark.apache.org/downloads.html)
   2. c:\spark-2.4 (중간에 경로 띄어쓰기 있으면 에러남)
4. winUtils
   1. visit (https://github.com/steveloughran/winutils)
   2. git clone https://github.com/steveloughran/winutils.git
   3. C:\Users\user\Downloads\winutils\hadoop-2.6.4\bin\winutils.exe 복사하기
   4. C:\hadoop\bin 폴더만들고, 위에 복사한거 붙여넣기
   5. 환경변수 클릭 - 시스템 변수 추가하기
      SPARK_HOME C:\spark-2.4\bin
      SCALA_HOME C:\scala\bin
      JAVA_HOME  C:\Progra~1\java\jdk1.8.0_144 (중간에 경로 띄어쓰기 있으면 에러남)
      HADOOP_HOME C:\hadoop
      JAVA_OPTIONS -Xmx512M -Xmx512M
      (에러 발생시)
      SPARK_HOME, SCALA_HOME 경로에 bin을 제거
      Path에 등록된 java 경로도 위의 JAVA_HOME과 유사하게한뒤 bin 추가하기
      
5. spark-shell 
   cmd열고 c:\로 이동한뒤, spark-2.4\bin\spark-shell        
// 출처 : https://jjangjjong.tistory.com/24      
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

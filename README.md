# manual-bigdata
-환경변수 백업이 가능한가?



### 윈도우 스칼라 window scala 설치
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
### 스칼라 튜토리얼
```
https://www.scala-exercises.org/scala_tutorial/terms_and_types
```

### 스칼라 스터디(한글)
```
https://twitter.github.io/scala_school/ko/index.html
```


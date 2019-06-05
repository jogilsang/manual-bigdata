# manual-bigdata
for me


### 윈도우 스칼라 window scala
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
      
   
   
   
```

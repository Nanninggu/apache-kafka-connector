# 파일위치
C:\Work

![image](https://user-images.githubusercontent.com/54211801/231951688-be03297c-937e-4b8f-9af7-c1fd85997b04.png)

### Kafka 설치
Kafka Connect 설치: Windows 10에서도 curl, tar 명령어 사용 가능

[버전은 골라서 다운로드 후 진행]

curl -O http://packages.confluent.io/archive/5.5/confluent-community-5.5.2-2.12.tar.gz

curl -O http://packages.confluent.io/archive/6.1/confluent-community-6.1.0.tar.gz

tar xvf confluent-community-6.1.0.tar.gz

cd  $KAFKA_CONNECT_HOME

### Kafka Connect 실행
.\bin\windows\connect-distributed.bat .\etc\kafka\connect-distributed.properties

### 수정
.\bin\windows\kafka-run-class.bat 파일에서 
rem Classpath addition for core 부분을 찾아서, 그 위에 아래 코드 삽입

![image](https://user-images.githubusercontent.com/54211801/231952347-33b4a5ef-b9bb-4ac5-90af-432b250bc237.png)

### 수정1
.\etc\kafka\connect-distributed.properties 파일 마지막에 아래 plugin 정보 추가

![image](https://user-images.githubusercontent.com/54211801/231952394-19c629e8-e2b5-4005-aa4d-d7f07b237e55.png)

### 수정2
JdbcSourceConnector에서 MariaDB 사용하기 위해 mariadb 드라이버 복사
${USER.HOME}\.m2 폴더에서 mariadb-java-client-2.7.2.jar 파일을 confluent 폴더아래의 ./share/java/kafka/로 복사

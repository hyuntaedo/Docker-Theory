Docker Theory
======================

## 목차

### 작업중


# 1. Docker
## 1.1. Container

[**VM vs Docker**](참고 : https://woochan-autobiography.tistory.com/463?category=452688)
1. Docker는 Container를 만들며, Linux에서 논리적으로 나눌 수 있는 Virtual Interface를 지원
2. Linux Control Group을 사용하여 가상화 환경을 제공
3. Windows에서 사용을 할 때는 Windows Hyper-V를 사용하여 Docker를 사용 --> Docker 환경은 Windows 환경보다는 Linux 환경이 좋다.

## 1.2. 모놀리식, 마이크로서비스
### 1.2.1. 모놀리식 Architecture

  1. 소프트웨어 프로그램의 전통적인 모델
  2. 다른 애플리케이션과 독립적인 통합된 유닛으로 만들어짐
  3. 모놀리식 Architecture는 모든 비지니스 관련 사항을 함께 결합하는 하나의 코드베이스를 갖춘 대규모의 단일 컴퓨팅 네트워크
  4. 서비스측 인터페이스 업데이트된 버전을 구축 및 배포하여 전체 스택을 업데이트 해야하나 이로인해 업데이트에 제한이 많고 시간이 오래걸림

#### 1.2.1.1. 모놀리식 아키텍쳐의 장점 

  1. 손쉬운 배포 : 실행 파일 또는 디렉토리가 하나여서 배포가 쉽다.
  2. 개발 : 하나의 코드베이스로 애플리케이션을 구축하여 개발하기 쉽다
  3. 성능 : 중앙집중식 코드베이스 및 Repo에는 대부분 하나의 API만으로 마이크로 서비스에서 여러 API가 수행하는 것과 동일한 기능을 수행 가능
  4. 테스트 간소화 : 하나의 중앙집중식 장치이므로 분산된 애플리케이션보다 End to End Test를 더 빠르게 수행 가능
  5. 간편한 디버깅 : 모든 코드가 한곳에 있으므로 문제 처리가 쉬움
  
#### 1.2.1.1. 모놀리식 아키텍쳐의 단점 

  1. 느린 개발속도 : 대규모 애플리케이션에서는 개발이 복잡해지고 속도가 느려짐
  2. 확장성 : 개별 컴포넌트 확장 불가능
  3. 기술 채택의 장벽 : 프레임워크 또는 언어를 변경하면 모든 애플리케이션에 전체적인 영향을 미치므로 비용과 시간이 많이 소요
  4. 유연성 부족 : 모놀리스의 경우 모놀리스에서 채택한 기술에서 다른 기술로 변경 불가능
  5. 배포 : 약간만 변경하더라도 전체를 다시 배포해야함
  
### 1.2.2. 마이크로서비스  

  1. 독립적으로 배포가  가능한 일련의 서비스를 이용하는 Architecture 방법
  2. 특정한 목표를 가진 비지니스 로직 및 데이터베이스가 존재
  3. 업데이트, 테스트, 배포 및 확장은 각 서비스 내에서 이루어짐
  4. 복잡성을 줄여주진 않으나, 작업이 서로 독립적으로 작동하고 전체에 기여하는 더 작은 프로세스로 분리하여 복잡성을 눈으로 보기 쉽게 만들어짐
  5. DevOps 채택과 같이 이루어지는 경우가 많음★★★★★★★★★★★

#### 1.2.2.1 마이크로서비스 아키텍쳐의 장점
  1. 성장하는 소프트웨어 회사의 여러 문제를 해결
  2. 독립적으로 실행하는 유닛으로 구성되므로, 다른 서비스에 영향을 주는 일 없이 각 서비스를 개발, 업데이트, 배포 및 확장이 가능
  3. 향상된 안정성, 성능으로 소프트웨어 업데이트를 자주 가능
  4. 애질리티 : 배포가 잦은 소규모팀에서 애자일 작업방식을 유도 가능
  5. 유연한 확장 : 부하용량에 도달 시 서비스의 새 인스턴스를 포함하는 클러스터에 신속하게 배포하여 부담을 완화 가능
  6. 지속적 배포 : 더욱 자주 release 및 realse 주기가 빠름
  7. 높은 유지관리성 및 테스트 편의성 : 새로운 기능을 실험해 보고 난 후 바로 롤백이 가능 따라서 코드를 보다 쉽게 업데이트하고 새로운 기능의 시장 출시를 앞당길 수 있음
  8. 독립적 배포 가능 : 개별적인 유닛이므로, 개별 기능을 쉽고 빠르게 배포 가능
  9. 기술 유연성 : 원하는 도구를 취사 선택가능
  10. 높은 안정성 : 전체 애플리케이션의 중단될 위험 없이 특정 서비스에 대한 변경사항 배포 가능


#### 1.2.2.1 마이크로서비스 아키텍쳐의 단점
  1. 무분별한 개발 확산 : 여러팀이 더 많은 장소에 더 많은 서비스를 만들기 때문에 모놀리스 아키텍쳐에 비해서 더 복잡해짐 따라서 관리가 되지않으면 개발속도가 느려지며 운영성증 저하
  2. 기하급수적인 인프라 비용 : 테스트도구, 배포 플레이북, 호스팅인프라, 모니터링 도구등에 대한 자체적 비용 발생
  3. 조직 오버헤드 추가 : 팀에서는 업데이트 및 인터페이스를 조정하기 위해 또 다른 커뮤니케이션과 공동작업이 이루어 져야 함
  4. 디버깅 문제 : 마이크로서비스는 로그집합을 가지고 있어 디버깅이 더 복잡함
  5. 표준화 부족 : 공통 플랫폼이 없어 로깅 표준 및 모니터링이 사용 됨
  6. 명확한 소유권 부족 : 더많은 서비스가 도입됨에 따라 팀의 수가 증가, 시간이 지나며 누구에게 문의를 해야 하는지 명확한 파악 불가

#### 1.2.3 마이크로식 아키텍쳐를 Docker에 적용
  1. Docker는 컨테이너가 많으면 다루기 힘듦
  2. Docker가 많을 때는 이를 아우르기 위해서 쿠버네티스를 사용
  3. Docker와 쿠버네티스 두가지 기술이 Container를 사용 시 가장 많이 언급되는 기술

#### 1.2.4 Docker의 장점(이점)
  1. 모듈성
  
    1.1 Docker의 컨테이너화 접근 방식은 전체 애플리케이션을 분해 할 필요 없이 애플리케이션의 일부를 분해하고, 업데이트 또는 복구하는 능력에 치중되어 있음
  
    1.2 사용자는 이 마이크로서비스 기반 접근 방식 이외에도 SOA(Service-oriented-architecture) 작동 방식과 동일하게 멀티플 애플리케이션 사이에서 프로세스를 공유
  
  2. 계층 및 이미지 버전 제어
  
    2.1 각 Docker 이미지 파일은 일련의 계층으로 이루어져 있으며 이 계층은 단일 이미지로 결합되어 있음
  
    2.2 이미지가 변경 될 떄 계층이 생성되고, 사용자가 실행 또는 복사같은 명령어를 지정할 때 마다 새 계층이 생성된다.
   
    2.3 Docker는 새로운 Container를 구축할 때 계층을 재사용하므로, 구축 프로세스가 훨씬 더 빨라진다.
  
    2.4 중간 변경사항이 이미지 사이에서 공유되므로, 속도, 규모, 효율성이 더 개선된다.
  
    2.5 계층화에는 버전 관리가 내재되어 있으며, 내장변경 로그가 기본적으로 적용되므로 Container 이미지를 완전히 제어 가능하다.
  
  3. 롤백★★★★★★★★★★★★★
  
    3.1 계층화에서 가장 유용한 부분은 롤백
  
    3.2 모든 이미지에는 계층이 있으며, 현재의 이미지 반복이 적절하지 않은 경우 이전 버전으로 롤백을 하면 된다.
  
    3.3 Agile 접근 방식을 지원하며 툴 관점으로 CI/CD를 수행하는데 도움을 준다.
  
  4. 신속한 배포
  
    4.1 각 프로세스의 컨테이너를 생성함으로써 유사한 프로세스를 새 앱과 빠르게 공유 가능
    
    4.2 컨테이너를 추가하거나 이동하기위해 OS를 부팅할 필요가 없으므로, 배포 시간이 크게 단축
    
    4.3 배포 속도가 빨라 컨테이너에서 생성된 데이터를 비용 효율적으로 쉽게 생성하고 삭제가 가능

****
## 2.1. Docker Image
* Docker Image란?
    
    컨테이너를 실행할 수 있는 실행파일, 설정 값들을 가지고 있는 것
    Image를 Container에 할당하고 실행하면 해당 프로세스가 동작하는 원리
    
    -------
    ![image](https://user-images.githubusercontent.com/44853842/177481669-49c5c1c0-5463-4275-abbf-645230096ac8.png)
    
    1. Ubuntu Image를 만들기 위해 Layer A,B,C가 들어간다.
    2. nginx Image를 만들기 위해서 Ubuntu  Image에 ngix Image가 추가
    실질적으로 더 Ubuntu와 ngix Image가 더해진 것이지만 과정은 ubuntu + ngix가 더해진 것이다.
    3. web Image를 만들려고 할 때 ubuntu Image에 nigix를 올린다음 web app을 올리는 것이 아닌 ngix base에 web app을 올려 이미지를 만든다. 

## 2.2. Docker File
* Docker File 이란?
    이미지 생성 출발점으로 이미지를 구성하기 위한 명령어들을 작성하여 이미지들을 구성할 수 있다.
    그 뜻은 Docker File을 읽을 수 있다면 해당 이미지가 어떻게 구성되어있는지 알 수 있다.
    
## 2.3. Docker Hub & Registry
* Docker Hub
  1. Docker Hub에서는 Image를 저장하고 관리 해 준다. 또한 많은 회사들이 Docker를 Software로 배포를 하여 공개 이미지들을 공유가 가능하다.
  2. Docker Hub 사용 시 Image를 docker pull하여 Container에 적용이 가능하다.

* Docker Registry
  1. Docker 보관소라고 생각하면 편함
  2. 누구나 Image를 Push 또는 Download가 가능하다.
  3. Docker Hub처럼 공개된 방식이 아닌 비공개 방식으로 저장소를 구축 가능하다.
  
 ![image](https://user-images.githubusercontent.com/44853842/177504400-e4b3c416-796e-4028-94c4-fbb61c435f4a.png)

  Docker Image Pull URL이다.
  그림과 같이 앞에 있는 URL을 적지 않으면 Docker Hub에서 Image를 Pull 받게되고 URL을 적어준다면 사설 저장소에서 Image를 받을 수 있다.

## 3.1 Docker Life Cycle
  ### Image
  ![image](https://user-images.githubusercontent.com/44853842/177508154-58f8e40d-b271-4b0d-9198-ff9f82cc9ab1.png)
  

## 3.2 Docker 명령어
  ### 3.2.0 Docker Login 명령어 
    `docker login[URL]` 

  ### 3.2.1 Docker 시작 명령어(Python) 
    
    `docker run -d -p 80:80 docker/getting-started` 

  ### 3.2.2 Docker Pull Docker 
    
    `docker pull [옵션] 이미지명[:태그명]` 
     
  ### 3.2.3 Docker create 
    
    `docker create <옵션> 이미지명 <명령어> <인자>` 
     
  ### 3.2.4 Docker run
    `docker run <옵션> 이미지명 <명령어> <인자>`
    
  ### 3.2.5 Docker stop
    `docker stop <옵션> 컨테이너명 <컨테이너명...>`
    
  ### 3.2.6 Docker rm, rmi 
    `docker rm`
    `docker rmi`
  
  ### 3.2.7 Docker commit
    `docker commit CONTAINER IMAGE_NAME`
    
  ### 3.2.8 Docker ps
    `docker ps`
    `docker ps -a`


## 4.1 Docker Image가 저장되는 방식

### 4.1.1 이전의 정리
  1. Container : 서버의 실행에 필요한 모든것(코드, 런타임, 시스템도구)들을 Container에 넣어 쉽게 추상화하고 어디에서든(GCP,AWS,Local-Machine)에서 실행이 가능
  2. Docker Image : Container의 모든 정보를 포함한 하나의 단위로 볼 수 있음
  3. Docker를 사용하는 이유 : Container를 활용하여 쉽게 개발환경과 운영환경을 동일하게 구성 가능하기 때문
  
### 4.1.1 Docker Container를 동시에 여러개 생성하여 구동하려면 어떻게 해야하나?
  1. docker run을 일일히 치기에는 너무 많으면 효율이 떨어진다.
  2. docker-compose를 사용하면 한번에 여러개의 container를 정의하고 실행 시킬 수 있다.(yml파일)
  
### 4.1.2 Docker Image가 저장되는 방식
`$ docker pull nginx:latest`
`Using default tag: latest`
`latest: Pulling from library/nginx`
`c499e6d256d6: Already exists`
`74cda408e262: Pull complete`
`ffadbd415ab7: Pull complete`
`Digest: sha256:282530fcb7cd19f3848c7b611043f82ae4be3781cb00105a1d593d7e6286b596`
`Status: Downloaded newer image for nginx:latest`
`docker.io/library/nginx:latest`

  1. 이런식으로 분리된 데이터를 레이어 라고 한다.
  2. 레이어는 Docker가 빌드 될 때 Dockerfile에 정의된 명령문(instructions)을 순서대로 실행하면서 만들어 진다.
  3. 레이어들은 각각 독립적으로 저장되며 읽기전용이라 임의로 수정할 수 없다.
  4. 실제로 레이어가 어떻게 저장되는지 확인 하려면 docker image inspect 명령어를 실행 후 hash값을 찾을 수 있다.
  5. 해시값으로 호스트 머신 내 어딘가 실제 레이너 내용이 저장된 것을 찾을 수 있다.

### 4.1.3 결과물 저장 장소
  ![image](https://user-images.githubusercontent.com/44853842/178099237-dafe698d-1eee-45f5-b938-f93422ad8918.png)


## 4.2 Docker Image layer에 대하여
  1. Docker Layer가 중요한 이유는 이미지를 빌드 할 때 마다 이미 생성된 레이어가 캐시되어 재사용 되기 때문에 빌드 시간을 단축 시킬수 있다.
  2. DockerFile에서 모든 명령문이 레이어가 되는것은 아니다.
  3. RUN, ADD, COPY 3가지만 레이어에 저장, CMD, LABEL, ENV< EXPOSE등과 같이 메타를 다루는 정보는 임시 레이어로써 도커 이미지사이즈에 영향을 주지 않음

![image](https://user-images.githubusercontent.com/44853842/178099297-dae6296d-38b6-47ae-945e-894b24882521.png)

  
  

This is a normal paragraph:

    This is a code block.
    
end code block.
```

실제로 적용해보면,

적용예:

*****
This is a normal paragraph:

    This is a code block.

end code block.
*****

> 한줄 띄어쓰지 않으면 인식이 제대로 안되는 문제가 발생합니다.

```
This is a normal paragraph:
    This is a code block.
end code block.
```

적용예:

*****
This is a normal paragraph:
    This is a code block.
end code block.
*****

### 2.4.1. 코드블럭
코드블럭은 다음과 같이 2가지 방식을 사용할 수 있습니다:

* `<pre><code>{code}</code></pre>` 이용방식

```
<pre>
<code>
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }

}
</code>
</pre>
```

<pre>
<code>
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
</code>
</pre>

* 코드블럭코드("\```") 을 이용하는 방법

<pre>
<code>
```
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
```
</code>
</pre>

```
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
```

**깃헙**에서는 코드블럭코드("\```") 시작점에 사용하는 언어를 선언하여 [문법강조(Syntax highlighting)](https://docs.github.com/en/github/writing-on-github/creating-and-highlighting-code-blocks#syntax-highlighting)이 가능하다.

<pre>
<code>
```java
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
```
</code>
</pre>

```java
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
```


## 2.5. 수평선 ```<hr/>```
아래 줄은 모두 수평선을 만든다. 마크다운 문서를 미리보기로 출력할 때 *페이지 나누기* 용도로 많이 사용한다.

```
* * *

***

*****

- - -

---------------------------------------
```

* 적용예
* * *

***

*****

- - -

---------------------------------------


## 2.6. 링크
* 참조링크

```
[link keyword][id]

[id]: URL "Optional Title here"

// code
Link: [Google][googlelink]

[googlelink]: https://google.com "Go google"
```

Link: [Google][googlelink]

[googlelink]: https://google.com "Go google"

* 외부링크
```
사용문법: [Title](link)
적용예: [Google](https://google.com, "google link")
```
Link: [Google](https://google.com, "google link")

* 자동연결
```
일반적인 URL 혹은 이메일주소인 경우 적절한 형식으로 링크를 형성한다.

* 외부링크: <http://example.com/>
* 이메일링크: <address@example.com>
```

* 외부링크: <http://example.com/>
* 이메일링크: <address@example.com>

## 2.7. 강조
```
*single asterisks*
_single underscores_
**double asterisks**
__double underscores__
~~cancelline~~
```

* *single asterisks*
* _single underscores_
* **double asterisks**
* __double underscores__
* ~~cancelline~~

> ```문장 중간에 사용할 경우에는 **띄어쓰기** 를 사용하는 것이 좋다.```   
> 문장 중간에 사용할 경우에는 띄어쓰기를 사용하는 것이 좋다.


## 2.8. 이미지
```
![Alt text](/path/to/img.jpg)
![Alt text](/path/to/img.jpg "Optional title")
```
![석촌호수 러버덕](http://cfile6.uf.tistory.com/image/2426E646543C9B4532C7B0)
![석촌호수 러버덕](http://cfile6.uf.tistory.com/image/2426E646543C9B4532C7B0 "RubberDuck")

사이즈 조절 기능은 없기 때문에 ```<img width="" height=""></img>```를 이용한다.

예
```
<img src="/path/to/img.jpg" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="RubberDuck"></img><br/>
<img src="/path/to/img.jpg" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="RubberDuck"></img>
```

<img src="http://cfile6.uf.tistory.com/image/2426E646543C9B4532C7B0" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="RubberDuck"></img><br/>
<img src="http://cfile6.uf.tistory.com/image/2426E646543C9B4532C7B0" width="40%" height="30%" title="%(비율) 크기 설정" alt="RubberDuck"></img>

## 2.9. 줄바꿈
3칸 이상 띄어쓰기(` `)를 하면 줄이 바뀐다.

```
* 줄 바꿈을 하기 위해서는 문장 마지막에서 3칸이상을 띄어쓰기해야 한다. 
이렇게

* 줄 바꿈을 하기 위해서는 문장 마지막에서 3칸이상을 띄어쓰기해야 한다.___\\ 띄어쓰기
이렇게
```

* 줄 바꿈을 하기 위해서는 문장 마지막에서 3칸이상을 띄어쓰기해야 한다. 이렇게

* 줄 바꿈을 하기 위해서는 문장 마지막에서 3칸이상을 띄어쓰기해야 한다.    \
이렇게


****
# 3. 마크다운 사용기
## 3.1. 위지윅(WSYWIG) 에디터
우리가 흔하게 접하는 웹에서 사용되는 에디터(네이버, 다음, 구글 등)이 대부분 위지윅 에디터에 속하며 기본적으로 HTML을 이용하여 스타일을 적용하여 문장을 꾸미는 형태를 취하게 된다. 그래서 하루패드와 같은 마크다운 에디터의 View 영역의 내용을 복사하여 붙여넣기를 하면 대체적으로 View영역에서 보이는 그대로 복사되는 편이다. 다만, 붙여넣기 이후에 문장들을 수정하려고 할 떄 문제가 되는데, 이는 스타일이 포함된 태그가 수정과정에서 변형되면서 전체적인 영향을 끼치는 탓이다. 티스토리 블로그에서는 쉽지 않고... 워드프레스의 경우에는 마크다운으로 작성된 포스트를 HTML로 변환해주는 기능을 활용하는 것이 좋다.
결론은, **복사해서 붙여넣기하면 가급적이면 본문은 수정하지 않는 것이 좋다.**

## 3.2. 깃헙Github, 비트버킷Bitbucket과 요비Yobi 등
최근 유행하는 협업개발플랫폼의 경우에는 마크다운을 변환하는 컨버터 기능을 기본탑재하고 있기 때문에 마크다운 문법으로 작성한 텍스트를 그대로 복사해서 붙여넣거나 업로드하는 것만으로 마크다운의 적용이 가능하다.

## 3.3. MS워드 적용
View 영역의 항목을 그대로 붙여넣거나 HTML 내보내기 등으로 생성한 파일을 불러오는 형태로 사용가능하다. 적용한 헤더를 워드가 읽어드리면서 목차에 적용하기 때문에 이를 활용하면 목차까지도 손쉽게 적용이 가능해진다.

*****

# 4. 정리
마크다운은 기본문법만 알고있다면 일반 텍스트편집기에서도 손쉽게 작성이 가능한 마크업언어다. 현재 다양한 도구와 플랫폼에서 지원하고 있기 때문에 더욱 손쉽게 스타일적용된 문서를 작성할 수 있어 점점 널리 사용되고 있다.   

> 마크다운을 이해하고 사용하면서 쉽고 빠르게 스타일문서를 작성해보세요.

저는 Dropbox 프로를 구매해서 집-랩탑-스마트폰이 각각 연동을 시켜서 사용하고 있습니다. 드랍박스에 저장된 마크다운 문서는 Dropbox 웹서비스 상에서 제공하기 때문에 웹상에서 바로 열람할 수도 있어 링크를 걸어서 다른 사람과 공유하는 형식으로 사용하고 있다.
* 링크 예: [Markdown 설명](https://www.dropbox.com/s/mzp9tq4qtfjdlif/20141021_markdown_use_tip.md?dl=0)

***** 

# P.S.
최근에는 [Notion](https://www.notion.so/product) 을 조금씩 사용중이다. Notion 에서 작성한 문서는 Atom(<https://atom.io/>), Visual Studio Code(<https://code.visualstudio.com/>), Notepad++(<https://notepad-plus-plus.org/>)텍스트 편집기에 복붙(복사하고 붙여넣기)하면 마크다운문법으로 작성된 문장이 기입되고 이지윅 에디터를 제공하는 웹에디터에 붙여넣기 하면 거의 완벽한 형태로 복사된다. 그래서 애용중이다.

## ○ 참고문서
* [78 Tools for writing and previewing Markdown](http://mashable.com/2013/06/24/markdown-tools/)
* [John gruber 마크다운 번역](http://nolboo.github.io/blog/2013/09/07/john-gruber-markdown/)
* [깃허브 취향의 마크다운 번역](http://nolboo.github.io/blog/2014/03/25/github-flavored-markdown/)
* [허니몬의 마크다운 작성법](http://www.slideshare.net/ihoneymon/ss-40575068)
* Notion.so(<https://www.notion.so/product>)
* Atom(<https://atom.io/>)
* Visual Studio Code(<https://code.visualstudio.com/>)
* Notepad++(<https://notepad-plus-plus.org/>)

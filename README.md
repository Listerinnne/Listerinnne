# 목차
- [UML 클래스 다이어그램 개요](#uml-클래스-다이어그램-개요)
  - [목차](#목차)
  - [클래스](#클래스)
    - [SsafitApplication](#ssafitapplication)
    - [MainUi](#mainui)
    - [SsafitUtil](#ssafitutil)
    - [Video](#video)
    - [VideoDao](#videodao)
    - [VideoDaoImpl](#videodaoimpl)
    - [VideoUi](#videoui)
    - [VideoReview](#videoreview)
    - [VideoReviewDao](#videoreviewdao)
    - [VideoReviewDaoImpl](#videoreviewdaoimpl)
    - [VideoReviewUi](#videoreviewui)
  - [관계](#관계)
  - [개선 사항](#개선-사항)
    - [문서화 강화](#문서화-강화)
    - [일관된 명명 규칙](#일관된-명명-규칙)
    - [클래스 설계 개선](#클래스-설계-개선)
    - [의존성 주입](#의존성-주입)
    - [오류 처리](#오류-처리)
    - [메서드 접근성](#메서드-접근성)
    - [유틸리티 클래스 강화](#유틸리티-클래스-강화)
    - [주석과 애노테이션](#주석과-애노테이션)
    - [테스트](#테스트)
    - [디자인 패턴](#디자인-패턴)
    - [JSON 처리](#json-처리)
    - [GSON 라이브러리와 Maven 사용](#gson-라이브러리와-maven-사용)
    - [결론](#결론)
- [타임라인](#타임라인)
  - [Github으로 협업 방법](#Github으로-협업-방법)


# UML 클래스 다이어그램 개요

이 문서는 `com.ssafy.fit` 애플리케이션의 UML 클래스 다이어그램에 대한 개요를 제공합니다. 다이어그램에는 다양한 클래스, 그들의 속성, 메서드 및 클래스 간의 관계가 포함되어 있습니다.

## 클래스

### SsafitApplication
- **패키지:** com.ssafy.fit.test
- **설명:** 애플리케이션의 시작점입니다.
- **메서드:**
  - `public void main(String[] args)` - 애플리케이션을 시작합니다.

### MainUi
- **패키지:** com.ssafy.fit.ui
- **설명:** 메인 사용자 인터페이스를 관리합니다.
- **메서드:**
  - `public void service()` - UI 서비스를 시작합니다.
  - `private void exit()` - 애플리케이션을 종료합니다.

### SsafitUtil
- **패키지:** com.ssafy.fit.util
- **설명:** 유틸리티 메서드를 제공합니다.
- **속성:**
  - `private static Scanner sc` - 사용자 입력을 받기 위한 스캐너 객체입니다.
- **메서드:**
  - `private SsafitUtil()` - 생성자.
  - `public static String input(String msg)` - 사용자로부터 문자열 입력을 받습니다.
  - `public static int inputInt(String msg)` - 사용자로부터 정수 입력을 받습니다.
  - `public static void printLine()` - 기본 줄을 출력합니다.
  - `public static void printLine(char ch)` - 특정 문자를 사용하여 줄을 출력합니다.
  - `public static void printLine(char ch, int len)` - 특정 문자와 길이를 사용하여 줄을 출력합니다.
  - `public static void screenClear()` - 화면을 지웁니다.

### Video
- **패키지:** com.ssafy.fit.model
- **설명:** 비디오 정보를 담고 있는 클래스입니다.
- **속성:**
  - `private int no` - 비디오 번호
  - `private String title` - 비디오 제목
  - `private String part` - 비디오 파트
  - `private String url` - 비디오 URL
- **메서드:**
  - `public int getNo()` - 비디오 번호를 반환합니다.
  - `public void setNo(int no)` - 비디오 번호를 설정합니다.
  - `public String getTitle()` - 비디오 제목을 반환합니다.
  - `public void setTitle(String title)` - 비디오 제목을 설정합니다.
  - `public String getPart()` - 비디오 파트를 반환합니다.
  - `public void setPart(String part)` - 비디오 파트를 설정합니다.
  - `public String getUrl()` - 비디오 URL을 반환합니다.
  - `public void setUrl(String url)` - 비디오 URL을 설정합니다.
  - `public String toString()` - 비디오 정보를 문자열로 반환합니다.

### VideoDao
- **패키지:** com.ssafy.fit.model.dao
- **설명:** 비디오 데이터 접근 객체를 정의하는 인터페이스입니다.
- **메서드:**
  - `public List<Video> selectVideo()` - 모든 비디오를 선택합니다.
  - `public Video selectVideoByNo(int no)` - 비디오 번호로 비디오를 선택합니다.

### VideoDaoImpl
- **패키지:** com.ssafy.fit.model.dao
- **설명:** VideoDao 인터페이스를 구현하는 클래스입니다.
- **속성:**
  - `private List<Video> list` - 비디오 리스트
  - `private static VideoDaoImpl instance` - 싱글톤 인스턴스
- **메서드:**
  - `private VideoDaoImpl()` - 생성자
  - `public static synchronized VideoDaoImpl getInstance()` - 싱글톤 인스턴스를 반환합니다.
  - `public List<Video> selectVideo()` - 모든 비디오를 반환합니다.
  - `public Video selectVideoByNo(int no)` - 비디오 번호로 비디오를 반환합니다.

### VideoUi
- **패키지:** com.ssafy.fit.ui
- **설명:** 비디오와 관련된 UI를 관리합니다.
- **속성:**
  - `private VideoDao videoDao` - 비디오 데이터 접근 객체
  - `private static VideoUi instance` - 싱글톤 인스턴스
- **메서드:**
  - `private VideoUi()` - 생성자
  - `public static VideoUi getInstance()` - 싱글톤 인스턴스를 반환합니다.
  - `public void service()` - UI 서비스를 시작합니다.
  - `private void listVideo()` - 비디오 리스트를 출력합니다.
  - `private void detailVideo()` - 비디오 상세 정보를 출력합니다.

### VideoReview
- **패키지:** com.ssafy.fit.model
- **설명:** 비디오 리뷰 정보를 담고 있는 클래스입니다.
- **속성:**
  - `private int videoNo` - 비디오 번호
  - `private int reviewNo` - 리뷰 번호
  - `private String nickName` - 작성자 닉네임
  - `private String content` - 리뷰 내용
- **메서드:**
  - `public int getVideoNo()` - 비디오 번호를 반환합니다.
  - `public void setVideoNo(int videoNo)` - 비디오 번호를 설정합니다.
  - `public int getReviewNo()` - 리뷰 번호를 반환합니다.
  - `public void setReviewNo(int reviewNo)` - 리뷰 번호를 설정합니다.
  - `public String getNickName()` - 작성자 닉네임을 반환합니다.
  - `public void setNickName(String nickName)` - 작성자 닉네임을 설정합니다.
  - `public String getContent()` - 리뷰 내용을 반환합니다.
  - `public void setContent(String content)` - 리뷰 내용을 설정합니다.

### VideoReviewDao
- **패키지:** com.ssafy.fit.model.dao
- **설명:** 비디오 리뷰 데이터 접근 객체를 정의하는 인터페이스입니다.
- **메서드:**
  - `public int insertReview(VideoReview videoReview)` - 리뷰를 삽입합니다.
  - `public List<VideoReview> selectReview(int videoNo)` - 비디오 번호로 리뷰를 선택합니다.

### VideoReviewDaoImpl
- **패키지:** com.ssafy.fit.model.dao
- **설명:** VideoReviewDao 인터페이스를 구현하는 클래스입니다.
- **속성:**
  - `private static int reviewNo` - 리뷰 번호
  - `private Map<Integer, List<VideoReview>> videoReviewDb` - 비디오 리뷰 데이터베이스
  - `private static VideoReviewDaoImpl instance` - 싱글톤 인스턴스
- **메서드:**
  - `private VideoReviewDaoImpl()` - 생성자
  - `public static synchronized VideoReviewDaoImpl getInstance()` - 싱글톤 인스턴스를 반환합니다.
  - `public int insertReview(VideoReview videoReview)` - 리뷰를 삽입합니다.
  - `public List<VideoReview> selectReview(int videoNo)` - 비디오 번호로 리뷰를 반환합니다.

### VideoReviewUi
- **패키지:** com.ssafy.fit.ui
- **설명:** 비디오 리뷰와 관련된 UI를 관리합니다.
- **속성:**
  - `private VideoReviewDao videoReviewDao` - 비디오 리뷰 데이터 접근 객체
  - `private static VideoReviewUi instance` - 싱글톤 인스턴스
  - `private int videoNo` - 비디오 번호
- **메서드:**
  - `private VideoReviewUi(int videoNo)` - 생성자
  - `public static VideoReviewUi getInstance(int videoNo)` - 싱글톤 인스턴스를 반환합니다.
  - `public void service()` - UI 서비스를 시작합니다.
  - `private void listReview()` - 리뷰 리스트를 출력합니다.
  - `private void registReview()` - 리뷰를 등록합니다.

## 관계
- **상속:**
  - `VideoDaoImpl` implements `VideoDao`
  - `VideoReviewDaoImpl` implements `VideoReviewDao`

- **연관 관계:**
  - `SsafitApplication` uses `MainUi`
  - `MainUi` uses `VideoUi`
  - `VideoUi` uses

 `VideoReviewUi`

- **집합 관계:**
  - `VideoUi` aggregates `VideoDao`
  - `VideoReviewUi` aggregates `VideoReviewDao`
  - `VideoDaoImpl` aggregates `Video`
  - `VideoReviewDaoImpl` aggregates `VideoReview`

## 개선 사항
### 문서화 강화
- 각 클래스와 메서드에 대한 설명을 추가하여 코드의 가독성을 높입니다.
- 각 메서드의 파라미터와 반환값에 대한 설명을 추가합니다.

### 일관된 명명 규칙
- 클래스 이름, 메서드 이름, 변수 이름이 일관된 명명 규칙을 따르도록 합니다.

### 클래스 설계 개선
- 단일 책임 원칙을 준수하여 각 클래스가 단일 책임만 가지도록 합니다.
- 인터페이스가 특정 기능에만 집중하도록 하고, 필요할 경우 작은 단위로 분리합니다.

### 의존성 주입
- 생성자 주입이나 세터 주입을 사용하여 의존성을 관리합니다.

### 오류 처리
- 각 메서드에 적절한 오류 처리를 구현합니다.

### 메서드 접근성
- 메서드의 접근성을 검토하고 적절하게 캡슐화합니다.

### 유틸리티 클래스 강화
- 유틸리티 클래스가 인스턴스화되지 않도록 모든 메서드가 static인 경우 생성자를 private으로 만듭니다.

### 주석과 애노테이션
- 적절한 위치에 주석과 애노테이션을 사용하여 코드 가독성과 유지 보수성을 향상시킵니다.

### 테스트
- 각 클래스와 메서드에 대한 단위 테스트를 구현하여 코드 품질을 유지하고 버그를 조기에 발견할 수 있도록 합니다.

### 디자인 패턴
- 적용 가능한 경우 디자인 패턴을 사용합니다.

### JSON 처리
- JSON 처리를 위해 GSON 라이브러리를 사용하여 객체를 직렬화하고 역직렬화합니다.

### GSON 라이브러리와 Maven 사용
이 프로젝트는 Maven을 사용하여 종속성을 관리하고 빌드를 수행합니다. Maven을 사용하면 프로젝트의 종속성을 자동으로 다운로드하고 관리할 수 있습니다.

프로젝트의 `pom.xml` 파일에 필요한 의존성이 명시되어 있으며, GSON 라이브러리 또한 Maven 중앙 저장소에서 자동으로 다운로드됩니다. 따라서 GSON의 JAR 파일을 직접 로컬로 연결할 필요가 없습니다. Maven이 자동으로 필요한 라이브러리를 다운로드하고 프로젝트에 포함시킵니다.

Maven을 사용하여 GSON을 프로젝트에 포함시키기 위해 `pom.xml` 파일에 다음과 같은 의존성을 추가했습니다:

```xml
<dependency>
    <groupId>com.google.code.gson</groupId>
    <artifactId>gson</artifactId>
    <version>2.10.1</version>
</dependency>
```

## 결론
이 UML 클래스 다이어그램은 `com.ssafy.fit` 애플리케이션의 구조와 클래스 간의 관계를 나타냅니다. 클래스는 패키지별로 잘 정리되어 있으며, 클래스 간의 관계가 명확하게 정의되어 있어 견고하고 유지 보수 가능한 아키텍처를 제공합니다. 제안된 개선 사항들을 적용하면 프로그램이 더 견고하고 유지 보수하기 쉬워지며, 다른 개발자들이 더 쉽게 이해하고 작업할 수 있을 것입니다.


# Babel

- 최신 사양의 소스코드를 구형 브라우저에서도 동작하는 소스코드로 변환(트랜스 파일링) 할 수 있음

> 트랜스파일(transplie): 어떤 특정 언어로 작성된 소스 코드를 다른 소스 코드로 변환하는 것
> 

### 개발환경 구축

- Babel 설치

```bash
yarn init
yarn add @babel/core @babel/cli
```

- Babel 프리셋 설치
    - 필요한 플러그인들을 목적에 따라 세트로 묶어 놓은 것
    - 함께 사용되어야 하는 Babel 플러그인을 모아 둔 것
        - @babel/preset-env
        - @babel/preset-flow
        - @babel/preset-react
        - @babel/preset-typescript
    - 프로젝트 지원 환경에 맞춰 동적으로 결정해줌
        - 프로젝트 지원 환경은 .browserslistrc파일에 상세히 설정할 수 있음
    
    ```bash
    yarn add @babel/preset-env
    ```
    
- Babel.config.json파일 설정
    - 프로젝트 루트 폴더에 babel.config.json 파일 생성
    
    ```bash
    {
    	"presets":["@babel/preset-env"] //@babel/preset-env를 사용하겠다는 의미
    }
    ```
    
- 트랜스파일링
    - Babel CLI명령어 등록
        - targetDirectory에 있는 모든 자바스크립트 파일들을 트랜스파일링한 후 그 결과물을 outdirectory에 저장
        - options
            - -w(—watch): 타겟 폴더에 있는 모든 자바스크립트파일들의 변경을 감지하여 자동으로 트랜스 파일링 함
            - -d(—out-dir): 트랜스 파일링된 결과물이 저장될 폴더를 지정( 지정하지 않으면 자동 생성)
    
    ```json
    //package.json
    {
    	//....,
    	"scripts":{ 
    		"build": "babel {targetDirectory} -w -d {outDirectory}"
            }
    }
    ```
    
- 테스트 코드 작성
- 트랜스 파일링 실행

```bash
yarn run build
```

### 빌드 단계

1. 파싱(Parsing): 코드를 읽고 추상 구문 트리(AST)로 변환하는 단계
2. 변환(Transforming): 추상 구문 트리를 변경
3. 출력(Printing): 변경된 결과물을 출력

⇒ 바벨은 파싱과 출력을 담당, 플러그인이 변환을 담당

### 플러그인(Plugin)

- 바벨이 어떤 코드를 어떻게 변활할지에 대한 규칙을 나타냄
- presets에 속해 있는 플러그인 외에 추가로 사용하고 싶다면 설치 후 babel.config.json변경

```bash
{
	"presets":["@babel/preset-env"],
	"plugins":["@babel/plugin-proposal-class-properties"]
}
```

[Babel · The compiler for next generation JavaScript](https://babeljs.io/)
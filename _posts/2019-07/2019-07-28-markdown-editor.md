---
layout : post
published : true
title : 마크다운을 렌더링하는 노트앱이 필요하다
subtitle : 깃허브 API 사용해서 커밋할 수 있을까
tags : [markdown, github, api]
---
#### 마크다운 노트
깃허브 블로그에 글을 올리려면 `마크다운`으로 작성해야하는데 내가 임시 작성하는 `에버노트`에는 마크다운 미리보기 기능이 없어 내 글이 어떤 식으로 그려지는지 확인 할 수 없다.
  
물론 컴퓨터로 작성하는 경우에는 `vscode`를 이용한다. 하지만 나는 핸드폰으로도 글을 쓰고 싶었고 마크다운 미리보기 기능이 있는 노트앱이 필요한 것이였다.
그래서 다른 노트 앱들을 찾아봤지만 내가 원하는 마크다운 기능을 지원하는 **무료**버전을 찾을 수 없었다. ~내가 찾다만 기분도 있지만~ 이것은 바로 사이드 프로젝트 타이밍!!!
  
#### 마크다운 코드를 변환시켜줘
우선 간단하게 마크다운 코드를 작성했고 이것을 변환해서 보여줘야하는데 막막했다.
처음엔 간단하게 정규식 써서 마크다운 태그가 있으면 HTML로 변환시켜줘야지 생각했다가 큰 착각이였다. 너무 일이 커진다.
  
당연히 `라이브러리`가 있겠지 생각하며 뭐라고 찾아봐야할까 왜 안나오지 하던 중 우연하게 찾게된 나와 비슷한 생각을 한듯한 블로그 발견했다.
검색어를 수정했고 마크다운 파서 라이브러리를 찾아냈다. 그 중 미리보기 기능을 내가 원하는 모습으로 구현되어있는 `react-native-markdown-renderer`를 사용하기로 했다.

#### 마크노트
`react-native-markdown-renderer`는 입력한 HTML을 마크다운으로 변환하여 렌더링해주는 라이브러리이다.
```js
import Markdown from 'react-native-markdown-renderer';

<Markdown>{HTML 코드}</Markdown>
```
사용법도 간단하게 구현되어 있다. `Markdown`안에 작성된 HTML 코드는 마크다운 형식에 맞게 변환되어 그려진다.
이를 통해 내가 구현하고자 했던 앱의 기능은 이렇다.
  
1. 마크다운 코드로 노트 작성 및 저장
2. 저장된 노트는 목록에서 마크다운이 적용된 화면으로 미리보기
3. HTML로만 볼 수 있는 화면을 만들고 해당 노트 내용 전체 복사 가능
  
#### 이런게 더 있으면 좋겠다
이 노트를 만들게 된 이유는 깃허브에 올리고 블로그에 올리려는 글을 미리보면서 작성하고자 했던 것이다.
여기까지 마크다운으로 작성된 코드를 미리보는 것은 확인하였다. 그렇다면 깃허브에 바로 커밋까지 할 수 없을까?
  
`깃허브API`를 한번 찾아보니 될 것도 같은데.. 그럼 한번 시도해보려고 한다.
(많은 도움을 받은 블로그 -> [깃허브로 로그인하기](https://gist.github.com/ninanung/2ad24c760e81401ed65f13f634a25e73))
  
#### 서버가 필요할까
처음에는 참고한 블로그를 따라서 `nodejs` 서버를 돌렸고 앱에서 나가는 api를 서버에서 받아서 다시 github api를 콜하도록 만들었다.
`github oauth`에는 `redirect url`이 필요한데, 토큰값을 해당 url로 리턴해주기 위해 설정하도록 되어있다.
나 또한 서버의 특정 url로 리턴 받을 수 있도록 하였고 토큰은 잘 넘어왔다.
  
그러나 서버로 넘어온 토큰값을 `앱의 특정 라우터`로 어떻게 전달해야 하는지 방법을 찾지 못했다.
앱에 스키마를 설정해서 보내볼까 했는데 이미 켜져있는 앱 위에 띄워진 웹뷰에서 리다이렉트 되는 스키마는 제대로 작동하지 않는듯 하였다.
그러다 의문이 든 것은 나는 앱을 만들고자 하는것인데 꼭 서버를 돌려야할까? 위의 블로그는 웹을 만들고자 했기에 nodejs로 서버를 돌리고 api를 서버에서 처리하여 cors도 해결할 수 있도록 구현하였다.
하지만 앱의 경우 cors가 발생하지 않는다. `axios`로 api를 보내서 필요한 값만 그대로 사용하면 되는데 너무 참고서를 많이 봤나보다.
  
웹뷰에 리다이렉트 된 값을 서버에서 앱의 특정 라우터로 보내지 못해 어려움이 있었던 문제는 곧바로 해결되었다.
`리턴되는 값을 그대로 전달해주고 웹뷰는 닫아버렸다!`
  
#### 진행사항
서버가 필요할까? 웹뷰에서 앱으로 어떻게 리턴하지? 하는 문제들을 해결하고나니 진행속도가 쑥쑥 올라갔다.
아직 원하던 api를 전부 찾지는 못했지만(원하는게 다 있는지 확인하지 못했다) 로그인하고 레포지터리 리스트를 그려주고 해당 레포의 커밋리스트들을 그려주는데 성공했다.
원하는 것들을 정리해보면
  
1. 해당 레포의 소스 파일 경로 가져오기
2. 해당 파일의 내용을 가져와서 마크다운 렌더링
3. 변경 후 커밋
  
`될까? 되겠지!`
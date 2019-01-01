---
layout : post
published : true
title : 안드로이드 카드게임
subtitle : 토이2 뇌순발력 카드게임
tags : [android,toy]
---

## 많이 놀았다
첫번째로 만든 계산기 수정은 미뤄두고 계속 놀았다.

세상엔 참 많은 놀거리가 있다.

연말인데 그동안을 돌아보며 화장실에서 갑자기 생각난 카드 형식의 미니 게임

*화장실처럼 집중하기 좋은 곳이 따로없다*


## 안드로이드 카드게임

- 문제는 사칙연산
- 정답은 카드로 여러장 제시
- 카운트다운
- 난이도에 따라 사칙연산 후 해당하는 값(계산, 앞, 뒤, 앞+뒤 숫자)

먼저 랜덤 숫자로 문제를 생성하고 정답을 계산
사칙연산에 따라 보기 생성방식을 다르게 하였다

```java

    /*
    NOTE 2018-12-29
    문제 생성 : 랜덤 수 2개, 사칙연산
    
    NOTE 2018-12-30
    보기 생성 : 덧셈뺄셈, 곱셈나눗셈에 따른 보기방식
    */
	
    private void init() {

        int random1 = (int) (Math.random() * 50 + 1);
        int random2 = (int) (Math.random() * 50 + 1);
        int operator = (int) (Math.random() * 4);
        String[] operatorArr = {"+", "-", "*", "/"};
        
	int answer = calc(random1, random2, operator);

        TextView textPreview = (TextView) findViewById(R.id.quiz);
        textPreview.setText(quiz(random1, random2, operatorArr[operator]));

        TextView answerPreview = (TextView) findViewById(R.id.answer);
        answerPreview.setText("정답 : " + answer);

        TextView exPreview = (TextView) findViewById(R.id.ex_btn);
        exPreview.setText("보기 : " + exArr[0] + " / " + exArr[1] +" / " + exArr[2] +" / "
                + exArr[3] +" / " + exArr[4] +" / " + exArr[5] + " / "
                + exArr[6] +" / " + exArr[7] +" / " + exArr[8]);
    }

    private String quiz(int ran1, int ran2, String operator){
        return ran1 + " " + operator + " " + ran2 + " = ?";
    }

    private int calc(int ran1, int ran2, int operator){
      int answer = 0;
      if(operator == 0){
        answer = ran1 + ran2;
      }else if(operator == 1){
        answer = ran1 - ran2;
      }else if(operator == 2){
        answer = ran1 * ran2;
      }else if(operator == 3){
        answer = ran1 / ran2;
      }else{
        // 에러 발생
      }
          return answer;
    }
    
    private int[] calcEx(int operator, int answer){
        int exArr[] = new int[9];
        
        // 정답의 위치 난수 생성
        int m = (int) (Math.random() * 9);
        
        // 덧뺄셈 : 정답 +-1
        // 곱나눗셈 : 정답 +-10
        if(operator == 0 || operator == 1){
           for(int i = 0 ; i < 9 ; i++){
               exArr[i] = answer + i - m;
           }
        }else if(operator == 2 || operator == 3){
            for(int i = 0 ; i < 9 ; i++){
                exArr[i] = answer + (i - m)*10;
            }
        }else{
            // 에러 발생
        }
        return exArr;
    }
```

#### 글이 안올라가는 경우
- title, subtitle에 괄호가 있으면 안되는것같다
- 수정했는데도 레이아웃이 적용되지 않아 : 사이를 띄워주었더니 되었다

***수정***
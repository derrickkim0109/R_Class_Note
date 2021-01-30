# 데이터 처리
     - library(dplyr) = display R
     - epal.Length 기준으로 오름차순 정렬하기
     - Sepal.Length 기준으로 오름차순 정렬후 1열과 2열만 보기
     - Sepal.Length 기준으로 정렬후 동일한 크기를 가진 데이터 발생시 
     - Petal.Length 기준으로 오름차순 정렬하기
     - Sepal.Length 기준으로 내림 차순 정렬
---     
### Sampling
     -  Random sampling(중복값을 허용하지 않음 )
     -  집단의 특성을 다 가지고 있어야함.
     -  iris의 Sampling 
     -  각 분류별로 따로 따로 해야 한다.
     
---
### 부분집합
     - 부분집합은 모집단에서 조건을 가지고 필요한 데이터만 추출하는 것이다. 
     - subset
     - 내가 데이터 어떤 부분을 뽑아 왔다면 꼭 structure를 확인 해봐야한다.
     - factor 조정
     - iris에서 Species가 setosa 이고 Sepal.Length가 5보다 큰 자료 추출하기
     - subset으로 필요없는 컬럼 지우기
     - subset(iris, select=Species)
     - '-Species' 하면 빼고 나온다
---
### 그룹연산 함수
    # Species 별로 Sepal.Width의 평균 구하기 
    mean(subset(iris, Species == 'setosa')$Sepal.Width)
    # (~) Tilt 연산자 
    # Species 별로 Sepal.Length 평균 구하기
    aggregate(Sepal.Length ~ Species, iris, mean)
    # ID 

---
### 서울 교통사고 조사 데이터 Set
                
    --     # 컬럼이 700개면??
            # for문을 이용한 NA 확인하기
            # 컬럼 갯수 먼저
            # ncol(seoul)
            # 매번 데이터 새로 받았을때 무조건 해야한다.
            for (i in 1:ncol(seoul)){
            #print(sum(is.na(seoul[,i]))) <- 컬럼명이 뭔지 모르자나!?
            cat(colnames(seoul[i]), ':', sum(is.na(seoul[,i])),"\n")
            }
            
            # 연도,월,자치구명 -> 고정건수 이것들을 주로 확인해보면된다
            # 발생건수, 사망자수, 부상자수 -> 가변건수 
            
            # 머를 체크 해야하나? 각 년도마다 1~12 까지 제대로 있냐? 확인해야 한다. 
            # 먼저이것부터 !
---
### 컬럼별 Data 확인
        # 연도 ---> 똑같냐? 빈도수 확인해라
        # regionAcc.mean의 발생건수를 기준으로 내림차순으로 정렬하기
        # 1등이 강남구야? 아니? 초딩이니? ---> 표준편차 확인해봐(고딩수준)
        # regionAcc.sd의 발생건수를 기준으로 내림차순으로 정렬하기
        # 표준편차 어디 써먹니?--->>
        # 자치구별 발생건수의 변동계수를 구하여라 ( 편차를 구하는 이유는 변동계수(지표값)를 구하기 위해 )
        # 변동계수 = 표준편차 / 평균   변동계수 = cv
        EX)
        # 서울시 교통사고 부상자수에 대한 변동계수 구하기
        # 1.평균
        region.injury.mean <- aggregate(부상자수 ~ 자치구명 ,seoul, mean)
        # 2.표준편차
        region.injury.sd <- aggregate(부상자수 ~ 자치구명 ,seoul, sd)
        # 3.변동계수
        region.injury.cv <- region.injury.sd$부상자수 /region.injury.mean$부상자수
        # 4.dataframe 만들기
        region.injury <- data.frame(자치구명 = region.injury.mean$자치구명,
                                    변동계수 = region.injury.cv)
        # 5.정렬하기
        arrange(region.injury,변동계수)
        
        -
        # 상관계수 percentage 
        # 0 ~ 0.3 : 상관없음
        # 0.3 ~ 0.5 : 약한 상관관계
        # 0.5 ~ 0.7 : 상관 있음
        # 0.7 ~ : 강한 상관관계가 있음
        
---
### 데이터 시각화

    -- Graph그릴때 무조건 이런방식으로 하라!
            x <- 1:10
            y <- 1:10
            # (x축,y축)
            plot(x, y,
                xlim = c(0,11), # x축의 범위 설정
                ylim = c(0,11)
                )
            # -> 효과를 줘라 
            # 발생건수가 150이상이면 빨간색 아니면 파란색으로 표현하기 
            
        - par(family = "AppleGothic") # for mac 
        -# Main Title 
        # 꺽은선 그래프 
        # 점과 꺽은선 그래프 
        # 점이 빠진 꺽은선 그래프 
        # 점과 꺽은선을 중첩한 그래프 
        # 수직선 그래프 
        # 데이터가 무지 많은경우 -> 막대그래프 보다 수직선 그래프가 훨씬 낫다.
        # 초기값을 기초로한 계단 모양 그래프 
        # 데이터 막 섞여있을경우
        # 최종값을 기초로한 계단 모양 그래프 
        # 데이터 막 섞여있을경우
        lty = 2 # line type : 0 ~ 6까지 있다. 

        
---
###  선그래프
    - 


----------
# 시험 문제이다.
        par(family = "AppleGothic") # for mac

        # abc 데이터  - 1 --> default 값이라 pch = 21dlek. 
        plot(abc,
             type ='o',
             ylim = c(0,400),
             col = 'red',
             axes = F, # x, y의 자표 Frame제거 = 축은 안쓰겠다.
             ann = F # x, y의 label 제거 
            )

        # x 축과 x축의 Label을 설정
        axis(1, at = 1:5, lab = c('서울','대전','대구','광주','원주'))

        # y축 y축의 라벨을 설정
        axis(2, ylim =c(0,400))

        # main title 지정
        title(main ='과일 판매량', col.main ='red')

        # x축 Title 지정
        title(xlab ='지역', col.lab = 'blue')

        # y축 Title 지정
        title(ylab ='판매량', col.lab ='blue')

        # def 데이터  - 2
        # lines 이름만 다르지 plot와 똑같다.
        lines(def,
              type = 'o',
              pch = 22,
              col = 'navy',
              lty = 2 # 점선 : 2
             )

        # ghi 데이터 - 3
        lines(ghi,
              type = 'o',
              pch = 24,
              col = 'blue',
              lty = 2 # 점선 : 2
             )

        # 범례 그리기 -> 각 그래프의 이름? 뭐야?? --> 위치 (어디 그릴꺼야??)-> x축 위치와 y축 위치를 알아야함. 
        legend(4, 400,
               c('야구장', '축구장','해변가'),
               # fill = c('red','blue','navy') <- 이렇게 해도되나
               col = c('red','blue','navy'),
               pch = c(21,22,24),
               lty = c(1,2,2),
               cex = 0.8
              )


# R_Class_Note

### Day_06

---
### 점차트

---
### pie 차트

            ratio <- sales / sum(sales) * 100
            label <- paste(week, '\n', ratio, "%") # week + ratio (Vector 두개를 1개로 만드는것은 'paste'뿐)
            # index 순서가 시계 반대 방향으로 돌아간다. 
            # pie 차트는 항상 숫자가 꼭 있는게 좋다. 
            
            # 3D Pie Chart => Package 설치 해야한다.  -> Not installed 에서 plotrix 라고 친다
            # r-plotrix 다운 받는다.
            # R Command 로도 받을수 있다.
            # install.packages('plotrix')

---
### 대선자료 시각화
            read.csv("../Data/election_result_ansi.csv", fileEncoding = 'euc-kr')
            
            # moon + hong + ahn = electionSum 이라는 컬럼을 만들어서
            # election에 컬럼 추가하기 (단, +는 사용하지 말기)
            # apply(df[,-3], 2, sum ) 행 
            # apply(df[,-3], 1, sum ) 열 

            # electionSum이 pop의 몇 퍼센트인지 구해서 electionRatio컬럼 생성
            
### electionRatio가 가장 높은 지역과 가장 낮은 지역구하기
            # arrange 쓰고 싶으면 
            library(dplyr)
            
            # 방법은 두가지가 있다
            # 1) 정렬 
            # 2) subset 

            # csv로 저장하기
            # row.names=F 꼭 써야 한다. 
            
### 광역시별 투표율을 3D Pie Chart로 표현하기
          
          {
                par(family = "AppleGothic")

                # Library 불러와야함  --> 3D Pie Chart
                library(plotrix)

                # 1) 광역시도별 합계를 구한다.
                elect_sum <- aggregate(pop ~ 광역시도, election, sum)
                #head(elect_sum)

                # 2) 합계별 내림차순 정렬
                elec_sum_order <- arrange(elect_sum, desc(elect_sum$pop))

                # 3) 3D Pie Chart 그리기 
                # ratio 구하기
                e_ratio <- round(elec_sum_order$pop / sum(elec_sum_order$pop) * 100,2)

                # Label 구하기
                label <- paste(elec_sum_order$광역시도, "\n", e_ratio, "%")

                # 3D Pie 그리기
                pie3D(elec_sum_order$pop,
                      main = '광역시도별 투표율' ,
                      labels = label, # index적혀 있는것들 

                      labelcex = 0.6, # text size
                      radius = 0.9 # 반지름을 좀 줄이거나 키울때
                   )
            }
            # pie chart의 필요한 명령어 -> help(pie3D)
            
            ****
            ### 문 후보의 광역시도별 득표율을 3D Pie Chart로 표현하기
            par(family = "AppleGothic")

            # 1) 광역시도별 합계를 구한다.
            elect_sum_moon <- aggregate(moon ~ 광역시도, election, sum)
            #head(elect_sum_moon)

            # 2) 합계별 내림차순 정렬
            elec_sum_order_moon <- arrange(elect_sum_moon, desc(elect_sum_moon$moon))
            #head(elec_sum_order_moon)

            # ratio 구하기
            e_moon_ratio <- round(elec_sum_order_moon$moon / sum(elec_sum_order_moon$moon) * 100,1)

            # Label 구하기
            moon_label <- paste(elec_sum_order_moon$광역시도,"\n",ifelse(e_moon_ratio>=3,paste(e_moon_ratio,"%"),""))

            # 3D Pie 그리기
            pie3D(elec_sum_order_moon$moon,
                  main = 'moon후보의 광역시도별 투표율' ,
                  labels = moon_label, # index적혀 있는것들 

                  labelcex = 0.6, # text size
                  radius = 0.9 # 반지름을 좀 줄이거나 키울때
                  
               )

---
### 

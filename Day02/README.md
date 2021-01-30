# R_Class_Note

### Day_02
---

### Vector
            - # iris에서 Species별로 분류하여 각 품종의 Sepal.Length의 평균구하기
            # 벡터 자료의 일부 변경 /// 앞에 쓰는것들은 대부분 데이터 이다. ex) replace(x, )
            # seq(초기값, 최종값, 증가치)
            {
            # c(), :, seq()
            # 반복
            rep(1, 100)
            rep(1:3, 10)
            rep(c(1,5,6), 10)
            }
            
--- 
### 벡터 자료 처리
            - 합집합 , 교집합, 차집합 
            벡터 자료 정렬
            # 중복안되는 난수 뽑는것.
            # sampling 
            - 오름차순, 내림차순
            {
            #iris의 Sepal.Length와 Petal.Length의 교집합 구하기
            x <- iris$Sepal.Length
            y <- iris$Petal.Length
            intersect(x, y)
            }
            #갯수 구하기 
            length(intersect(x, y))
            # 벡터에 이름 주기
                names(var) <- c("유비",'장비', "초선")
            
---
### 문자열 벡터
            name <- c("Apple", "Computer", "Samsung", "Communication")

            # name에서 Co를 가지고 있는 단어의 번지수
            grep("Co", name)
            # name에서 Co를 가지고 있는 단어 출력
            name[c(2,4)]
            name[grep("Co", name)]
            # name에서 om을 가지고 있는 단어의 번지수

            # 10번지 ~ 전체 data중 끝에서 5번째 까지 알고 싶어?
            a[10: (length(a)- 5) ]
            
            # 1번지 빼고
            a[-1]
            # 2번과 4번 삭제
            a[-c(2,4)]
            # 2번과 5~10번 삭제
            a[-c(2,5:10)]
            # 홀수번지 data의 합계 구하기
            sum(a[seq(1,length(a),2)])
            
            #iris의 데이터중 10의 배수의 row만 출력하기
            #2차원은 항상 마지막에 , 가 있다.
            iris[seq(10, nrow(iris),10),]
            
            # 중앙값과 평균!
            
            # 벡터 계산 - > length먼저 체크를 꼭해야한다 -> 갯수가 같냐?

            # \n : 한줄 띄우기, \t : Tab 간격 만큼 띄기
---
## 행렬(Martrix)
- 2차원 데이터를 저장하는 자료형 
- 데이터의 형태가 모두 일치되어야 구성

            # 벡터로 행렬 만들기
            # Data의 추가 : rbind(row bind)
            # column의 추가 : cbind(column bind)
            
            # iris의 1 ~ 5번 데이터 추출하기
            irisHead <- head(iris, 5)
            irisHead
            # 추출한 데이터의 row에 1,1,1,1,setosa 추가하기
            irisHead <- rbind(irisHead, c(1,1,1,1,"setosa"))
            irisHead
            # 추출한 데이터의 abc라는 컬럼과 2,2,2,2,2,2의 데이터 추가하기 
            #-------------
            #abc <- rep(2,6)
            #irisHead <- cbind(irisHead, abc)
            #-------------
            # mat1D와 mat2D를 하나의 Databset으로 만들기


---
# 데이터 프레임
: 다양한 자료형으로 구성된 2차원 형태의 데이터 구조


            -# 벡터로 데이터프레임 만들기
            
            # fruit에서 번호를 제외한 모든 내용 보기
            
            # fruit에서 2,4번 행을 제외한 상품명, 금액, 재고량만 출력

            # 금액 * 재고량 계산후 재고금액 이라는 컬럼을 생성하여 
            # fruit에 붙이기

--- 
# 외부 File 불러오기
            #절대경로 /user/R/Note/
            #상대경로 
            # txt file 불러오기
            #read.table("../Data/emp.txt", fileEncoding = "euc-kr")
        
        
## Level을 보는게 상당히 중요하다. ‘ x ‘ 어떤 데이터가 들어가있는지 봐야함

# League_Of_Legend_Data_Analysis<br/>
![image](https://github.com/user-attachments/assets/e94ee626-cd38-4552-a98b-f7f02e8b65c3)

## 서론 
> - 최장기간 PC방 점유율 1위••• 323주 연속 1위 달성
>주 평균 플레이 시간 ‘1692만 시간’••• 10대男 비중 70%<br/><br/>
>▶주 평균 롤 플레이 타임 약 ‘1692만 시간’
>LoL은 10월 첫째 주 기준, 323주 연속 PC방 점유율 1위에 오르며 매주 자체 기록을 경신 중이다.
>2023년 9월부터 2024년 8월까지 한국에서 LoL을 즐긴 플레이어의 과반수는 10대와 20대 남성이다.
>통계청 장래인구추계 기준, 10대 남성의 약 70%가 LoL을 즐기는 것으로 나타났다.
>라이엇 게임즈는 이용 시간 관련 세부 지표도 공개했다.
>2024년 기준 전체 한국 플레이어의 주간 평균 LoL 플레이 타임은 약 1692만 시간이다. 이중 약 절반이 랭크 게임 플레이 타임에 해당한다.<br/>
>출처: 게임&동향 기사<br/><br/>

리그 오브 레전드 흔히들 롤이라고 부르는 게임은 거의 10년이라는 세월동안 한국 온라인 게임 1위를 지키고 있을 정도로 매우 인기있는 게임이다. <br/>
그렇다면 왜 이렇게 인기가 있는 걸까?<br/><br/>
* 롤이란<br/>
![image](https://github.com/user-attachments/assets/3a426db3-fb9a-4b59-ac55-46bd92dc8821)<br/><br/>
위 이미지는 소환사의 협곡으로 5명의 플레이어가 게임을 하는 무대로 기본적으로 5대5 팀게임으로 진행이 된다는 특징이 있다. 게임의 최종적 목표는 양쪽 끝에 있는 넥서스라고 하는 본진을 터뜨리는 것을 목표하고 있다. 이를 위해서 넥서스에서 나오는 미니언이라는 존재들과 상대를 죽임으로써 나오는 돈으로 아이템을 사서 강해지는 방식으로 게임을 풀어나가면 된다. 기본적으로 탑 ,미드 ,바텀 ,정글  4포지션으로 나뉘며 바텀에 원딜과 서폿이 할당됨에 따라 5명이 모두 게임에 할당된다.<br/><br/>

* 롤이 왜 재밌을까?<br/>
![image](https://github.com/user-attachments/assets/50cf2311-21a7-461b-bf00-e95de43db753)
> 2022 LCK 스프링 PO 2R 5세트에서 10,600골드 차이를 뒤집히며 역전패 당한 DWG KIA<br/>

롤의 묘미라고 하면 많다. 혼자 게임을 박살내버리서 게임을 캐리시킨다든가 위 사진처럼 제아무리 불리한 상황에서 역전을 하는 상황등등 정말 많은데 한단어로 압축을 하자면 변수가 무궁무진하다는 점을 크게 꼽을 수 있을 것 같다. 엔딩을 보면 끝인 콘솔겜이나 매일매일 하는 행동이 반복돼는 rpg과 달리 매순간 매순간 자신의 선택에 따라 다른 상황이 나오는 것이 롤이다. 그 변수를 잘 이용하여 승리를 거뭐쥐었을때의 도파민은 이루맗핳수 없을 정도로 많이 나온다.<br/><br/>

* 변수창출의 라인 미드
> 2024.11.3 기준<br/>
> 롤 프로게이머 연봉<br/> 
> 1위: 페이커<br/>
> 2위: 바이퍼<br/>
> 3위: 쵸비<br/>
> 4위: 제카<br/>
> 5위: 쇼메이커<br/>

2위 원딜인 바이퍼를 제외하고는 전부다 미드라이너들이 연봉이 제일 높다. 이렇듯 미드라이너는 롤에서의 팀의 허리라는 말이 나올정도로 중요하고 변수덩어리인 라인이다.<br/><br/>

그렇다면 잘하는 미드라이너가 되기 위해서는 무슨 요소들이 필요할까?

## 본론 

### 목표: 30명의 솔랭 데이터를 가공하고 모델을 학습시켜 승패를 가장 잘 예측하는 모델 만들기<br/>

#### 데이터 전처리 <br/>

30명의 솔랭 데이터를 가져와서 데이터 전처리를 해볼 예정이다.

* 예외처리를 하고 미드라이너 매치를 추출하는 과정<br/><br/>

龙宫公主#0904_customData.json<br/>
<pre>
<code>
{"killAt14":4,"deathAt14":1,"assistAt14":2,...............}
</code>
</pre>
<br/>
龙宫公主#0904_matchData.json<br/>
<pre>
<code>
{"metadata":{"dataVersion":"2","matchId":"KR_7250780365","participants":["VNtg66LuBnvZ2wYt-wY5Y2cN4EZ7-Uz8AHgX_Pt5Fp9wQeBvS8mD_Aq-uY3rYoBW60KajTZhZTMUjA","EPVscaMKw3dq5WvzM4SaXGFzohjXWMUbJ9A2WAM7wI_NVLNZM9sxXg2dpq11m_6UMNv3M8w0h0Y15Q",.........}
</code>
</pre>
<br/>
龙宫公主#0904_timelineData.json<br/>
<pre>
<code>
{"metadata":{"dataVersion":"2","matchId":"KR_7250780365","participants":["VNtg66LuBnvZ2wYt-wY5Y2cN4EZ7-Uz8AHgX_Pt5Fp9wQeBvS8mD_Aq-uY3rYoBW60KajTZhZTMUjA",...............}
</code>
</pre>
<br/>
龙宫公主#0904이라는 플레이어가 한 게임에서 모든 요소들이 저 세계의 파일에 담겨있다. 그중 미드라이너에 해당하는 것들만을 솎아 낼 것인데 이 과정을 나머지 29명의 플레이어의 플레이 로그에 반복적용해서 30명 전원의 미드라이너들의 요소를 추출 하는 것이 첫 단계이다.<br/><br/>

* 라인전 이전과 이후 구분<br/><br/>
롤에는 라인전 페이즈와 한타 페이즈라는 것이 존재한다. 보통 15분전에 자신의 지정된 라인에서 상대편과 게임을 진행하는 단계를 라인전 페이즈라 하며 15분이후에 5대 5 단체 싸움을 하는 단계를 한타 페이즈라 부릅니다. 둘다 중요한 요소들이지만 어느 단계의 중요도가 높은지를 파악하기 위해서 라인전과 이전과 이후로 데이터를 나누겠다.


<pre>
추출 결과
<code>
{
"gamerName": "龙宫公主",
        "numValidGame": 58,
        "match": [
            {
                "riotIdGameName": "龙宫公主",
                "matchId": "KR_7250780365",
                "gameCreation": 1725030458253,
                "gameDuration": 1861.272415313,
                "participantId": 3,
                "opponentpId": 8,
                "teamId": 100,
                "teamPosition": "MIDDLE",
                "win": true,
                "kda": 5,
                "kills": 10,
                "deaths": 5,
                "assists": 15,
                "solokills": 1,
                "solodeaths": 1,
                "totalDamageDealtToChampions": 28838,.........}
</code>
</pre><br/><br/>

* 특정 미드라이너와 상대방 미드라이너의 데이터를 토대로 격차 및 비율 데이터 산출<br/>
롤에서 상대 미드보다 게임에 영향력을 끼치고 있는지는 정말 중요하다. 미드라이너는 상대편 미드라이너보다 앞서가고 있다는 것은 게임이 종합적으로 앞서가고 있다는 지표와도 같기 때문이다. 그렇기 때문에 둘사이의 차이를 데이터로 산춣하려한다.

<pre>
추출 결과
<code>
 {
        "GamaName": "龙宫公主",
        "matches": [
            {
                "matchId": "KR_7250780365",
                "gameCreation": 1725030458253,
                "gameDuration": 1861.272415313,
                "riotIdGameName": "龙宫公主",
                "participantId": 3,
                "opponentRiotIdGameName": "n8jj",
                "opponentParticipantId": 8,
                "targetTeamId": 100,
                "targetWin": true,
                "at14": {
                    "gameDuration": 840.239,
                    "combat": {
                        "killsRatio": 0.4,
                        "deathsRatio": 0.5,
                        "assistsRatio": 0.25,
                        "solokillsRatio": 0.0,
                        "solodeathsRatio": 0.0,
                        "dpm": 351.6142430903588,
                        "dtpm": 431.37726289781835,
                        "targetKDA": {
                            "kills": 2,
                            "deaths": 1,
                            "assists": 1
                        },
                        "targetSoloKDA": {
                            "solokills": 0,
                            "solodeaths": 0
                        },
                        "opponentKDA": {
                            "kills": 3,
                            "deaths": 1,
                            "assists": 3
                        },
                        "opponentSoloKDA": {
                            "solokills": 1,
                            "solodeaths": 1
                        }.........}
</code>
</pre><br/><br/>

 * 간단한 테이블 형태로 데이터를 가공

<pre>
추출 결과
<code>
 {
"gamerName": "龙宫公主",
        "opponentGamerName": "n8jj",
        "matchID": "KR_7250671169",
        "gameCreation": 1725030458253,
        "gameDuration": 1861.272415313,
        "at14gameDuration": 840.239,
        "targetTeamId": 100,
        "targetWin": true,
        "at14killsRatio": 0.4,
        "at14deathsRatio": 0.5,
        "at14assistsRatio": 0.25,
        "at14solokillsRatio": 0.0,
        "at14solodeathsRatio": 0.0,
        "at14dpm": 351.6142430903588,
        "at14dtpm": 431.37726289781835,
        "at14cspm": 7.640683186569535,.........}
</code>
</pre><br/><br/>

#### 모델 만들기 <br/>

* 모델 선택
현재 예측하는 값이 승리와 패배로 이진분류에 해당한다. 모델중 이진분류에 가장 적합한 모델은 sigmoid 함수를 사용하는 logistic regression이 가장 적합하다 생각해서 선택했습니다.

* 원소 선택
  * 한타 페이즈가 5:5 싸움이다 보니 1:1인 라인전 과정보다 변수가 많이 생기기 때문에 af14의 원소들을 선택햇다.
    
    
   







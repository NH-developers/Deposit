# Deposit
예치금관리 API
## 1 소개
### 1.1 예치금관리
편리하고 정확한 자금처리 및 이용자별 예치금 관리가 가능한 서비스입니다.
#### 1.1.1 예치금관리 NH API 목록
| 전문명 | API |
|:---:|:---:|
| 예치금 가상계좌 발급 |	OpenVirtualAccount |
| 가상계좌 입금내역 조회 납부 |	VirtualAccountReceivedListInquiry |	
| 결제대금 지급계좌 이체요청 | PaymentPayoutAccountTransfe |	
| 결제대금 지급계좌 이체요청 결과확인 |	CheckPaymentPayoutAccountTransfer |	
| 결제대금 지급요청 |	PaymentPayoutReceivedTransfer |	
| 결제대금 지급요청 결과확인 | CheckPaymentPayoutReceivedTransfer |	
| 예치금 잔액조회 | DepositAmountAccountBalancesInquiry |

## 2 resource url
#### 2.1 예치금 가상계좌 발급
https://developers.nonghyup.com/OpenVirtualAccount.nh
#### 2.2 가상계좌 입금내역 조회
https://developers.nonghyup.com/VirtualAccountReceivedListInquiry.nh
#### 2.3 결제대금 지급계좌 이체요청
https://developers.nonghyup.com/PaymentPayoutAccountTransfer.nh
#### 2.4 결제대금 지급계좌 이체요청 결과확인
https://developers.nonghyup.com/CheckPaymentPayoutAccountTransfer.nh
#### 2.5 결제대금 지급요청
https://developers.nonghyup.com/PaymentPayoutReceivedTransfer.nh
#### 2.6 결제대금 지급요청 결과확인
https://developers.nonghyup.com/CheckPaymentPayoutReceivedTransfer.nh
#### 2.7 예치금 잔액조회
https://developers.nonghyup.com/DepositAmountAccountBalancesInquiry.nh

## 3 example
### 3.1.1 예치금 가상계좌 발급 Request example
```json
{                                                               
    "Header" : { 
       "ApiNm" : "OpenVirtualAccount",          
       "Tsymd" : "20221201",                       
       "Trtm" : "133259",                          
       "Iscd" : "000329",                           
       "FintechApsno" : "003",                             
       "ApiSvcCd" : "TEST_API_G",                      
       "IsTuno" : "20221201133259000001",
       "AccessToken" : "10b74dd7f5f0f521ecdc7ade82f793bdfc119c3635d2e5303ae6aba0c93d4246"
     },                                                         
     "Dpnm" : "홍길동",                    
     "MnrcClamt" : "",                   
     "MnrcClsnDt" : ""                   
}
```
### 3.1.2 예치금 가상계좌 발급 Request Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	 
| Dpnm |	예금주명 |	필드 |	50 |	필수 |	- MAX: 한글 6자리  
- 예금주명 앞에 기관 약어명(3자) 자동추가 (총 9자리)  
- 테스트에서는 예금주명 |
| MnrcClamt |		입금마감금액 |	필드 |	15 |	선택 |	테스트에서는 미입력 |
| MnrcClsnDt |	입금마감일시 |	필드 |	14 |	선택 |	테스트에서는 미입력 |
### 3.1.3 예치금 가상계좌 발급 Response example
```json
{ 
    "Header":{
       "ApiNm" : "OpenVirtualAccount",
       "Tsymd" : "20221201“,
       "Trtm" : "133259“,
       "Iscd" : "000329",
       "FintechApsno" : "003",
       "ApiSvcCd" : "TEST_API_G",
       "IsTuno" : "20221201133259000001",
       "Rpcd" : "00000",
       "Rsms" : "정상 처리 되었습니다."
    }, 
    "Dpnm" : "홍길동",
    "VractPrtn" : "1",
    "MnrcClamt" : "50000",
    "MnrcClsnDt" : "20121122173000",
    "DayMnrcLmamt" : "44",
    "Vran" : "79000000000001",
    "IsncRmngCnt" : "180",
    "IsncFncnt" : "20"
}
```
### 3.1.4 예치금 가상계좌 발급 Response Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	 
| Dpnm |	예금주명 |	필드 |	50 |	필수 |	테스트에서는 예금주명 |
| VractPrtn |	가상계좌유형 |	필드 |	1 |	필수 |	테스트에서는 "1" |
| MnrcClamt |		입금마감금액 |	필드 |	15 |	필수 |
| MnrcClsnDt |	입금마감일시 |	필드 |	14 |	필수 |
| DayMnrcLmamt |	일입금한도금액 |	필드 |	15 |	필수 |
| Vran |	가상계좌번호 |	필드 |	20 |	필수 |
| IsncRmngCnt |	발급잔여건수 |	필드 |	10 |	필수 |	 
| IsncFncnt |	발급완료건수 |	필드 |	10 |	필수 |	

### 3.2.1 가상계좌 입금내역 조회 Request example
```json
{
    "Header" : {
       "ApiNm" : "VirtualAccountReceivedListInquiry", 
       "Tsymd" : "20180320",
       "Trtm" : "100030",
       "Iscd" : "000001",
       "FintechApsno" : "011",
       "ApiSvcCd" : "10B_001_00",
       "IsTuno" : "20180320100032000029",
       "AccessToken": "10b74dd7f5f0f521ecdc7ade82f793bdfc119c3635d2e5303ae6aba0c93d4246"
    },
   "Insymd" : "20180315",
   "Ineymd" : "20180315",
   "Vran" : "",
   "Lnsq" : "",
   "PageNo" : ""
}
```
### 3.2.2 가상계좌 입금내역 조회 Request Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	 
| Insymd |	조회시작일자 |	필드 |	8 |	필수 |	- 거래일자 기준/현재일자 이후 조회불가  
- 유효 타입: yyyyMMdd |
| Ineymd |	조회종료일자 |	필드 |	8 |	필수 |	- 거래일자 기준/현재일자 이후 조회불가  
- 유효 타입: yyyyMMdd  
- 조회범위 1일 이내 |
| Vran |	가상계좌번호 |	필드 |	20 |	선택 |	가상계좌 입력 시 해당 가상계좌의 내역 조회 |
| Lnsq |	정렬순서 |	필드 |	10 |	선택 |	ASC:오름차순, DESC:내림차순, default:DESC |
| PageNo |	페이지번호 |	필드 |	4 |	선택 |	Default : 1 |
### 3.2.3 가상계좌 입금내역 조회 Response example
```json
{
   "Header" : {
   	   "ApiNm" : "VirtualAccountReceivedListInquiry",
   	   "Tsymd" : "20180320",
       "Trtm" : "100030",
       "Iscd" : "000001",
       "FintechApsno" : "011",
       "ApiSvcCd" : "10B_001_00",
       "IsTuno" : "20180320100032000029",
       "Rpcd" : "00000",
       "Rsms" : "정상 처리 되었습니다."
    },
   "TotCnt" : "1",
   "IqtCnt" : "1",
   "PageNo" : "1",
    "Rec" : 
    [ {
           "Vran" : "79014238679123" 
           "MnrcStts" : "0",
           "Sqno" : "180315000001",
           "MnrcDt" : "20180315",
           "Mntmd" : "132810",
           "MnrcAmt" : "100"
    } ]
}
```
### 3.2.4 가상계좌 입금내역 조회 Response Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	 
| TotCnt |	총건수 |	필드 |	10 |	필수 |	 
| Iqtcnt |	조회총건수 |	필드 |	10 |	필수 |	 
| PageNo |	페이지번호 |	필드 |	4 |	필수 |
| REC |	거래내역목록 | 반복부 | | 필수 | 페이지당 20 건 |
| Sqno |	순번 |	필드 |	12 |	필수 |	 	 
| Vran |	가상계좌번호 |	필드 |	20 |	필수 |
| MnrcStts |	입금상태 |	필드 |	1 |	필수 |	1:정상, 0:처리중, 9:오류 |
| MnrcDt |	입금일자 |	필드 |	8 |	필수 |	YYYYMMDD |
| Mntmd |	입금시각 |	필드 |	6 |	필수 |	HHMISS |
| MnChkTm |	입금확인시각 |	필드 |	6 |	필수 |	 
| MnrcAmt |	입금금액 |	필드 |	15 |	필수 |	

### 3.3.1 결제대금 지급계좌 이체요청 Request example
```json
{
    "Header" : {
       "ApiNm" : "PaymentPayoutAccountTransfer",
       "Tsymd" : "20180320",
       "Trtm" : "100030",
       "Iscd" : "000001",
       "FintechApsno" : "011",
       "ApiSvcCd" : "10B_002_00",
       "IsTuno" : "20180320100032000008",
       "AccessToken": "10b74dd7f5f0f521ecdc7ade82f793bdfc119c3635d2e5303ae6aba0c93d4246"
    },
   "Tram" : "100",
   "Acno" : "06001019975"
}
```
### 3.3.2 결제대금 지급계좌 이체요청 Request Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	
| Tram |	거래금액 |	필드 |	15 |	필수 |	 
| Acno |	계좌번호 |	필드 |	20 |	필수 |	기관 약정계좌 (농협 모계좌) |
### 3.3.3 결제대금 지급계좌 이체요청 Response example
```json
{
  "Header" : {
       "ApiNm" : "PaymentPayoutAccountTransfer",
       "Tsymd" : "20180320",
       "Trtm" : "100030",
       "Iscd" : "000001",
       "FintechApsno" : "011",
       "ApiSvcCd" : "10B_002_00",
       "IsTuno" : "20180320100032000008",
       "Rpcd" : "00000",
       "Rsms" : "정상 처리 되었습니다."
    },
   	"Rgno" : "NO_1803200000042",
    "Tram" : "100"
}
```
### 3.3.4 결제대금 지급계좌 이체요청 Response Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	
| Rgno |	등록번호 |	필드 |	20 |	필수 |	결제대금 지급요청 대상 등록번호 |
| Tram |	거래금액 |	필드 |	15 |	필수 |	

### 3.4.1 결제대금 지급계좌 이체요청 결과확인 Request example
```json
{
    "Header" : {
       "ApiNm" : "CheckPaymentPayoutAccountTransfer",
       "Tsymd" : "20180320",
       "Trtm" : "100030",
       "Iscd" : "000001",
       "FintechApsno" : "011",
       "ApiSvcCd" : "10B_002_00",
       "IsTuno" : "20180320100032000010",
       "AccessToken": "10b74dd7f5f0f521ecdc7ade82f793bdfc119c3635d2e5303ae6aba0c93d4246"
    },
   "OrtrYmd" : "20180320",
   "OrtrIsTuno" : "20180320100032000008",
   "Tram" : "100"
}
```
### 3.4.2 결제대금 지급계좌 이체요청 결과확인 Request Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	
| OrtrYmd |	원거래일자 |	필드 |	8|	필수 |	원 거래의 API 실행일자 |
| OrtrIsTuno |	원거래기관거래고유번호 |	필드 |	20 |	필수 |	원 거래의 기관거래고유번호 |
| Tram |	거래금액 |	필드 |	15 |	필수 |	
### 3.4.3 결제대금 지급계좌 이체요청 결과확인 Response example
```json
{
   "Header" : {
       "ApiNm" : "CheckPaymentPayoutAccountTransfer",
       "Tsymd" : "20180320",
       "Trtm" : "100030",
       "Iscd" : "000001",
       "FintechApsno" : "011",
       "ApiSvcCd" : "10B_002_00",
       "IsTuno" : "20180320100032000010",
       "Rpcd" : "00000",
       "Rsms" : "정상 처리 되었습니다."
    },
   "Rgno" : "NO_1803200000042",
   "Pcrs" : "00000",
   "Prtm" : "104635"
}
```
### 3.4.4 결제대금 지급계좌 이체요청 결과확인 Response Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	
| Rgno |	등록번호 |	필드 |	20 |	필수 |
| Pcrs |	처리결과 |	필드 |	5 |	필수 |	원거래에 대한 처리결과 ※공통부 Rpcd=‘00000’경우만 참조 처리 결과 코드 |
| Prtm |	처리시각 |	필드 |	6 |	필수 |

### 3.5.1 결제대금 지급요청 Request example
```json
{
    "Header" :  {
       "ApiNm" : "PaymentPayoutReceivedTransfer",
       "Tsymd" : "20180320",
       "Trtm" : "100030",
       "Iscd" : "000001",
       "FintechApsno" : "011",
       "ApiSvcCd" : "10B_003_00",
       "IsTuno" : "20180320100032000013",
       "AccessToken": "10b74dd7f5f0f521ecdc7ade82f793bdfc119c3635d2e5303ae6aba0c93d4246"
    },
   "Rgno" : "NO_1803200000044",
   "Tram" : "100",
   "Bncd" : "011",
   "Acno" : "3170003417501",
   "DractOtlt" : "출금계좌인자내용",
   "MractOtlt" : "입금계좌인자내용"
}
```
### 3.5.2 결제대금 지급요청 Request Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	
| Rgno |	등록번호 |	필드 |	20 |	필수 |	결제대금 지급요청 대상 등록번호 |
| Tram |	거래금액 |	필드 |	15 |	필수 |	 
| Bncd |	은행코드 |	필드 |	3 |	필수 |	 
| Acno |	계좌번호 |	필드 |	20 |	필수 |	 
| DractOtlt |	출금계좌인자내용 |	필드 |	25 |	필수 |	출금계좌(약정계좌) 통장인자내용 or 고객명 |
| MractOtlt |	입금계좌인자내용 |	필드 |	25 |	필수 |	입금고객계좌 통장인자내용 |
### 3.5.3 결제대금 지급요청 Response example
```json
{
    "Header" : {
       "ApiNm" : "PaymentPayoutReceivedTransfer",
       "Tsymd" : "20180320",
       "Trtm" : "100030",
       "Iscd" : "000001",
       "FintechApsno" : "011",
       "ApiSvcCd" : "10B_003_00",
       "IsTuno" : "20180320100032000013",
       "Rpcd" : "00000",
       "Rsms" : "정상 처리 되었습니다."
    }
}
```
### 3.5.4 결제대금 지급요청 Response Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	

### 3.6.1 결제대금 지급요청 결과확인 Request example
```json
Request example
{
    "Header" : {
       "ApiNm" : "CheckPaymentPayoutReceivedTransfer",
       "Tsymd" : "20180320",
       "Trtm" : "100030",
       "Iscd" : "000001",
       "FintechApsno" : "011",
       "ApiSvcCd" : "10B_003_00",
       "IsTuno" : "20180320100032000027",
       "AccessToken": "10b74dd7f5f0f521ecdc7ade82f793bdfc119c3635d2e5303ae6aba0c93d4246"
    },
   "OrtrYmd" : "20180320",
   "OrtrIsTuno" : "20180320100032000013",
   "Rgno" : "NO_1803200000044",
   "Tram" : "100",
   "Bncd" : "011",
   "Acno" : "3170003417501"
}
```
### 3.6.2 결제대금 지급요청 결과확인 Request Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	
| OrtrYmd |	원거래일자 |	필드 |	8|	필수 |	결제대금 지급요청 일자 |
| OrtrIsTuno |	원거래기관거래고유번호 |	필드 |	20 |	필수 |	결제대금 지급요청 기관거래 고유번호 |
| Rgno |	등록번호 |	필드 |	29 |	필수 |	결제대금 지급요청 대상 등록번호 |
| Tram |	거래금액 |	필드 |	15 |	필수 |	 
| Bncd |	은행코드 |	필드 |	3 |	필수 |	 
| Acno |	계좌번호 |	필드 |	20 |	필수 |	 
### 3.6.3 결제대금 지급요청 결과확인 Response example
```json
{
    "Header" : {
       "ApiNm" : "CheckPaymentPayoutReceivedTransfer",
       "Tsymd" : "20180320",
       "Trtm" : "100030",
       "Iscd" : "000001",
       "FintechApsno" : "011",
       "ApiSvcCd" : "10B_003_00",
       "IsTuno" : "20180320100032000027",
       "Rpcd" : "00000",
       "Rsms" : "정상 처리 되었습니다."
    },
    "Pcrs" : "00000",
    "Prtm" : "141653"
}
```
### 3.6.4 결제대금 지급요청 결과확인 Response Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	
| Pcrs |	처리결과 |	필드 |	5 |	필수 |	원거래에 대한 처리결과 ※공통부 Rpcd=‘00000’경우만 참조 처리 결과 코드 |
| Prtm |	처리시각 |	필드 |	6 |	필수 |

### 3.7.1 예치금 잔액조회 Request example
```json
{
    "Header" : {
       "ApiNm" : "DepositAmountAccountBalancesInquiry",
       "Tsymd" : "20221201",
       "Trtm" : "100030",
       "Iscd" : "000001",
       "FintechApsno" : "011",
       "ApiSvcCd" : "10B_004_00",
       "IsTuno" : "2022101100032000031",
       "AccessToken": "10b74dd7f5f0f521ecdc7ade82f793bdfc119c3635d2e5303ae6aba0c93d4246"
    }
} 	
```
### 3.7.2 예치금 잔액조회 Request Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	  	
### 3.7.3 예치금 잔액조회 Response example
```json
{
    "Header" : {
       "ApiNm" : "DepositAmountAccountBalancesInquiry",
       "Tsymd" : "20221201",
       "Trtm" : "100030",
       "Iscd" : "000001",
       "FintechApsno" : "011",
       "ApiSvcCd" : "10B_004_00",
       "IsTuno" : "20221201100032000031",
       "Rpcd" : "00000",
       "Rsms" : "정상 처리 되었습니다."
    },
   "DepsBal" : "100000000"
}
```
### 3.7.4 예치금 잔액조회 Response Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||	  	
| DepsBal |	예치잔액 |	필드 |	15 |	필수 |

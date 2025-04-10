# Store API

## 상품 카테고리 목록 조회
 
- 호출 URL : https://adm.snapplay.io/adm/main/store/cats?app_id=<YOUR_APP_ID>

```json
{
    "ret_cd": 0,
    "cat": [
        {
            "seq_no": 1,
            "cat_id": 1003,
            "cat_nm": "편의점",
            "img_url": "https://d1djcwwrtg2512.cloudfront.net/store/1171"
        },
        {
            "seq_no": 2,
            "cat_id": 1004,
            "cat_nm": "상품권",
            "img_url": "https://d1djcwwrtg2512.cloudfront.net/no_image.jpg"
        }
    ]
}
```

## 특정 카테고리의 상품목록 조회

- 호출 URL : https://adm.snapplay.io/adm/main/store/prds?app_id=<YOUR_APP_ID>&cat_id=<카테고리 ID>

```json
{
    "ret_cd": 0,
    "prd": [
        {
            "seq_no": 1,
            "swap_nm": "CU",
            "img_url": "https://d1djcwwrtg2512.cloudfront.net/store/1168",
            "prd_desc": "전국 CU에서 상품교환이 가능합니다. \n유효기간 이후에는 사용이 불가합니다.\n각종 할인적용 및 포인트 적립 불가 합니다.\n자체 행사상품에는 제외 됩니다.\n1+1/2+1등 행사상품 +1적용은 되지 않습니다.",
            "tr_type": "G",
            "prd_nm": "트윅스쿠키",
            "prd_id": 1001,
            "sale_price": 1000
        },
        {
            "seq_no": 2,
            "swap_nm": "투썸플레이스",
            "img_url": "https://img.giftting.co.kr/dev/goods/G00000028764/G00000028764_250.jpg",
            "prd_desc": "테스트",
            "tr_type": "G",
            "prd_nm": "아메리카노 (R)",
            "prd_id": 1002,
            "sale_price": 4100
        }
    ]
}
```

## 카테고리 목록과 상품목록을 한번에 조회

- 호출 URL : https://adm.snapplay.io/adm/main/store/catprds?app_id=<YOUR_APP_ID>
- cat 배열에 카테고리 목록이 담겨 있으며 prd_ids 는 해당 카테고리에 속한 상품의 prd_id 의 목록이 담겨있다.
- 상품 정보는 prd 배열에서 prd_id 로 매칭하여 확인할 수 있다.
- prd_ids 에 존재하는 prd_id 의 상품 정보가 prd 배열에 없을 수도 있다. 실제 판매 중인 상품 목록만 내려준다.
  
```json
{
    "ret_cd": 0,
    "prd": [
        {
            "swap_nm": "CU",
            "img_url": "https://d1djcwwrtg2512.cloudfront.net/store/1168",
            "prd_desc": "전국 CU에서 상품교환이 가능합니다. \n유효기간 이후에는 사용이 불가합니다.\n각종 할인적용 및 포인트 적립 불가 합니다.\n자체 행사상품에는 제외 됩니다.\n1+1/2+1등 행사상품 +1적용은 되지 않습니다.",
            "tr_type": "G",
            "prd_nm": "트윅스쿠키",
            "prd_id": 1001,
            "sale_price": 1000
        },
        {
            "swap_nm": "투썸플레이스",
            "img_url": "https://img.giftting.co.kr/dev/goods/G00000028764/G00000028764_250.jpg",
            "prd_desc": "테스트",
            "tr_type": "G",
            "prd_nm": "아메리카노 (R)",
            "prd_id": 1002,
            "sale_price": 4100
        }
    ],
    "cat": [
        {
            "seq_no": 1,
            "cat_id": 1003,
            "prd_ids": [
                1001,
                1002
            ],
            "cat_nm": "편의점",
            "img_url": "https://d1djcwwrtg2512.cloudfront.net/store/1171"
        },
        {
            "seq_no": 2,
            "cat_id": 1004,
            "prd_ids": [
                1002
            ],
            "cat_nm": "상품권",
            "img_url": "https://d1djcwwrtg2512.cloudfront.net/no_image.jpg"
        }
    ]
}
```
## 상품 구매
- 호출 URL : https://adm.snapplay.io/adm/main/store/reqpr?app_id=<YOUR_APP_ID>&pub_user_nm=<구매자>&user_info=<전화번호>&user_ip_addr=<구매자 기기 IP 주소>
- 구매 API 는 사용자 단말기에서 직접 호출 할 수 없다. 반드시 매체사의 서버에서 호출해야하며 해당 매체사 서버의 IP 주소는 등록되어 있어야한다. (별도 문의)
- 구매 시 사용자의 잔여 포인트 등의 구매 가능 여부는 매체사에서 확인해야하며 구매 후에는 상품 가격에 해당되는 사용자의 포인트를 차감하도록 구현해야한다. (이에 대한 책임은 매체사에게 있음)
- 구매후 전달되는 pin_no 는 사용자에게 바코드로 표시하여야한다. 바코드 표시 규칙은 아래와 같다.
  - 쿠폰번호가 모두 숫자형인 경우
    - 자릿수가 짝수인 경우 : Code 128C
    - 자릿수가 홀수인 경우 : Code 128
  - 쿠폰번호가 문자형인 경우
    - Code 128

# Store API

호출 URL

https://adm.snapplay.io/adm/main/store/catprds?app_id=<YOUR_APP_ID>

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

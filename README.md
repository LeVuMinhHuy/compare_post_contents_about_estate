### compare_post_contents_about_estate
#### News:
1. Decrease the complexity of compare to O(N) with N is the number of posts
2. Add more features in one attribute. Ex: attr_addr_street can include "hoang hoa tham, nguyen thi minh khai" instead of just "hoang hoa tham".
#### Result:
![Result](https://github.com/LeVuMinhHuy/compare_post_contents_about_estate/blob/minhhuy/result.png)

#### Đánh giá testcases:

1. Testcase: Có đủ thông tin trong cả 2 posts, đúng thứ tự:
``` 
  {
    "id": 100,
    "content": "Em cần nhượng phòng gấpĐịa chỉ: 242Hoàng Hoa Thám,p5, Q. Bình Thạnh. Phòng e ở được từ 2-3 người. Phòng có giá 2tr5, có nhà vệ sinh riêng, nước 50k/người, điện 3,5k/kwh. Sát chợ nên rất nhộn nhịp, ăn uống thoải mái, gần hồ về đêm rất yên tĩnh. Sdt 0944296412 "
  },
  {
    "id": 101,
    "content": "Vì đang kẹt tiền nên em có một căn nhà ở hoàng hoa thám ,p5, quận bình thạnh cần bán gấp. Phòng giá 5 triệu. Gần hồ và chợ nên rất yên tĩnh, nhộn nhịp . Liên hệ: 0944296412 "
  },
```

Cho ra kết quả:

```
hoang hoa tham binh thanh p 5 cho ho nhon nhip yen tinh 
hoang hoa tham binh thanh p 5 cho ho nhon nhip yen tinh 
Two posts: 101 and 100 are identical. 
```

2. Testcase: Có đủ thông tin trong cả 2 posts, đảo thứ tự:
```
  {
    "id": 300,
    "content": "Cho thuê nguyên căn mặt tiền Hai Bà Trưng, Phường Tân Định, Quận 1. ,Diện tích 4x15m nở hậu 6m. Trống suốt, khu vực kinh doanh mọi ngành nghề ,DTSD: 100m2,Giá thuê 45 triệu/tháng. Vị trí gần Trần Quang Khải. ,Liên hệ anh Bình 0906.311.001 -chị Lan 0916.316.839"
  },
  {
    "id": 301,
    "content": "Cần mua nhà ở quận 1, đường hai bà trưng, phường tân định, gần đường Trần Quang Khải"
  },
```
Kết quả:
```
hai ba trung quan 1 tan dinh 
hai ba trung quan 1 tan dinh 
Two posts: 301 and 300 are identical. 
```

3. Testcase: Thiếu chỉ 1 thông tin về tên phường:
```
  {
    "id": 500,
    "content": "Cho thuê nhà mặt tiền 2 căn có hầm đường số 44 Phường 10 quận 6,* DT: 8x20, 1 trệt, 1 hầm, sân thượng, 3 lầu, 4PN, 7WC sạch sẽ thoáng mát,* Vị trí đẹp mặt tiền đường lớn phù hợp kinh doanh mọi ngành nghề, cho thuê văn phòng, ngân hàng, kinh doanh cửa hàng, shop, khách sạn hoặc trung tâm ngoại ngữ ,* Giá thuê: 50tr còn thương lượng,* Ưu tiên khách thiện trí - MTG, TB.,Liên hệ: 0938 558 577"
  },
  {
    "id": 501,
    "content": "Tìm nhà quận 6, nằm trên đường số 44, phường 10. Yêu cầu vị trí đẹp, nhà ở mặt tiền để tiện kinh doanh"
  },
  {
    "id": 502,
    "content": "Tìm nhà quận 6, nằm trên đường số 44. Yêu cầu vị trí đẹp, nhà ở mặt tiền để tiện kinh doanh"
  },
```

Kết quả:

```
so 44 quan 6 phuong 10 
so 44 quan 6 phuong 10 
Two posts: 501 and 500 are identical. 

502: so 44 quan 6 
```

4. Testcase: Không đủ thông tin ở 2 posts về địa chỉ, hoặc không khớp thông tin về yêu cầu khu vực xung quanh...
```

  {
    "id": 700,
    "content": "Cho thuê gấp mặt bằng ở ngã tư Đường Trần Lựu và Trần Đào, P.Bình An , Quận 2 giá 15 triệu /tháng,Gần siêu thị , dân cư đông đúc , giao thông thuận tiện ,an ninh, sạch sẽ . ,Diện tích: 5x20 (m2). ,Kết cấu: hầm, 1 trệt .,Giá thuê: 15 triệu /tháng. ,Mọi chi tiết thuê villa – biệt thự quận 2 vui lòng liên hệ: ,Trần Nam 0968-274-869 ** 0902-971-889 ,Mail: Nambdspro@gmail.com."
  },
  {
    "id": 701,
    "content": "Tìm nhà ở đoạn đường trần lựu giao với trần đào. dân cư đông đúc , giao thông thuận tiện ,an ninh, sạch sẽ"
  },
  {
    "id": 702,
    "content": "Tìm nhà ở đoạn giao của đường trần đào và đường trần lựu. dân cư đông đúc , giao thông thuận tiện ,an ninh, sạch sẽ"
  },
  {
    "id": 703,
    "content": "Tìm nhà ở đoạn giao của đường trần đào và đường trần lựu. quận 2 có dân cư đông đúc , giao thông thuận tiện ,an ninh, sạch sẽ"
  },
  {
    "id": 704,
    "content": "Tìm nhà ở đoạn giao của đường trần đào và đường trần lựu. quận 2 phường bình an, có dân cư đông đúc , giao thông thuận tiện ,an ninh, sạch sẽ"
  },
  {
    "id": 705,
    "content": "Tìm nhà ở đoạn giao của đường trần đào và đường trần lựu. quận 2 phường bình an. khu vực dân cư đông đúc , giao thông thuận tiện ,an ninh, sạch sẽ. Ưu tiên khu vực gần khu dân cư, siêu thị"
  },
  {
    "id": 706,
    "content": "Tìm nhà ở đoạn giao của đường trần đào và đường trần lựu. quận 2 phường bình an, dân cư đông đúc , giao thông thuận tiện ,an ninh, sạch sẽ. Ưu tiên khu vực ngã tư có siêu thị"
  },
```

Kết quả:

```
tran dao tran luu quan 2 binh an nga tu sieu thi an ninh dan cu dong duc giao thong thuan tien sach se 
tran luu an ninh dong duc giao thong thuan tien sach se 
tran dao tran luu an ninh dong duc giao thong thuan tien sach se 
tran dao tran luu quan 2 an ninh dong duc giao thong thuan tien sach se 
tran dao tran luu quan 2 binh an an ninh dong duc giao thong thuan tien sach se 
tran dao tran luu quan 2 binh an khu dan cu sieu thi an ninh dong duc giao thong thuan tien sach se 
tran dao tran luu quan 2 binh an nga tu sieu thi an ninh dong duc giao thong thuan tien sach se 
```

Không có post nào trùng nhau

5. Testcase: Trùng ngẫu nhiên
```
  {
    "id": 800,
    "content": "nhà có 40 phòng cho thuê hien tại con trong 3 phong khu vuc trung tâm gần truong dại hoc bách khoa,qua quân 10 5p,gân chợ....,phòng có máy lanh,máy nong lanh,nôi thất cơ bản..,giá từ: 2tr6 đêns 6tr5,lh: 0917383381,dc: 99 binh thới f11 quân 11 hcm"
  },
  {
    "id": 800,
    "content": "tìm một ngôi nhà ở sao hỏa, khu vực gần hố đen vũ trụ. nhưng lại có chợ và trường đại học"
  }
```

Kết quả:

```
cho truong dai hoc 
cho truong dai hoc 
```


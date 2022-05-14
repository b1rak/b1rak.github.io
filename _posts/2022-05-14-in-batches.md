---
layout: post
title:  "in_batches, find_each, find_in_batches"
categories: 개발
---

# 차이를 표로보기
<table>
  <tr><td>종류</td><td>반환 타입</td><td>특징</td></tr>
  <tr><td>in_batches</td><td>ActiveRecord::Relation</td><td>블록을 넘겨받음으로 추가적인 조건문 설정이나 update_all 같은 처리를 수행할 수 있다.</td></tr>
  <tr><td>find_in_batches</td><td>모델의 Array</td><td>in_batches의 결과를 Array로 변환한 것</td></tr>
  <tr><td>find_each</td><td>모델</td><td>find_in_batches + each</td></tr>
</table>

# 참고
- find_each: [https://railsdoc.com/page/find_each](https://railsdoc.com/page/find_each)
- find_in_batches: [https://railsdoc.com/page/find_in_batches](https://railsdoc.com/page/find_in_batches)
- in_batches [https://railsdoc.com/page/in_batches](https://railsdoc.com/page/in_batches)

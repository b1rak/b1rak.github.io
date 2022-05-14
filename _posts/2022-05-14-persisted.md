---
layout: post
title:  "persisted?"
categories: 개발
---

# persisted?
https://apidock.com/rails/v6.1.3.1/ActiveRecord/Persistence/persisted%3F

DB에 저장된 데이터라면 true 를 반환된다.
저장되었던 데이터라도 파괴(삭제)되었다면 false 를 반환한다.

# new_record? 와의 차이
new_record? 는 아직 보존되지 않은 새 레코드인 경우만 true 를 반환한다.
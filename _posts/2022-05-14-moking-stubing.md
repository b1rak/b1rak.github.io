---
layout: post
title:  "더미, 스터빙, 모킹"
categories: 개발
---

# 더미
메소드 호출에는 전달되지만 실제로는 사용되지 않는 객체를 말한다.
Ruby 에서 ArgumentError 를 피하기 위한것이 가장 큰 목적이다.

# 스터빙
메세지 호출시 미리 준비된 값을 반환하는 것을 말한다.

스터빙이 가지는 장점.
- 실제로 테스트하고 싶은 기능에 집중할 수 있다.
- 불필요한 시간소모를 피한다.

주의해야할 점은, 테스트에 관련된 메소드 호출은 스터빙하지 않아야 한다는 것이다. 실행이 무의미한 테스트가 될 가능성이 있다.

Ruby Minitest를 이용한 예시.
```ruby
test 'call post api' do
  mock = Minitest::Mock.new
  def mock.post_api; true; end

  # APIService.new 가 호출되면 mock 을 반환한다
  APIService.stub :new, mock do
    message = messages(:one)
    assert message.send_post_api
  end
end
```

# 모킹
스터빙과 거의 같으나, 메소드가 호출되었는지 확인하는 것을 목적으로 한다.

```ruby
test 'call post api' do
  mock = Minitest::Mock.new
  mock.expect :post_api, true

  # APIService.new 가 호출되면 mock 을 반환한다
  APIService.stub :new, mock do
    message = messages(:one)
    assert message.send_post_api
  end

  # post_api 가 호출된 것을 확인한다
  assert_mock mock
end
```


# 이 모든것은 데스트 더블
테스트에서 실제 개체를 대체하기 위해 작성되어지는 개체를 포괄적으로 테스트 더블이라 부른다.
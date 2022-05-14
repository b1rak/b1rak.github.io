---
layout: post
title:  "inverse_of"
categories: 개발
---

# 앞서서
- inserse_of 옵션은 Rails4.1부터 기본적으로 적용된다.
  - 단, :has_many, :has_one, :belongs_to 같은 기본적인 관련설정에 한한다.
  - :conditions, :through, :polymorphic, :foreign_key 같은 복잡한 관계설정이 대해서는 기본적으로 적용되지 않는다.

# inverse_of 란
ActiveRecord에서 쌍방향으로 관련설정을 할때에, 각각의 참조되는 객체가 동일할 것을 보장하는 옵션이다.

inverse_of 를 설정하지 않은 소스코드를 예로 들어보자.

```ruby
class ChatRoom
  has_many :messages
end

class Message
  belongs_to :chat_room
end

# 레코드를 가져와서
chat_room = CharRoom.first
message = chat_room.messages.first

# 오브젝트의 동일성을 체크해보면
chat_room.equal?(message.chat_room)
#=> false
```

inverse_of 옵션을 사용하면, 아래와 같은 변화가 생긴다.

```ruby
chat_room.equal?(message.chat_room)
#=> true
```

# 참조
- http://wangjohn.github.io/activerecord/rails/associations/2013/08/14/automatic-inverse-of.html
# 서비스 분석?

1. 인터페이스는 구현체를 바꿔끼기 위해, 트레잇은 중복을 줄이기 위해

2. 내가 메일을 보낼껀데.. 메일을 어떤 방식으로 보낼지 정하지 않았으면 인터페이스를 생성한다음 인터페이스에서 메일 보낼때 필요한 기능들에 대해 정의하고

3. 이 기능에 맞게 메일 보내는 구현체를 작성한다음 <-- 이부분이 이제 mailgun이나 gmail이나 기타 등등 ..

1. 구현체? 구현하는 내용이 변경될 경우 인터페이스를 사용하여 호출하는 쪽은 변화가 없게 유지하는 것

2. 중복되는 내용이 발생할 경우 트레잇을 이용해 소스의 중복을 줄인다. ? 

1. 모델에는 릴레이션과 해당 필드 정의..

2. 레포지토리는 해당 릴레이션으로 얻을 수 있는 데이터 정리와.. 가공한 데이터들을 만든다.

3. 레포지토리와 인터페이스 RequestForm Exception 정의

4. DTO를 만들어서 관리하는 방법과.. 특정 데이터 형식으로 변환하기 위해 trait를 사용하는 방법 <-- 이렇게 사용할 경우 repo 데이터를 변환

5. 비즈니스 로직은 서비스로 빼서 사용한다..

# Relation With

- https://stackoverflow.com/questions/18963483/retrieving-relationships-of-relationships-using-eloquent-in-laravel

- 폴더별 깃 설정

# find, first, get

- https://stackoverflow.com/questions/33027047/what-is-the-difference-between-find-findorfail-first-firstorfail-get
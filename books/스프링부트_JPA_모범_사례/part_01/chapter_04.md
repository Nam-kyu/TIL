# @ManyToMany 연관관계를 효과적으로 구성하는 방법

### 항상 List가 아닌 Set 사용
  - 특히 삭제 처리와 관련해 Set을 사용하고 List를 피하는 것이 좋다.
  - 디테일한 내용은 chapter5 참고

### CascadeType.ALL 및 CascadeType.REMOVE 사용하지 않기
  - 대부분의 경우 제거에 대한 전이는 좋지 않은 생각
  - 예를들어 Author와 Book이 1:N의 관계를 가지고 있다고 가정했을 때 Author를 삭제할 경우 같이 삭제될 Book이 다른 Author에 의해 참조되는 경우가 존재할 수 있음
  - 따라서 CascadeType.REMOVE 사용을 피하고 명시적으로 CascadeType.PERSIT와 CascadeType.MERGE를 사용해야한다.
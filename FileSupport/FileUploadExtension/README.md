File 확장자와 관련있는 JavaScript 테스트 코드 입니다.
=====================================

# FileUploadExtend
## 1. ExtensionFilter.html
html에서 input이 file일경우 표시되는 all files(모든 파일) 옵션을 제거하는 방법을 찾아보는데 이것은 브라우저 자체에서 제공하기 때문에 삭제 할 방법이 전혀 없습니다. 우선 특정 확장자를 바탕으로 제어하기 위해선 accept속성을 통해 커스텀 option을 생성하고, 만약 all files를 선택할 경우 change event에서 걸러줄 수 밖에 없습니다. 
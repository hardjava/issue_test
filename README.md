# issue_test

1. 다음 문구를 confict_test.txt 에 추가
    ```
    스파르타 코딩 클럽 git 강의 최고!
    라인 1
    라인 2
    라인 3
    라인 4
    라인 5
    라인 6

    cherry-pick 브랜치 테스트 입력 입니다.

    아무말 대잔치!
    ```
2. main branch 에서 다음과 같은 명령어 실행
    - git add conflict_test.txt
    - git commit -m "main commit"

3. conflict branch 에서 다음을 추가
    ```
    ...
    라인 3 --> conflict-test 브랜치에서 라인 3 수정
    ...
    # 파일 끝에 추가
    conflict-test 브랜치에서 새로운 라인 B1 추가
    ```
    - git add conflict_test.txt
    - git commit -m "conflict commit"

4. main branch 에서 다음 내용을 업데이트
    ```
    ...
    라인 3 --> main 브랜치에서 라인 3 수정
    ...
    # 파일 끝에 추가
    main 브랜치에서 새로운 라인 M1 추가
    ```
    - git add conflict_test.txt
    - git commit -m "main: update line 3 and add M1"

5. conflict branch 에서 main을 rebase로 가져옴
    ```
    # conflict-test 브랜치로 이동
    git checkout conflict-test

    # main 브랜치의 변경사항을 rebasing
    git rebase main
    ```

6. 충돌 발생
    - Accept Both Changes 를 통해 변경 사항 전부반영 후 수정
    - git add conflict_test.txt
    - git rebase --continue
        - 새로운 커밋 메시지 입력
    - rebase 수정 후 빠져 나오기

7. git log 확인

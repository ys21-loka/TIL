# fatal: refusing to merge unrelated histories error 발생 시 대처

push 전 pull 사용, 프로젝트 병합

fatal: refusing to merge unrelated histories error 발생시 입력

```bash
git pull origin 브런치명 --allow-unrelated-histories
```

> 이미 존재하는 두 프로젝트의 기록을 저장하는 상황, 서로 관련없는 기록 병합을 허용
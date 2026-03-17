# 1. 원격 확인 및 최근 커밋 확인
  git remote -v
  git log --oneline -5

  # 2. mapping 파일을 git 추적에서 제거 시도 (이후 되돌림)
  git rm --cached mapping.xml mapping_pb000.xml

  # 3. 위 명령 되돌리기 (원격 삭제 방지)
  git reset HEAD mapping.xml mapping_pb000.xml

  # 4. mapping 파일 제외하고 전체 변경사항 staging
  git add -A
  git reset HEAD -- mapping.xml mapping_pb000.xml

  # 5. 커밋
  git commit -m "Releases 폴더 정리: 불필요 파일 삭제, .gitignore 추가"

  # 6. push (원격에 새 커밋이 있어서 rejected)
  git push

  # 7. 원격 변경사항 pull (rebase)
  git pull --rebase origin main

  # 8. 다시 push (성공)
  git push origin main

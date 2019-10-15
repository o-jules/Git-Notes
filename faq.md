# 常见问题

- 如何撤销 Git 本地的某些操作（如 reset, rebase, commit 等）

- 如何整合两个或者多个 Git 项目为一个（需要保持各个项目的历史纪录）

  1. Create a new empty repository New
  2. Make an initial commit because we need one before we do a merge
  3. Add a remote to old repository A
  4. Merge A/master to New/master
  5. Make a subdirectory folderA
  6. Move all files into subdirectory folderA
  7. Commit all of the file moves
  8. Repeat 3-6 for another repository

  ```bash
  # step 1 - 2
  mkdir result
  cd result
  git init
  git commit --allow-empty -m "init: empty project"

  # step 3 - 8
  git remote add -f A https://github.com/A.git
  git fetch --all
  git merge --allow-unrelated-histories A/master
  mkdir folderA
  git mv -k * folderA
  git commit -m "move: A files into subdir folderA"
  ```

  References:
  - [merging-two-git-repositories-into-one-repository-without-losing-file-history](https://www.waltercedric.com/index.php/development/2295-merging-two-git-repositories-into-one-repository-without-losing-file-history)

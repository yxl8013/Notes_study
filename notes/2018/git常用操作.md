1.远程没东西
git init //建本地仓库
git remote add origin 仓库地址 //连接远程仓库
git add .  //推到暂存区
git commit -m “备注” //推到版本库
git push origin master //推送到远程仓库
.................................................
2.远程有东西
git init //建本地仓库
git remote add origin 仓库地址 //连接远程仓库
git pull 	//拉取远程仓库的东西
git add .  //推到暂存区
git commit -m “备注” //推到版本库
git push origin master //推送到远程仓库
.................................................
3.创建分支
git branch 分支名 //创建分支
git branch lsh
git checkout 分支名 //切换分支
git checkout lsh
.................................................
4.关联分支（前提是已经切换到自己的分支）
git remote add hongshao https://github.com/OneEightZeroEight/souyidai.git //关联到仓库
git push -v origin hongshao //将此分支名与仓库关联
..................................................
5.分支推上主分支
git add .  //推到暂存区
git commit -m “备注” //推到版本库
git checkout master //切换回主分支
git merge hongshao  //与分支代码合并
git push origin master //推送到远程仓库
.................................................
# 创建Git-CI Runner

## 下载runner：
* X86: https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-windows-386.exe
* X64: https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-windows-amd64.exe
* CDN: ftp://gui.avepoint.net/software/

## 获取相关信息
* 打开该project/group的CI/CD Settings页面，展开Runners。
* 在Set up a specific(group) Runner manually下面，有url和对应的token内容。

## 创建目录
* 创建一个运行目录，如：C:/GitLab-Runner。
* 将下载的exe文件copy至此目录内，并重命名，如：gitlab-runner.exe。

## 注册Runner
1. 在刚创建的目录运行cmd或PowerShell。
2. 注册
```
./gitlab-runner.exe register
```
3. 执行注册后，会要求输入相关信息，先输入之前获取的url。
```
https://git.avepoint.net/
```
4. 输入之前获取的token。
5. 输入description（对这个runner的描述）。
6. 输入tags，根据需求，可不输入，直接回车。
7. 输入[Runner executor](https://docs.gitlab.com/runner/executors/README.html)类型，推荐简单的shell，需要复杂功能的可以选择Docker。
8. 注册完成。

## 添加service
* 添加service
```
./gitlab-runner.exe install
```
* 将service修改为admin账号启动。
* 启动service。

## Check
回到project/group的Runner的settings页面，查看是否有新创建的Runner。

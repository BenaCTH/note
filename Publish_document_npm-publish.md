# npm Feed
https://proget.avepoint.net/npm/avepoint-npm/

# GIT-CI Runner设置
1. 安装npmrc
```
npm i npmrc -g
```
2. 配置avepoint-npm及发布所需的user配置
```
npmrc -c avepoint-npm
npm config set @gui:registry https://proget.avepoint.net/npm/avepoint-npm
npm config set always-auth true --scope:@gui
npm adduser --registry=https://proget.avepoint.net/npm/avepoint-npm/ --scope:@gui
npm login --scope=@gui --registry=https://proget.avepoint.net/npm/avepoint-npm/
```
3. 发布
```
npmrc avepoint-npm
npm publish --registry https://proget.avepoint.net/npm/avepoint-npm/
```

# git添加Pipeline

* 添加.gitlab-ci.yml，定义stages。

  1. build：执行build打包相关script，控件示例为调用./build.cmd。
  2. unit test：尚未实现。
  3. release：执行npm发布相关script，控件示例为调用./release.cmd。
```
//release stage执行条件为在git上进行release。
//目前暂用only进行实现（only:variables为实验性功能，在git12.3之后改为rules进行实现）。
//条件为执行release操作，且对应的tag以v开头（暂不确定俩条件是AND还是OR，理论上都可以）。
only:
  variables:
    - $CI_RUNNER_TAGS == "release"
    - $CI_COMMIT_REF_NAME =~ /^v/
```

# 在git与npm同步发布
* 在git上创建tag，版本号格式va.b.c，如v1.6.2。
* 创建时填写release notes，git会自动进行release，并创建Pipeline，执行上面定义的stage。
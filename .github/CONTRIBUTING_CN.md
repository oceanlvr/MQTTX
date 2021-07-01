# 贡献指南

您好, 非常感谢您对 [MQTT X](https://mqttx.app/zh) 的支持。

如果您在使用过程中发现了问题 🐛 或有更好的意见和建议 💡，都可以参考以下方法修改项目代码并参与到项目中。

1. Fork 这个仓库

2. 如下运行项目

    ``` shell
    # 安装依赖
    cd MQTTX
    yarn install

    # 编译和热加载以进行开发
    yarn run electron:serve

    # 编译并压缩代码打包成安装包
    yarn run electron:build
    ```

3. 添加 Git 的 upstream remote

    ```shell
    git remote add upstream git@github.com:emqx/MQTTX.git`
    ```

4. 可以参考以下项目结构来进行源码修改:

    ```shell
    src
      ├── App.vue       # 主视图组件
      ├── api           # 请求数据的 API 集合
      ├── assets        # 资源
      │   ├── font
      │   ├── images
      │   └── scss
      ├── background.ts # 主进程文件
      ├── components    # 公用组件的集合
      ├── database      # 数据库的配置文件
      ├── lang          # 国际化配置文件
      ├── main          # 操作主进程的代码
      ├── main.ts       # 主渲染进程的文件
      ├── plugins       # 扩展 Vue 的插件
      ├── router        # 视图路由的配置集合
      ├── store         # Vuex 状态管理的配置集合
      ├── types         # 类型定义的集合
      ├── utils         # 通用工具的集合
      └── views         # 视图代码的集合
          ├── Home.vue
          ├── about
          ├── connections
          ├── log
          ├── script
          ├── settings
          └── window
    ```

5. 在新分支上添加一个 commit，并将其推送。请参阅以下说明来编写提交时 commit 信息的规范：

    - 基础格式

    `<type>(<scope>): <subject>`

    `type` 表示提交的类型, `scope` 表示提交修改的范围，`subject` 表示主要描述内容。

    例子:

    ```shell
    git commit -m "fix(index.vue): fix the mqtt connect bug"
    ```

    - 类型
      - feat: 新功能 (feature)
      - fix: 修补 bug
      - refactor: 重构 既不是修补 bug 也不是新功能
      - style: 修改样式 代码格式
      - docs: 文档
      - perf: 性能
      - revert: 恢复原状
      - test: 增加测试
      - ci: 持续集成
      - build || chore: 构建过程或辅助工具的变动

6. 最后，向上游仓库中的 `dev/*` 分支发起一个 pull request 请求，我们将对其进行认真的审查，该仓库中至少会包含一个 `dev/${version}` 的分支。

7. 发版流程，在当前 `dev/*` 分支拉下最新的主分支 `maste`，对于一个版本号 `major.minor.patch`，使用 `npm version [patch | minor | major] 'commit message'` 分别对其各个版本位进行升级，其中 `major` 为主版本号，即含有大的并且可能含有断层的修改，`minor` 为次版本号，反映一些较大的修改，`patch` 为补丁版本，主要是没有巨大断层的小改动。`npm version` 命令执行之后产生一个记录新版本号的 commit，之后使用 rebase merge 合并到主分支 `master`，最后使用 `git tag` 命令对其分支做记录。即完成了一个发布流程。

谢谢您的耐心阅读！并感谢您对 MQTT X 的贡献！:)

commit 信息前缀
```
type: commit 的类型
upd:更新某功能（不是 feat, 不是 fix）
feat: 新特性,新功能（feature）
fix: 修改问题,修补bug
refactor: 代码重构（即不是新增功能，也不是修改bug的代码变动）
docs: 文档修改
style: 代码格式修改, 注意不是 css 修改
test: 测试用例修改
chore: 其他修改, 比如构建流程, 依赖管理.
scope: commit 影响的范围, 比如: route, component, utils, build...
subject: commit 的概述, 建议符合 50/72 formatting
body: commit 具体修改内容, 可以分为多行, 建议符合 50/72 formatting
footer: 一些备注, 通常是 BREAKING CHANGE 或修复的 bug 的链接.
```

使用

```
git commit -m 'feat: 增加 xxx 功能'
```

**commit中添加emoji**
```
git commit -m ':tado: init'

上面的 :tado: 就是某个小表情
```

1. 可以直接在emoji的网站搜索后使用，如 [emoji](https://emoji.muan.co/)

2. 可以安装 [emoji插件](https://hooj0.github.io/git-emoji-guide/)
    ```
    npm i -g gitmoji-cli
    ```

    查看 emoji 列表

    ```
    gitmoji -l
    ```

    会得到以下列表

    ```
    🎨 - :art: - Improving structure / format of the code.
    ⚡️ - :zap: - Improving performance.
    🔥 - :fire: - Removing code or files.
    🐛 - :bug: - Fixing a bug.
    🚑 - :ambulance: - Critical hotfix.
    ✨ - :sparkles: - Introducing new features.
    📝 - :pencil: - Writing docs.
    🚀 - :rocket: - Deploying stuff.
    💄 - :lipstick: - Updating the UI and style files.
    🎉 - :tada: - Initial commit.
    ✅ - :white_check_mark: - Updating tests.
    🔒 - :lock: - Fixing security issues.
    🍎 - :apple: - Fixing something on macOS.
    🐧 - :penguin: - Fixing something on Linux.
    🏁 - :checkered_flag: - Fixing something on Windows.
    🤖 - :robot: - Fixing something on Android.
    🍏 - :green_apple: - Fixing something on iOS.
    🔖 - :bookmark: - Releasing / Version tags.
    🚨 - :rotating_light: - Removing linter warnings.
    🚧 - :construction: - Work in progress.
    💚 - :green_heart: - Fixing CI Build.
    ⬇️ - :arrow_down: - Downgrading dependencies.
    ⬆️ - :arrow_up: - Upgrading dependencies.
    📌 - :pushpin: - Pinning dependencies to specific versions.
    👷 - :construction_worker: - Adding CI build system.
    📈 - :chart_with_upwards_trend: - Adding analytics or tracking code.
    ♻️ - :recycle: - Refactoring code.
    🐳 - :whale: - Work about Docker.
    ➕ - :heavy_plus_sign: - Adding a dependency.
    ➖ - :heavy_minus_sign: - Removing a dependency.
    🔧 - :wrench: - Changing configuration files.
    🌐 - :globe_with_meridians: - Internationalization and localization.
    ✏️ - :pencil2: - Fixing typos.
    💩 - :poop: - Writing bad code that needs to be improved.
    ⏪ - :rewind: - Reverting changes.
    🔀 - :twisted_rightwards_arrows: - Merging branches.
    📦 - :package: - Updating compiled files or packages.
    👽 - :alien: - Updating code due to external API changes.
    🚚 - :truck: - Moving or renaming files.
    📄 - :page_facing_up: - Adding or updating license.
    💥 - :boom: - Introducing breaking changes.
    🍱 - :bento: - Adding or updating assets.
    👌 - :ok_hand: - Updating code due to code review changes.
    ♿️ - :wheelchair: - Improving accessibility.
    💡 - :bulb: - Documenting source code.
    🍻 - :beers: - Writing code drunkenly.
    💬 - :speech_balloon: - Updating text and literals.
    🗃 - :card_file_box: - Performing database related changes.
    🔊 - :loud_sound: - Adding logs.
    🔇 - :mute: - Removing logs.
    👥 - :busts_in_silhouette: - Adding contributor(s).
    🚸 - :children_crossing: - Improving user experience / usability.
    🏗 - :building_construction: - Making architectural changes.
    📱 - :iphone: - Working on responsive design.
    🤡 - :clown_face: - Mocking things.
    🥚 - :egg: - Adding an easter egg.
    🙈 - :see_no_evil: - Adding or updating a .gitignore file
    📸 - :camera_flash: - Adding or updating snapshots
    ⚗ - :alembic: - Experimenting new things
    🔍 - :mag: - Improving SEO
    ☸️ - :wheel_of_dharma: - Work about Kubernetes
    🏷️ - :label: - Adding or updating types (Flow, TypeScript)
    🌱 - :seedling: - Adding or updating seed files
    🚩 - :triangular_flag_on_post: - Adding, updating, or removing feature flags
    🥅 - :goal_net: - Catching errors
    💫 - :dizzy: - Adding or updating animations and transitions
    🗑 - :wastebasket: - Deprecating code that needs to be cleaned up.
    ```



# contact-manager
原文https://scotch.io/tutorials/build-an-interactive-command-line-application-with-nodejs   
项目使用yarn管理
```bash
npm install -g yarn
```

### 1.创建项目
```bash
$ yarn init
yarn init v1.16.0
question name (contact-manager): 
question version (1.0.0): 
question description: A command-line contact management system
question entry point (index.js): 
question repository url (https://github.com/lizhigang858/contact-manager.git): 
question author (li <lizhigang858@126.com>): 
question license (MIT): 
question private: 
success Saved package.json
✨  Done in 55.09s.
$ yarn add mongoose inquirer commander
yarn add v1.16.0
info No lockfile found.
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 50 new dependencies.
info Direct dependencies
├─ commander@2.20.0
├─ inquirer@6.3.1
└─ mongoose@5.5.11
info All dependencies
├─ ansi-escapes@3.2.0
├─ ansi-regex@4.1.0
├─ ansi-styles@3.2.1
├─ async@2.6.2
├─ bluebird@3.5.1
├─ bson@1.1.1
├─ chalk@2.4.2
├─ chardet@0.7.0
├─ cli-cursor@2.1.0
├─ cli-width@2.2.0
├─ color-convert@1.9.3
├─ color-name@1.1.3
├─ commander@2.20.0
├─ debug@3.1.0
├─ external-editor@3.0.3
├─ figures@2.0.0
├─ has-flag@3.0.0
├─ iconv-lite@0.4.24
├─ inquirer@6.3.1
├─ is-fullwidth-code-point@2.0.0
├─ is-promise@2.1.0
├─ kareem@2.3.0
├─ memory-pager@1.5.0
├─ mimic-fn@1.2.0
├─ mongodb@3.2.5
├─ mongoose-legacy-pluralize@1.0.2
├─ mongoose@5.5.11
├─ mpath@0.6.0
├─ mquery@3.2.0
├─ ms@2.1.1
├─ mute-stream@0.0.7
├─ onetime@2.0.1
├─ os-tmpdir@1.0.2
├─ require_optional@1.0.1
├─ resolve-from@2.0.0
├─ restore-cursor@2.0.0
├─ run-async@2.3.0
├─ rxjs@6.5.2
├─ safer-buffer@2.1.2
├─ saslprep@1.0.3
├─ semver@5.7.0
├─ sift@7.0.1
├─ signal-exit@3.0.2
├─ sparse-bitfield@3.0.3
├─ string-width@2.1.1
├─ strip-ansi@5.2.0
├─ supports-color@5.5.0
├─ through@2.3.8
├─ tmp@0.0.33
└─ tslib@1.9.3
✨  Done in 23.33s.

```

### 2.逻辑
这个项目需要用到mongo，所以我在kubernete上配置了一个mongo

### 3.处理用户输入
使用commander来编写基本的命令行框架，完成后可以执行如下命令测试
```bash
$ node contact.js --help # Shows you program description, usage, commands, actions, and aliases
$ node contact.js --version # Shows the version number specified
$ node contact.js addContact John Doe 013-452-3134 john.doe@contacto.com
$ node contact.js r john # Notice we used r which is an alias for getContact.
```

### 4.与用户交互
除了可以在程序开始时让用户输入参数，我们还可以在程序运行过程中与用户交互，这就要借助<code>inquirer.js</code>了

### 5.将程序转换为shell命令
```bash
$ yarn link # creates a symbolic link between project directory and executable command.
$ contacto --help # Returns usage instructions.
$ contacto r john # Returns user detail.
```

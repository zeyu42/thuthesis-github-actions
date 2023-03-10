# thuthesis-github-actions

清华大学学位论文 LaTeX 模版 [thuthesis](https://github.com/tuna/thuthesis) 建议在最后提交时使用 Windows 编译以获得正确的字体。本项目提供使用 Github Actions 自动编译 thuthesis 的脚本。用户可以将本 repo 中的 `.github` 文件夹拷贝至自己的论文项目中并上传至 Github。此时，在 repo 的 Actions 菜单中可以看到 Github Actions 会自动编译项目（首次编译 thuthesis 提供的样例论文大致需要 10 分钟，此后 TeX 环境会自动缓存，这一时间将缩短至 2 分钟），并生成论文和书脊供下载。此后，每当用户将新的 commit push 到 repo 中时，Github 都会自动重新编译论文。

之所以要这样做而不是本地编译，是为了方便非 Windows 环境的用户在编译论文时使用正确的字体。实际上，学校提供了论文的 Word 模版，并在其中规定了字体。thuthesis 只有在 Windows 环境下编译（或在安装了 Windows 字体的其他系统下编译）才严格符合学校的规定。本脚本使用了 Github Actions 提供的 Windows 环境以生成字体正确的论文。

本脚本基于另一个 [Action](https://github.com/teatimeguest/setup-texlive-action) 以实现 TeX Live 环境，并在安装 Windows 中的繁简中文字体时借鉴了这个 [Github Gist](https://gist.github.com/ivan/2c2b493729faacf08c3e7a090e57a236)，特此致谢。本脚本的贡献主要在于，在一个基本的 Tex Live 环境的基础上，安装 thuthesis 所需要的 package。

本脚本在 thuthesis 7.3.1 上通过测试。

**注意：在 `.github/workflows/build.yml` 中，默认的论文主文件名为 `thuthesis-example.tex`（第 74 行），与 thuthesis 提供的默认文件名相同。然而，thuthesis 文档建议用户在写自己的论文时不要使用这一文件名，而是复制这一文件，并重新命名。这里假定用户没有采纳这一建议。这样，用户应当可以直接用这个脚本生成 thuthesis 的样例论文。如果用户采纳了 thuthesis 的建议，也请自行修改 `.github/workflows/build.yml` 中第 74 行和第 81 行的文件名，以编译正确的文件。（如果你不知道这里在说什么，大概率可以直接忽略。）**

**注意：使用这一脚本要求用户将自己的论文上传到 Github。这一行为是否合适请自行判断。此外，用户也应该注意储存自己论文 repo 的类型（public/private），以防以不合理的方式公开自己的研究成果。**

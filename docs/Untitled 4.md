每次执行指令都会新建 `overleaf_project_时间戳` 文件夹。

1. 在里面生成 [main.tex](vscode-file://vscode-app/d:/Microsoft VS Code/61b3d0ab13/resources/app/out/vs/code/electron-browser/workbench/workbench.html)。
2. [main.tex](vscode-file://vscode-app/d:/Microsoft VS Code/61b3d0ab13/resources/app/out/vs/code/electron-browser/workbench/workbench.html) 内容始终来自你定义的初始模板，不再读取当前打开文件。

已调整内容：

- 新任务：`.vscode/tasks.json:5`
  `Generate Overleaf TeX From Initial Template`

- 新脚本：[generate-overleaf-from-template.ps1](vscode-file://vscode-app/d:/Microsoft VS Code/61b3d0ab13/resources/app/out/vs/code/electron-browser/workbench/workbench.html)

- 初始模板：[overleaf-initial-template.tex](vscode-file://vscode-app/d:/Microsoft VS Code/61b3d0ab13/resources/app/out/vs/code/electron-browser/workbench/workbench.html)

- 旧脚本已删除：`scripts/generate-overleaf-from-current.ps1`

- 你以后直接这样调用：

  1. `Ctrl+Shift+P`
  2. `Tasks: Run Task`
  3. 选 `Generate Overleaf TeX From Initial Template`

  如果你想更新“初始格式”，只需要改这个文件：
  [overleaf-initial-template.tex](vscode-file://vscode-app/d:/Microsoft VS Code/61b3d0ab13/resources/app/out/vs/code/electron-browser/workbench/workbench.html)
  之后每次执行任务都会按它生成新文档。

**使用方法：**

1. **通过 VS Code 任务运行（推荐）：**
   - 按 `Ctrl+Shift+P`
   - 输入"Tasks: Run Task"
   - 选择 **"Generate Math Worksheet and Download"**
   - PDF 将自动生成并复制到 Downloads 文件夹
2. **通过批处理文件运行：**
   - 双击 [run-worksheet.bat](vscode-file://vscode-app/d:/Microsoft VS Code/61b3d0ab13/resources/app/out/vs/code/electron-browser/workbench/workbench.html)
   - 或在终端运行：[run-worksheet.bat](vscode-file://vscode-app/d:/Microsoft VS Code/61b3d0ab13/resources/app/out/vs/code/electron-browser/workbench/workbench.html)



**脚本参数（可选）：**

- [--count 30](vscode-file://vscode-app/d:/Microsoft VS Code/61b3d0ab13/resources/app/out/vs/code/electron-browser/workbench/workbench.html)：指定题目数量（默认 50）
- [--seed 1234](vscode-file://vscode-app/d:/Microsoft VS Code/61b3d0ab13/resources/app/out/vs/code/electron-browser/workbench/workbench.html)：指定随机种子（可重现相同题目）
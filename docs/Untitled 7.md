curl (bash / WSL / Git Bash):

curl -X POST 'http://127.0.0.1:5000/api/questions' \
  -H 'Content-Type: application/json' \
  -d '{
    "content": "请写出一元二次方程 x^2-3x+2=0 的两根。",
    "answer": "x=1, x=2",
    "tags": ["代数","一元二次"],
    "difficulty": 90,
    "chapter_id": 1,
    "section_id": 2
  }'





PowerShell (Invoke-RestMethod)：

$body = @{
  content    = ""
  answer     = "x=1, x=2"
  tags       = @("代数","一元二次")
  difficulty = 90
  chapter_id = 1
  section_id = 2
}
$json = $body | ConvertTo-Json -Depth 10
$bytes = [System.Text.Encoding]::UTF8.GetBytes($json)
Invoke-RestMethod -Uri 'http://127.0.0.1:5000/api/questions' -Method Post -ContentType 'application/json; charset=utf-8' -Body $bytes

$body = @{
  content    = "\begin{tasks}[label=(\arabic*)](2) % (2) 表示分为两列
        \task $f(x) = \displaystyle \frac{x^3 - 1}{\sin x}$ \hfill\mbox{}
        \task $f(x) = \displaystyle \frac{\sin x}{\sin x + \cos x}$ \hfill\mbox{}
        \task  $f(x) = \displaystyle \frac{x}{\sqrt{2x+1}}$ \hfill\mbox{}
        \task  $f(x) = (3x+1)^2 \ln(3x)$ \hfill\mbox{}
        \task  $f(x) = 3^x e^{-3x}$ \hfill\mbox{}
        \task  $f(x) = 2x \tan x$ \hfill\mbox{}
        \task  $f(x) = (x-2)^3 (3x+1)^2$ \hfill\mbox{}
        \task  $f(x) = \displaystyle \frac{x^2}{(2x+1)^3}$ \hfill\mbox{}
        \task  $f(x) = e^{-2x+1} \cos(-x^2+x)$ \hfill\mbox{}
        \task  $f(x) = \displaystyle \frac{\sin 2x}{\sqrt{x}}$ \hfill\mbox{}
        \task  $f(x) = \sin^4(3x) \cos^3(4x)$ \hfill\mbox{}
        \task  $f(x) = 2(e^{\frac{x}{2}} + x e^{\frac{x}{2}})$ \hfill\mbox{}
        \task  $f(x) = \displaystyle \frac{x \ln x}{x+1} - \ln(x+1)$ \hfill\mbox{}
        \task $f(x) = x^2 \sin 3x - \displaystyle \frac{2}{\sqrt{x}}$ \hfill\mbox{}
        \task $f(x) = \displaystyle \frac{e^x - e^{-x}}{e^x + e^{-x}}$ \hfill\mbox{}
        \task $f(x)=\displaystyle \ln (x+\sqrt{x^2+1})$ \hfill\mbox{}
        \task $f(x)=\displaystyle \frac{x\sin x+\cos x}{x\cos x-\sin x}$ \hfill\mbox{}

        \task $\displaystyle f(x) = (\cos x - x)(\pi + 2x) - \frac{8}{3}(\sin x + 1)$ \hfill\mbox{}
    \end{tasks}"
  answer     = "x=1, x=2"
  tags       = @("代数","一元二次")
  difficulty = 90
  chapter_id = 1
  section_id = 2
}
$json = $body | ConvertTo-Json -Depth 10
$bytes = [System.Text.Encoding]::UTF8.GetBytes($json)
Invoke-RestMethod -Uri 'http://127.0.0.1:5000/api/questions' -Method Post -ContentType 'application/json; charset=utf-8' -Body $bytes


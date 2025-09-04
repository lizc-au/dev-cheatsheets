# YAML via Base64 (PowerShell) — CRLF + 2/4/6 indent

Pattern: write YAML as base64 to avoid newline/indent corruption.

Encode → get base64:
```powershell
$lines=@('name: Node CI','on: [push, pull_request]','jobs:',' test:',' runs-on: ubuntu-latest',' steps:',' - uses: actions/checkout@v4');
$y=($lines -join \"rn\");
$b=[Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes($y));
$b
```

Decode → write file:
```powershell
$b='PASTE_BASE64_HERE';
[IO.File]::WriteAllBytes('.github/workflows/ci.yml',[Convert]::FromBase64String($b))
```

Tip: follow 2/4/6 indent rule (and 8/10 for nested keys).

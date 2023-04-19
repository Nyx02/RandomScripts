# Base64 Decoding Trinity - Python, Bash & Powershell

```
*Mainly decoding a multi-encoded base64 string*
```

## Python
```python
import base64


with open('base64.txt') as f:
    output = f.read()

#decode x times
for line in range(50):
    output = base64.b64decode(output)

print(output.decode('ascii'))
```

## Bash
```bash
!/usr/bin/env bash

decode=$(<base64.txt)
for line in {1..50}; do
     decode=$(<<<"$decode" base64 --decode)
done
echo "$decode"
```

## Powershell
```powershell
$output = Get-Content base64.txt

foreach ($line in 1..50) {
    $output = %{[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($output))}
}

$output 
```

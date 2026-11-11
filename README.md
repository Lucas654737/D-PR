# 🎬 Decupagem Premiere — Releases

Repositório público de **distribuição** do [Decupagem Premiere](https://github.com/Lucas654737/caos) —
plugin que remove silêncios de vídeos com IA, com app desktop (Electron) e painel para o **Adobe Premiere Pro**.

> O código-fonte fica no repositório privado. Aqui ficam **apenas os binários** que o app baixa.

---

## 📥 Instalação (usuário final)

1. Baixe a versão mais recente:
   **[`DecupagemPremiere-win-Setup.exe`](https://github.com/Lucas654737/D-PR/releases/latest/download/DecupagemPremiere-win-Setup.exe)** (~129 MB)
2. **Duplo clique** — instalação por usuário (`%LocalAppData%`), **não precisa de administrador**
3. O app abre num **assistente de primeira execução**:
   - verifica o que já existe no seu PC (FFmpeg, Premiere, espaço em disco, internet)
   - **pede seu consentimento** antes de baixar qualquer coisa
   - baixa o servidor de análise (~83 MB) com verificação de integridade
   - (se você tiver Premiere) instala o painel CEP no Premiere Pro
4. Na **primeira análise**, o modelo Whisper (~484 MB) é baixado automaticamente com barra de progresso

**Atualizações:** o próprio app avisa quando sair versão nova e atualiza sozinho (Velopack).

---

## 📦 O que tem em cada release

| Asset | Para que serve |
|---|---|
| `DecupagemPremiere-win-Setup.exe` | Instalador único (o que o usuário final baixa) |
| `DecupagemPremiere-<versão>-full.nupkg` | Pacote completo para auto-update |
| `DecupagemPremiere-win-Portable.zip` | Versão portátil (sem instalar) |
| `RELEASES` | Índice de versões para o Velopack |
| `assets.win.json` / `releases.win.json` | Metadados do Velopack |
| `manifest.json` | Catálogo de downloads do backend (URL + SHA256) |
| `decupagem-server-<versão>.zip` | Servidor de análise (release `server-*`) |

---

## 🔄 Atualizar os arquivos (mantenedor)

```powershell
# 1. build do instalador (no repo do código, pasta standalone/)
powershell scripts\build-installer.ps1 -Versao 1.0.1

# 2. publicar
gh release upload 1.0.1 `
  "dist-vpk\DecupagemPremiere-win-Setup.exe" "dist-vpk\RELEASES" `
  "dist-vpk\DecupagemPremiere-1.0.1-full.nupkg" "dist-vpk\assets.win.json" `
  "dist-vpk\releases.win.json" -R Lucas654737/D-PR --clobber
```

O `manifest.json` (backend) é atualizado quando a versão do **servidor** muda —
veja o passo a passo em `server/release/README-PUBLISH.md` no repositório do código.

---

## 🧪 Verificação de integridade

Todos os downloads são conferidos por **SHA256** antes de serem instalados.
O hash oficial de cada versão está no `manifest.json` do próprio release.

---

*Decupagem Premiere — app desktop + painel Premiere Pro, 100% local (exceto a chave de API de IA, que você configura uma vez na interface).*

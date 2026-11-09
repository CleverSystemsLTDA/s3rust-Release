# s3rust-Release

Firmware publicado da placa **s3rust1** (servidor de senhas, ESP32) da Clever Systems.

Os arquivos ficam nas [Releases](../../releases). O **Gravador de placas Clever** (`clever-flasher.exe`) busca a release mais recente daqui e baixa o firmware sozinho.

## Formato de cada release

O gravador depende deste formato. A Action que publica as releases precisa seguir:

| Item | Formato | Exemplo |
|---|---|---|
| Tag | `v<versão>-<commit>` | `v0.1.0-b8977bb` |
| Atualização em campo | `s3rust1-<versão>-<commit>-field-update.bin`: preserva Wi-Fi, contadores e fila (termina antes de `0x310000`) | `s3rust1-0.1.0-b8977bb-dirty-field-update.bin` |
| Fábrica (opcional) | `s3rust1-<versão>-<commit>-factory.bin`: imagem de 4 MB, **apaga** os dados da placa | |
| Checksum | `<arquivo>.sha256` para cada `.bin`: SHA-256 em hex | |

- O gravador usa só `releases/latest`. Rascunhos e pré-releases são ignorados.
- Por padrão o gravador baixa só o `*-field-update.bin`. A imagem de fábrica só é usada se o operador escolher.
- O gravador confere o SHA-256 antes de usar o arquivo e recusa se não bater.
